---
title: Journey Optimizer - Plan directeur de la messagerie tierce
description: Illustre comment Adobe Journey Optimizer peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 97%

---

# Plan directeur de la messagerie tierce

Illustre comment Adobe Journey Optimizer peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées.

<br>

## Architecture

<img src="assets/3rd-party-messaging-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Conditions préalables

Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.

Application de messagerie tierce

* Doit prendre en charge les appels d’API REST pour envoyer des payloads transactionnels.

<br>

## Garde-fous

[Lien de produit pour les garde-fous de Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)


## Étapes de mise en œuvre

### Adobe Experience Platform

#### Schéma/jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=fr) dans Experience Platform, en fonction des données fournies par le client.
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

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=fr) à l’aide des API de streaming et des connecteurs sources.

### Journey Optimizer

1. Configurez votre source de données Experience Platform et déterminez les champs à mettre en cache dans le cadre des données profileStreaming utilisées pour lancer un parcours client. Vous devez d’abord configurer Journey Optimizer pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configuration d’actions personnalisées pour une application tierce.

### Configuration push mobile (facultative, car des jetons peuvent être collectés par des tiers)

1. Implémentez le SDK Mobile Experience Platform pour collecter des jetons push et des informations de connexion afin de les lier à des profils clients connus.
1. Tirez parti des balises Adobe et créez une propriété mobile avec l’extension suivante :
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identité pour [!DNL Edge Network]
   * Mobile Core
1. Assurez-vous que vous disposez d’un flux de données dédié pour les déploiements d’applications mobiles par rapport aux déploiements web.
1. Pour plus d’informations, reportez-vous à la section [Guide d’Adobe Journey Optimizer Mobile](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/).

<br>

## Documentation connexe

* [Documentation pour Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
