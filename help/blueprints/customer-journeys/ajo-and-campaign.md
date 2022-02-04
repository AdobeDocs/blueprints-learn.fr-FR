---
title: Journey Optimizer avec plan directeur Adobe Campaign
description: Illustre l’utilisation de Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign
solution: Experience Platform, Journey Optimizer, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 26%

---

# Journey Optimizer avec Adobe Campaign

Illustre l’utilisation de Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.

<br>

## Architecture

<img src="assets/ajo-campaign-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>L’utilisation de Journey Optimizer et de Campaign pour envoyer des messages indépendamment les uns des autres est possible, mais présente des considérations techniques à prendre en compte. Si vous souhaitez suivre cette route, contactez votre architecte d’entreprise de prévente afin de vous assurer que vous comprenez ce qui sera nécessaire pour prendre en charge l’implémentation.

<br>

## Conditions préalables

### Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Experience Event, ajoutez le groupe de champs &quot;Orchestration eventID&quot; lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Individual Profile, ajoutez le groupe de champs &quot;Détails du test de profil&quot; pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.
* Journey Optimizer et Campaign sont configurés dans la même organisation IMS.

### Campaign v7/v8 ou Campaign Standard

* L&#39;instance d&#39;exécution du service de messagerie en temps réel (c&#39;est-à-dire Message Center) doit être hébergée par des Cloud Services gérés par Adobe.
* La création de tous les messages s&#39;effectue dans l&#39;instance Campaign elle-même.

<br>

## Garde-fous

[Lien de produit de la protection Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)

### Autres garde-fous Journey Optimizer

* La limitation est disponible aujourd’hui via l’API pour s’assurer que le système de destination n’est pas saturé au point d’échec. Cela signifie que les messages qui dépassent la limite seront complètement ignorés et ne seront jamais envoyés. Le ralentissement n’est pas pris en charge.
   * Nombre maximum de connexions : nombre maximum de connexions http/s qu’une destination peut gérer
   * Nombre d’appels max. : nombre maximal d’appels à effectuer dans le paramètre periodInMs
   * periodInMs - durée en millisecondes
* Les parcours initiés d’appartenance à un segment peuvent fonctionner suivant deux modes :
   * Segments par lot (actualisés toutes les 24 heures)
   * Segments de diffusion en continu (&lt;qualification de 5 minutes)
* Segments par lot : veillez à connaître le volume quotidien des utilisateurs qualifiés et à garantir que le système de destination peut gérer les pics de débit par parcours et sur tous les parcours.
* Segments en diffusion en continu : veillez à ce que le pic initial des qualifications de profil puisse être traité en même temps que le volume de qualification des diffusion en continu quotidien par parcours et sur tous les parcours
* offer decisioning non pris en charge
* Les événements professionnels ne sont pas pris en charge
* Intégrations sortantes vers des systèmes tiers
   * Pas de prise en charge d’une seule adresse IP statique, car notre infrastructure comporte plusieurs clients (doit mettre en liste autorisée toutes les adresses IP du centre de données).
   * Seules les méthodes de POST et de PUT sont prises en charge pour les actions personnalisées.
   * Prise en charge de l’authentification : token | password | OAuth2
* Impossible de regrouper et de déplacer des composants individuels de Adobe Experience Platform ou de Journey Optimizer entre différents environnements de test. Doit être réimplémenté dans les nouveaux environnements

<br>

### Campaign (v7/v8)

* L&#39;instance d&#39;exécution de Message Center doit être hébergée par des Cloud Services gérés par Adobe.
* Doit être sur v7 build >21.1 ou v8
* Débit des messages
   * AC (v7) 50 000 par heure
   * AC (v8) jusqu’à 1 million par heure selon le package
* AC (v7) ne prend en charge que le parcours initié par un événement
   * Aucun Parcours initié pour l’appartenance à un segment ou à un segment
   * Les parcours basés sur les audiences et les événements professionnels en lecture ne sont pas pris en charge en raison du volume qu’il peut envoyer aux instances d’exécution.
* Ni AC (v7) ni AC (v8) ne prennent en charge l’Offer decisioning dans les messages
* Pas de limitation des appels API sortants vers Campaign
* Les journaux des messages transactionnels ne sont pas synchronisés nativement avec AEP. Nécessite un effort de conseil. Recommandation d’exporter des logs au plus toutes les 4 heures

<br>

### Campaign Standard

* Prend en charge 14 tps (50 k par heure) dans le débit
* Ne prend en charge que les parcours initiés par un événement
   * Aucun Parcours initié pour l’appartenance à un segment ou à un segment
   * Les parcours basés sur les audiences et les événements professionnels en lecture ne sont pas pris en charge en raison du volume qu’il peut envoyer aux instances d’exécution.
* Les activités d’ouverture et de clic à partir des messages transactionnels envoyés à Campaign Standard sont exposées en mode natif sous la forme d’&quot;événements de réaction&quot; dans la zone de travail du parcours Journey Optimizer.
* Les logs des messages transactionnels ne sont pas resynchronisés en mode natif vers l’Experience Platform. Nécessite un effort de conseil. Recommandation d’exporter des logs au plus toutes les 4 heures

<br>

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas basés sur des classes d’événements d’expérience pour les tables broadLog, trackingLog et adresses non livrables d’Adobe Campaign (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour une utilisation par Parcours.

#### Sources / destinations

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide d’API de diffusion en continu et de connecteurs sources.

### Journey Optimizer

1. Configurez votre source de données Experience Platform et déterminez les champs à mettre en cache dans le cadre des données profileStreaming utilisées pour lancer un parcours client. Vous devez d’abord configurer Journey Optimizer pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion
1. Configurez des sources de données externes
1. Configuration d’actions personnalisées pour l’instance Campaign

### Campaign v7/v8 ou Campaign Standard

* Les modèles de messagerie doivent être configurés avec un contexte de personnalisation approprié.
* Les workflows d&#39;export doivent être configurés pour réexporter les logs des messages transactionnels vers l&#39;Experience Platform. Il est recommandé d’exécuter au plus toutes les 4 heures

### Configuration des notifications push mobiles (facultatif)

1. Mise en oeuvre du SDK Mobile Experience Platform pour collecter des jetons push et des informations de connexion afin de lier à des profils clients connus
1. Tirez parti des balises Adobe et créez une propriété mobile avec l’extension suivante :
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * Identité pour Edge Network
   * Mobile Core
1. Assurez-vous que vous disposez d’un flux de données dédié pour les déploiements d’applications mobiles par rapport aux déploiements web.
1. Pour plus d’informations, reportez-vous à la section [Guide de Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Il se peut que les jetons mobiles doivent être collectés à la fois dans Journey Optimizer et Campaign si vous souhaitez envoyer des communications en temps réel via Journey Optimizer et des notifications push par lots via Campaign. Campaign v8 requiert l’utilisation exclusive du SDK Campaign pour capturer des jetons push.

<br>

## Documentation connexe

* [Documentation Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Documentation de Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation pour Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)