---
title: Plan de préparation et d'importation des données
description: Ce schéma montre toutes les méthodes d'assimilation et de préparation des données à Adobe Experience Platform.
solution: Experience Platform,Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1,5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: 2343151a1ed5374c299fb9317f6282c232d5d23b
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# Plan de préparation et d&#39;importation des données

Le plan de préparation des données et d&#39;importation englobe toutes les méthodes permettant de préparer et d&#39;assimiler les données à Adobe Experience Platform.

La préparation des données comprend le mappage des données source au schéma du modèle de données d’expérience (XDM). Il comprend également les transformations effectuées sur les données, y compris le formatage des dates, le fractionnement/concaténation/conversions de champs et la jonction/fusion/re-saisie d’enregistrements. La préparation des données permet d’unifier les données client afin de fournir une analyse agrégée/filtrée, y compris le rapports ou la préparation des données pour l’assemblage/la science/activation des données du profil client.

## Architecture

<img src="assets/dataingest.svg" alt="Architecture de référence pour le plan directeur de préparation des données et d'importation" style="border:1px solid #4a4a4a" />

## Méthodes d&#39;assimilation des données

| Méthodes d&#39;assimilation | Description |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDK Web/Mobile | Latence :<ul><li>Temps réel : même collection de pages pour Edge Network</li><li>L&#39;assimilation en flux continu à un Profil ~1 minute</li><li>Extraction en flux continu vers le lac de données (micro-lot ~15 minutes)</ul>Documentation : <ul><li>[SDK Web](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[SDK mobile](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| Sources de diffusion en continu | Latence :<ul><li>Temps réel : même collection de pages pour Edge Network</li><li>L&#39;assimilation en flux continu à un Profil ~1 minute</li><li>Extraction en flux continu vers le lac de données (micro-lot ~15 minutes)</li></ul>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| API de diffusion en continu | Latence :<ul><li>Temps réel : même collection de pages pour Edge Network</li><li>L&#39;assimilation en flux continu à un Profil ~1 minute</li><li>Extraction en flux continu vers le lac de données (micro-lot ~15 minutes)</li><li>7 Go/heure</li></ul>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| Outils ETL | Utilisez les outils ETL pour modifier et transformer les données d’entreprise avant leur assimilation en Experience Platform.<br><br>Latence :<ul><li>Le minutage dépend de la planification des outils ETL externes, puis les garde-fous d&#39;assimilation standard s&#39;appliquent en fonction de la méthode utilisée pour l&#39;assimilation.</li></ul> |
| Sources de lots | Récupération planifiée à partir de sources<br>Latence : ~ 200 Go/heure<br><br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[Tutorials vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| API de lot | Latence :<ul><li>Apport du lot au Profil en fonction de la taille et des charges de trafic ~45 minutes</li><li>Apport du lot au lac de données en fonction de la taille et des charges de trafic</li></ul>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Connecteurs d’applications d’Adobe | assimiler automatiquement les données provenant des applications Adobe Experience Cloud ;<ul><li>Adobe Analytics : [Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors) et [Didacticiel vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager : [Documentation](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors) et [Didacticiel vidéo](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## Méthodes de préparation des données

| Méthodes de préparation des données | Description |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!UICONTROL Espace de travail]  des sciences de données - Prévisualisation des données | Transformation pilotée par le modèle, transformation par script.<br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>| Outil ETL externe ([!DNL Snaplogic], [!DNL Mulesoft], [!DNL Informatica], etc.) | Effectuez des transformations complexes dans l&#39;outil ETL et utilisez les API source Experience Platform standard ou les connecteurs pour assimiler les données résultantes.                                                                                                                                                               |

| [!UICONTROL Requête Service] - Data Prep                                  | Associe, sépare, fusionne, transforme, Requête et filtre des données dans un nouveau jeu de données. Utilisation de Create Table as Select (CTAS) <br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| Fonctions XDM Mapper &amp; Data Prep (Diffusion en continu et traitement par lot)     | Mappez les attributs source au format CSV ou JSON dans les attributs XDM lors de l’assimilation d’Experience Platform.<br>calculer les fonctions sur les données au fur et à mesure de leur assimilation ; c&#39;est-à-dire le formatage des données, le fractionnement, la concaténation, etc.<br>[Documentation](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## Publications de blog connexes

* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [[!DNL High Throughput Ingestion with Iceberg]](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [[!DNL Query Service Tricks in Adobe Experience Platform (Writing Queries and Storing Derived Datasets)]](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [[!DNL Digging into Adobe Experience Platform’s Experience Data Model to More Fully Understand the Power of Real-time Customer Profile]](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
