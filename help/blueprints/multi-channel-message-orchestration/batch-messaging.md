---
title: Messagerie par lots et plan stratégique Adobe Experience Platform
description: Exécution des campagnes de messagerie planifiées et par lots à l’aide d’Adobe Experience Platform en tant que hub central des profils clients et de la segmentation.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 81df87f850b7ac4be9dce7a3b96d39a3a47685c5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Messagerie par lots et plan stratégique Adobe Experience Platform

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

<img src="assets/aepbatch.svg" alt="Architecture de référence pour la messagerie par lots et le schéma directeur Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Garde-fous

* Prend uniquement en charge les déploiements d&#39;une seule unité d&#39;organisation Adobe Campaign
* L&#39;Adobe Campaign est une source de vérité pour tous les profils principaux, ce qui signifie que les profils doivent exister dans Adobe Campaign et que les nouveaux profils ne doivent pas être créés sur la base de segments Experience Platform.
* La réalisation de l’appartenance au segment depuis Experience Platform est latente à la fois pour les segments par lot (1 par jour) que par flux (environ 5 minutes)

**[!UICONTROL Partage de ] segments de la plateforme de données clientes en temps réel vers Adobe Campaign :**

* Limite de 20 segments recommandée
* L’activation est limitée à toutes les 24 heures
* Seuls les attributs de schéma d’union sont disponibles pour l’activation (pas de prise en charge des événements de tableau / mappage / expérience).
* Recommandation de ne pas dépasser 20 attributs par segment
* Un fichier par segment de tous les profils avec des segments d’appartenance « réalisés » OU si l’appartenance au segment est ajoutée en tant qu’attribut dans le fichier, les profils « réalisés » et « sortis »
* Les exportations de segments incrémentielles ou complètes sont prises en charge
* Le cryptage des fichiers n’est pas pris en charge
* workflows d’exportation Adobe Campaign à exécuter toutes les 4 heures au maximum
* Voir [garde-fous pour l’ingestion de profils et de données dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités dans Experience Platform, en fonction des données fournies par le client.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. Créez des schémas Adobe Campaign pour WideLog, trackingLog, les adresses non livrables et les préférences de profil (facultatif).
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) des ensembles de données dans l’Experience Platform pour que les données soient assimilées.
1. [Ajoutez les ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) étiquettes d’utilisation des données dans l’Experience Platform au jeu de données pour la gouvernance.
1. [Créez des stratégies pour appliquer la gouvernance sur les destinations.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez le schéma et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Configurez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) des stratégies de fusion pour les différentes vues du Profil [!UICONTROL  client en temps ] réel (facultatif).
1. Créez des segments pour l’utilisation de Adobe Campaign.

#### Sources / destinations

1. [Ingérez des données dans Experience Platform à l’aide d’API de diffusion en continu et de connecteurs source.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. Configurez la destination de l&#39;enregistrement blob [!DNL Azure] à utiliser avec Adobe Campaign.

#### Déploiement d’applications mobiles

1. Mise en oeuvre du SDK Adobe Campaign pour Adobe Campaign Classic ou du SDK Experience Platform pour Adobe Campaign Standard. Si l’Experience Platform Launch est présent, il est recommandé d’utiliser l’extension Adobe Campaign Classic ou Adobe Campaign Standard avec le SDK Experience Platform.

#### Adobe Campaign

1. Configurez des schémas pour le profil, les données de recherche et les données de personnalisation de livraison pertinentes.

>[!IMPORTANT]
>
>Il est essentiel de comprendre à ce stade quel est le modèle de données dans l&#39;Experience Platform pour les données de profil et de événement afin que vous sachiez quelles données seront nécessaires à Adobe Campaign.

#### Importer des workflows

1. Chargez et assimilez des données de profil simplifiées sur Adobe Campaign sFTP.
1. Chargez et assimilez les données d’orchestration et de personnalisation des messages sur Adobe Campaign sFTP.
1. Ingérez les segments d’Experience Platform à partir du blob [!DNL Azure] via des workflows.

#### Exporter des workflows

1. Renvoyez les journaux Adobe Campaign à l’Experience Platform par workflows toutes les quatre heures (largeLog, trackingLog, adresses non livrables).
1. Renvoyez les préférences de profil à Experience Platform via des workflows créés par consultation toutes les quatre heures (facultatif)


## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation pour Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
