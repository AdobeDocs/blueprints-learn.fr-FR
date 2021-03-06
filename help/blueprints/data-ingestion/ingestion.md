---
title: Plan directeur de la préparation et de l’ingestion de données
description: Ce plan directeur décrit toutes les méthodes de préparation et d’ingestion des données dans Adobe Experience Platform.
solution: Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1
source-git-commit: 5ee530220cd5928f9ab4aabd50148b963273d67c
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 100%

---

# Plan directeur de la préparation et de l’ingestion de données

Le plan directeur de la préparation et de l’ingestion de données englobe et décrit toutes les méthodes de préparation et d’ingestion des données dans Adobe Experience Platform.

La préparation des données inclut le mapping de données sources vers un schéma du Modèle de données d’expérience (XDM). Elle inclut également la réalisation de transformations sur les données, y compris le formatage de la date ; le fractionnement, la concaténation ou les conversions de champ ; et la jonction, la fusion ou la ressaisie d’informations. La préparation des données permet d’unifier les données clients pour fournir une analyse agrégée / filtrée, y compris la création de rapports ou la préparation de données pour l’assemblage d’un profil client, la data science, l’activation.

## Architecture

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architecture de référence pour le plan directeur de la préparation et de l’ingestion de données" style="width:90%; border:1px solid #4a4a4a" />

## Garde-fous de l’ingestion des données

Le diagramme ci-dessous illustre les principaux garde-fous de performance et la latence de l’ingestion de données dans Adobe Experience Platform.

<img src="../experience-platform/assets/aep_data_flow_guardrails.svg" alt="Flux de données Experience Platform" style="border:1px solid #4a4a4a" width="90%" />

## Méthodes d’ingestion de données

| Méthodes d’ingestion | Description |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDK web / mobile | Latence :<ul><li>Temps réel - même collection de page sur Edge Network</li><li>Ingestion en continu vers le profil ~ 1 minute</li><li>Ingestion en continu vers le lac de données (micro-lot ~ 15 minutes)</ul>Documentation : <ul><li>[SDK web](https://experienceleague.adobe.com/docs/web-sdk.html?lang=fr)</li><li>[Tutoriel sur la mise en œuvre d’Adobe Experience Cloud avec le SDK web](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=fr)</li><li>[SDK mobile](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)</li><li>[Tutoriel sur la mise en œuvre d’Adobe Experience Cloud dans les applications mobiles](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html?lang=fr)</li></ul> |
| Sources de diffusion | [Sources de diffusion en continu](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr#connectors)<br>Latence :<ul><li>Temps réel - même collection de page sur Edge Network</li><li>Ingestion en continu vers le profil ~ 1 minute</li><li>Ingestion en continu vers le lac de données (micro-lot ~ 15 minutes)</li></ul> |
| API de diffusion | [API de serveur Edge Network (préférée)](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/data-collection/interactive-data-collection.html?lang=fr) - Prend en charge les services Edge, notamment la segmentation Edge et l’<br>[API Core Service de collecte de données](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/streaming/http.html?lang=fr) - Ne prend pas en charge les services Edge, redirige directement vers le hub.<br>Latence :<ul><li>Temps réel - même collection de page sur Edge Network</li><li>Ingestion en continu vers le profil ~ 1 minute</li><li>Ingestion en continu vers le lac de données (micro-lot ~ 15 minutes)</li><li>7 Go/heure</li></ul>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=fr#what-can-you-do-with-streaming-ingestion%3F) |
| Outillage ETL | Utilisez les outils ETL pour modifier et transformer les données d’entreprise avant ingestion dans Experience Platform.<br><br>Latence :<ul><li>La synchronisation dépend du planning de l’outil ETL externe, puis les garde-fous d’ingestion standard s’appliquent en fonction de la méthode utilisée pour l’ingestion.</li></ul> |
| Sources de lots | Récupération planifiée à partir des sources<br>Latence : ~ 200 Go/heure<br><br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[Tutoriels vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html?lang=fr) |
| Lot API | Latence :<ul><li>Ingestion par lots dans le Profil en fonction de la taille et des charges de trafic ~ 45 minutes</li><li>Ingestion par lots dans le lac de données en fonction de la taille et des charges de trafic</li></ul>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=fr#batch) |
| Connecteurs d’applications Adobe | Ingèrent automatiquement les données qui proviennent des applications Adobe Experience Cloud<ul><li>Adobe Analytics : [Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=fr#connectors) et [Tutoriel vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html?lang=fr)</li><li>Audience Manager : [Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr#connectors) et [Tutoriel vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html?lang=fr)</li></ul> |


## Méthodes de préparation des données

| Méthodes de préparation des données | Description |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Outil ETL externe ([!DNL Snaplogic], [!DNL Mulesoft], [!DNL Informatica], etc.) | Effectuez des transformations complexes dans l’outillage ETL et utilisez des API ou des connecteurs sources Experience Platform standard [!UICONTROL Flow Service] pour ingérer les données résultantes. |
| [!UICONTROL Service de requête] - Préparation des données | Associe, fractionne, fusionne, transforme, interroge et filtre des données dans un nouveau jeu de données. <br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr#sql) pour l’utilisation de Create Table as Select (CTAS) |
| Fonctions XDM Mapper et Data Prep (en flux continu et par lots) | Faites correspondre les attributs source au format CSV ou JSON avec les attributs XDM lors de l’ingestion de données dans Experience Platform.<br>Calculent des fonctions sur les données au fur et à mesure qu’elles sont ingérées ; c’est-à-dire le formatage, le fractionnement, la concaténation des données, etc.<br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=fr) |

## Articles de blog connexes

* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [[!DNL High Throughput Ingestion with Iceberg]](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [[!DNL Query Service Tricks in Adobe Experience Platform (Writing Queries and Storing Derived Datasets)]](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [[!DNL Digging into Adobe Experience Platform’s Experience Data Model to More Fully Understand the Power of Real-time Customer Profile]](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
