---
title: Journey Optimizer avec plan directeur Adobe Campaign v8
description: Illustre l’utilisation d’Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.
solution: Journey Optimizer, Campaign, Campaign v8, Campaign v8 Client Console
version: Campaign v8, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: 7547cdc57e50d63f4a7949c00a77b82c86da831e
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 63%

---

# Journey Optimizer avec plan directeur Adobe Campaign v8

Montre comment Adobe [!DNL Journey Optimizer] peut être utilisé avec Adobe [!DNL Campaign] pour envoyer des messages en mode natif en utilisant le serveur de messagerie en temps réel dans [!DNL Campaign].

## Architecture

<img src="assets/ajo-campaign-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>L’utilisation de Journey Optimizer et de Campaign pour envoyer des messages indépendamment les uns des autres est possible mais présente des considérations techniques à prendre en compte. Si vous souhaitez suivre cette route, contactez votre architecte d’entreprise de prévente afin de vous assurer que vous comprenez ce qui sera nécessaire pour prendre en charge l’implémentation.

## Conditions préalables

Examinez les conditions préalables suivantes pour chaque application.

### Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.
* Journey Optimizer et Campaign sont configurés dans la même organisation IMS.

### Campaign v8

* L’instance d’exécution du service de messagerie en temps réel (soit le Message Center) doit être hébergée par les Managed Cloud Services Adobe.
* La création de tous les messages s’effectue dans l’instance Campaign elle-même.

## Garde-fous

* [Limites du produit Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

* [Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Étapes de mise en œuvre

Suivez les implémentations de chaque application décrites ci-dessous.

### Adobe Experience Platform

#### Schéma/jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=fr) dans Experience Platform, en fonction des données fournies par le client.
1. (Facultatif) Créez des schémas basés sur la classe d’événements d’expérience pour les tables broadLog, trackingLog et d’adresses non délivrables d’Adobe Campaign.
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

1. [Ingérer des données dans [!DNL Experience Platform]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide des API de streaming et des connecteurs source.

### Journey Optimizer

1. Configurez votre source de données [!DNL Experience Platform] et déterminez les champs qui doivent être mis en cache dans le cadre de la diffusion en continu profile. Les données utilisées pour initier un parcours client doivent d’abord être configurées dans Journey Optimizer pour obtenir un identifiant d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configurez les actions personnalisées pour l&#39;instance Campaign.

### Campaign v8

* Les modèles de message doivent être configurés avec le contexte de personnalisation approprié.
* Par [!DNL Campaign] standard : les workflows d&#39;export doivent être configurés pour réexporter les logs des messages transactionnels vers Experience Platform. Il est recommandé de l’exécuter au plus toutes les quatre heures.
* Pour [!DNL Campaign] v8.4, il est possible d’utiliser le connecteur Source Adobe [!DNL Campaign] Managed Services dans Experience Platform pour synchroniser la diffusion et le suivi des événements de Campaign dans Experience Platform. Consultez la documentation du connecteur [Source](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr) pour plus de détails.

### Configuration des notifications push mobiles (facultatif)

1. Implémentez [!DNL Experience Platform] Mobile SDK pour collecter des jetons push et des informations de connexion à lier à des profils client connus.
1. Tirez parti des balises Adobe et créez une propriété mobile avec l’extension suivante :
   * [!DNL Journey Optimizer] Adobe | [!DNL Campaign Classic] Adobe | [!DNL Campaign Standard] Adobe
   * [!DNL Edge Network] de [!DNL Experience Platform] Adobe
   * Identité pour [!DNL Edge Network]
   * Mobile Core
1. Assurez-vous de disposer d’un flux de données dédié pour les déploiements d’applications mobiles par rapport aux déploiements web.
1. Pour plus d&#39;informations, suivez le [Guide Adobe Journey Optimizer Mobile](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer/push-notification/).

   >[!IMPORTANT]
   >Il se peut que les jetons mobiles doivent être collectés à la fois dans Journey Optimizer et Campaign si vous souhaitez envoyer des communications en temps réel via Journey Optimizer et des notifications push par lots via Campaign. Campaign v8 requiert l’utilisation exclusive du SDK Campaign pour capturer des jetons push.

## Documentation connexe

* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=fr)
