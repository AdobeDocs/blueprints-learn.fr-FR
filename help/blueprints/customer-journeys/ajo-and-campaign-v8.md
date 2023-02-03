---
title: Journey Optimizer avec plan directeur Adobe Campaign v8
description: Illustre l’utilisation d’Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: ht
source-wordcount: '1028'
ht-degree: 100%

---

# Journey Optimizer avec plan directeur Adobe Campaign v8

Illustre l’utilisation d’Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.

<br>

## Architecture

<img src="assets/ajo-campaign-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>L’utilisation de Journey Optimizer et de Campaign pour envoyer des messages indépendamment les uns des autres est possible mais présente des considérations techniques à prendre en compte. Si vous souhaitez suivre cette route, contactez votre architecte d’entreprise de prévente afin de vous assurer que vous comprenez ce qui sera nécessaire pour prendre en charge l’implémentation.

<br>

## Conditions préalables

### Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.
* Journey Optimizer et Campaign sont configurés dans la même organisation IMS.

### Campaign v8

* L’instance d’exécution du service de messagerie en temps réel (soit le Message Center) doit être hébergée par les Managed Cloud Services Adobe.
* La création de tous les messages s’effectue dans l’instance Campaign elle-même.

<br>

## Garde-fous

[Lien de produit pour les garde-fous de Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)

### Autres mécanismes de sécurisation de Journey Optimizer

* La limitation est désormais disponible par le biais de l’API pour garantir que le système de destination n’est pas saturé au point d’échec. Cela signifie que les messages qui vont au-delà du plafond seront ignorés et ne sont jamais envoyés. La limitation n’est pas prise en charge.
   * Connexions max. - Nombre maximal de connexions http/s qu’une destination peut gérer
   * Nombre d’appels max - Nombre maximal d’appels pouvant être effectués dans le paramètre periodInMs
   * periodInMs - temps en millisecondes
* Les parcours initiés d’abonnement à un segment peuvent fonctionner suivant deux modes :
   * Segments par lot (actualisés toutes les 24 heures)
   * Segments par diffusion en flux continu (qualification de moins de 5 minutes)
* Segments par lot : veillez à connaître le volume quotidien des utilisateurs qualifiés et à garantir que le système de destination peut gérer les pics de débit par parcours et sur tous les parcours.
* Segments en diffusion en continu : veillez à ce que le pic initial des qualifications de profil puisse être traité en même temps que le volume de qualification des diffusions en continu quotidien par parcours et sur tous les parcours
* Gestion des décisions non prise en charge
* Les événements métier ne sont pas pris en charge.
* Intégrations sortantes vers des systèmes tiers
   * Pas de prise en charge d’une seule adresse IP statique, car notre infrastructure est définie pour plusieurs clients (doit mettre en liste autorisée toutes les adresses IP du centre de données).
   * Seules les méthodes de POST et de PUT sont prises en charge pour les actions personnalisées.
   * Prise en charge de l’authentification : token | password | OAuth2
* Il n’est pas possible de regrouper et de déplacer des composants individuels d’Adobe Experience Platform ou de Journey Optimizer entre différentes sandbox. Vous devez les réimplémenter dans les nouveaux environnements.

<br>

### Campaign (v8)

* L’instance d’exécution de Message Center doit être hébergée par Adobe Managed Cloud Services.
* Débit des messages
   * AC (v8) jusqu’à 1 million par heure selon le package
* AC (v8) ne prend pas en charge la gestion des décisions dans les messages.
* Pas de limitation des appels API sortants effectués vers Campaign.
* Avec Campaign v8.4, il est possible d’utiliser le connecteur source Adobe Campaign Managed Services dans Experience Platform pour synchroniser les événements de diffusion et de suivi de Campaign dans Experience Platform. Pour plus d’informations, consultez la documentation sur les connecteurs source. [Lien](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr)

<br>

## Étapes de mise en œuvre

### Adobe Experience Platform

#### Schéma/jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=fr) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas basés sur des classes d’événements d’expérience pour les tables broadLog, trackingLog et adresses non livrables d’Adobe Campaign (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil/identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour utilisation dans Journey.

#### Sources/destinations

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide des API de streaming et des connecteurs sources.

### Journey Optimizer

1. Configurez votre source de données Experience Platform et déterminez les champs à mettre en cache dans le cadre des données profileStreaming utilisées pour lancer un parcours client. Vous devez d’abord configurer Journey Optimizer pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configurez des actions personnalisées pour l’instance Campaign.

### Campaign v8

* Les modèles de messagerie doivent être configurés avec un contexte de personnalisation approprié.
* Pour Campaign Standard, les workflows d’export doivent être configurés pour réexporter les logs des messages transactionnels vers Experience Platform. Il est recommandé d’effectuer des exécutions au plus toutes les quatre heures.
* Pour Campaign v8.4, il est possible d’utiliser le connecteur source Adobe Campaign Managed Services dans Experience Platform pour synchroniser les événements de diffusion et de suivi de Campaign dans Experience Platform. Pour plus d’informations, consultez la documentation sur les connecteurs source. [Lien](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr)

### Configuration des notifications push mobiles (facultatif)

1. Implémentez le SDK Mobile Experience Platform pour collecter des jetons push et des informations de connexion afin de les lier à des profils clients connus.
1. Tirez parti des balises Adobe et créez une propriété mobile avec l’extension suivante :
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * Identité       pour Edge Network
   * Mobile Core
1. Assurez-vous que vous disposez d’un flux de données dédié pour les déploiements d’applications mobiles par rapport aux déploiements web.
1. Pour plus d’informations, reportez-vous à la section [Guide d’Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer).

   >[!IMPORTANT]
   >Il se peut que les jetons mobiles doivent être collectés à la fois dans Journey Optimizer et Campaign si vous souhaitez envoyer des communications en temps réel via Journey Optimizer et des notifications push par lots via Campaign. Campaign v8 requiert l’utilisation exclusive du SDK Campaign pour capturer des jetons push.

<br>

## Documentation connexe

* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=fr)
