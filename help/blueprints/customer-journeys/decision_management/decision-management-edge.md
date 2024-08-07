---
title: Plan directeur de la gestion des décisions sur Edge
description: Diffusez des offres personnalisées à vos clients sur l’ensemble des canaux, y compris dans les expériences web et mobiles en temps réel.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 80%

---

# Journey Optimizer - [!DNL Decision Management] sur le plan directeur Edge

[!DNL Decision Management] est un service fourni dans le cadre de [!DNL Journey Optimizer]. Ce plan directeur décrit les cas d’utilisation et les fonctionnalités techniques de l’application et fournit une analyse approfondie des différents composants architecturaux et des considérations qui entrent en compte dans la gestion des décisions.

>[!MORELIKETHIS]
>
>Pour en savoir plus sur [!DNL Decision Management], consultez la [présentation du plan directeur](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=fr) ou consultez la [documentation du produit](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr).

[!DNL Decision Management] peut être déployé de l’une des deux façons suivantes. Le premier s’effectue via le [!DNL Experience Platform] Hub, qui est une architecture de centre de données unique. L’approche de type « hub » permet d’exécuter, de personnaliser et de diffuser les offres avec une latence en secondes. L’architecture du hub est donc mieux adaptée aux expériences client qui ne demandent pas de latence inférieure à une seconde, par exemple pour les prises de décisions sur les offres pour les kiosques ou les expériences assistées par agent, telles que dans les centres d’appel ou les interactions en personne.

La seconde approche est via l’Experience Platform [!DNL Edge Network], qui est une infrastructure géographiquement répartie mondialement et qui sert des expériences de sous-seconde et de millisecondes rapides. Expérience client finale exécutée par l’infrastructure Edge la plus proche de la géolocalisation des consommateurs afin de minimiser la latence. [!DNL Decision Management] sur Edge est conçu pour proposer des expériences client en temps réel. Il s’agit notamment des expériences telles que les demandes de personnalisation entrantes web ou mobiles.

Ce plan directeur couvrira les détails de la gestion des décision sur Edge.

Pour en savoir plus sur la gestion des décisions sur le hub, reportez-vous au plan directeur [Gestion des décisions sur le hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=fr).

## Cas d’utilisation de la gestion des décisions sur Edge

* Cas d’utilisation de la diffusion en continu où la latence du contexte du profil est stricte en dessous d’une latence de 15 minutes et où l’exécution de la gestion des décisions est en sous-seconde.
* Personnalisation en ligne via des expériences entrantes web ou mobiles
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, par e-mail et les autres canaux d’interaction par le biais d’Adobe Journey Optimizer

<br>

## Architecture

<img src="../assets/offers_edge.svg" alt="Plan directeur de la gestion des décisions concernant l’architecture de référence sur Edge" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Modèles d’intégration

| Intégration | Description |
| :-- | :--- |
| [Gestion des décisions avec Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=fr) | La gestion des décisions peut être intégrée à Adobe Target afin que les offres puissent être testées et diffusées en tant qu’expériences Target. |

## Conditions préalables

Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.

<br>

## Garde-fous

* Pour en savoir plus sur les garde-fous Journey Optimizer, consultez [Garde-fous Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=fr).

* Pour en savoir plus sur les garde-fous de la gestion des décisions, consultez la [description du produit de gestion des décisions](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html).

[Barrières de sécurité et guide de latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## Modèles de mise en œuvre

* Utilisez le SDK web ou mobile pour le déploiement sur des sites web et des applications mobiles afin de mettre en œuvre la gestion des décisions à l’endroit où le SDK a été déployé.
   * [Plan directeur de SDK web ou mobile](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=fr)
   * [SDK web](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html?lang=fr)
   * [SDK Mobile](https://aep-sdks.gitbook.io/docs/)

Ou

* Pour une mise en œuvre serveur à serveur de l’API, utilisez l’API de service Edge Network pour mettre en œuvre directement la gestion des décisions serveur à serveur.
   * [API du serveur Edge Network](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html?lang=fr)

<br>

## Étapes de mise en œuvre

### Adobe Experience Platform

#### Schéma/jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=fr) dans Experience Platform, en fonction des données fournies par le client.
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

## Documentation connexe

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=fr)
* [Gestion des décisions Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr)
* [Description du produit Adobe Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Description du produit de gestion des décisions Adobe](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html)
