---
title: Plan directeur pour Adobe Experience Platform et les messages par lots
description: Exécution des campagnes de messagerie planifiées et par lots à l’aide d’Adobe Experience Platform en tant que hub central des profils clients et de la segmentation.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
source-git-commit: 3c950cebaa25901ae50433775c510ed834d8bcd5
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 99%

---

# Plan directeur pour Adobe Experience Platform et les messages par lots

Exécution des campagnes de messagerie planifiées et par lots à l’aide d’Adobe Experience Platform en tant que hub central des profils clients et de la segmentation.

## Cas d’utilisation

* Campagnes de messages électroniques programmés
* Campagnes d’intégration et de remarketing

## Applications

* Adobe Experience Platform
* Adobe Campaign Classic ou Standard

## Modèles d’intégration

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architecture

<img src="assets/aepbatch.svg" alt="Architecture de référence pour la messagerie par lots et plan directeur d’Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Garde-fous

* Ne prend en charge que les déploiements d’une seule unité organisationnelle d’Adobe Campaign
* Adobe Campaign est une source de confirmation pour tous les profils actifs, c’est-à-dire que les profils doivent exister dans Adobe Campaign et que de nouveaux profils ne doivent pas être créés en fonction des segments Experience Platform.
* La réalisation de l’abonnement au segment depuis Experience Platform est latente à la fois pour les segments par lots (1 par jour) que par flux continu (environ 5 minutes)

Partage des segments **[!UICONTROL Real-time Customer Data Platform] vers Adobe Campaign :**

* Limite de 20 segments recommandée
* L’activation est limitée à toutes les 24 heures
* Seuls les attributs de schéma d’union sont disponibles pour l’activation (pas de prise en charge des événements de tableau / mappage / expérience).
* Recommandation de ne pas dépasser 20 attributs par segment
* Un fichier par segment de tous les profils avec des segments d’appartenance « réalisés » OU si l’appartenance au segment est ajoutée en tant qu’attribut dans le fichier, les profils « réalisés » et « sortis »
* Les exportations de segments incrémentielles ou complètes sont prises en charge
* Le cryptage des fichiers n’est pas pris en charge
* Les workflows d’exportation d’Adobe Campaign doivent être exécutés toutes les 4 heures au plus
* Voir [garde-fous pour l’ingestion de profils et de données dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas Adobe Campaign pour les éléments broadLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour utilisation dans Adobe Campaign.

#### Sources / destinations

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide d’API de diffusion en continu et de connecteurs sources.
1. Configurez la destination de l’enregistrement blob [!DNL Azure] à utiliser avec Adobe Campaign.

#### Déploiement d’applications mobiles

1. Utilisez le SDK Adobe Campaign pour Adobe Campaign Classic ou le SDK Experience Platform pour Adobe Campaign Standard. Si vous disposez d’Experience Platform Launch, il est recommandé d’utiliser l’extension Adobe Campaign Classic ou Adobe Campaign Standard avec le SDK Experience Platform.

#### Adobe Campaign

1. Configurez des schémas pour le profil, les données de recherche et les données de personnalisation de diffusion pertinentes.

>[!IMPORTANT]
>
>Il est essentiel de comprendre à ce stade quel est le modèle de données dans Experience Platform pour les données de profil et d’événement afin de savoir quelles données seront requises dans Adobe Campaign.

#### Importer des workflows

1. Chargez et ingérez les données de profil simplifiées sur le SFTP d’Adobe Campaign.
1. Chargez et ingérez les données d’orchestration et de personnalisation de la messagerie sur le SFTP d’Adobe Campaign.
1. Ingérez les segments d’Experience Platform à partir du blob [!DNL Azure] via des workflows.

#### Exporter des workflows

1. Renvoyez les journaux d’Adobe Campaign à Experience Platform via des workflows toutes les quatre heures (broadLog, trackingLog, adresses non livrables).
1. Renvoyez les préférences de profil à Experience Platform via des workflows créés par consultation toutes les quatre heures (facultatif)


## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation pour Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
