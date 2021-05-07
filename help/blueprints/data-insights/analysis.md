---
title: Plan directeur pour l’analyse des données et la Data Intelligence
description: Ce plan directeur montre la capacité d’Adobe Experience Platform à effectuer des requêtes exploratoires et une analyse des données existant dans un lac de données.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 85%

---

# Plan directeur pour l’analyse des données et la Data Intelligence

L’analyse des données et la Data Intelligence montre la capacité d’Adobe Experience Platform à effectuer des requêtes exploratoires et une analyse des données qui existent dans un lac de données.

Le service de requête [!UICONTROL Query Service] d’Experience Platform permet d’effectuer des requêtes SQL sur les données. [!UICONTROL Data Science Workspace] permet d’effectuer des tâches d’exploration de données, de data science et de machine learning sur les données.

En outre, Experience Platform permet des connexions avec des clients SQL tiers, des interfaces et des outils de Business Intelligence (BI), leur donnant la possibilité d’accéder et d’interroger directement les données dans Experience Platform, par le biais du protocole [!DNL PostgreSQL].

Certains garde-fous s’appliquent au délai d’expiration de la requête et pour limiter la quantité de données incluse dans le résultat de la requête, comme relevé dans la description du plan directeur.

## Cas d’utilisation

* Requête interactive et agrégation de données
* Accès aux lignes et colonnes des données ingérées pour exploration et validation
* Tableau de bord et visualisation des données via les outils de Business Intelligence

## Applications

* Adobe Experience Platform

## Architecture

<img src="assets/data_exploration.svg" alt="Architecture de référence pour le plan directeur de l’exploration des données d’entreprise et la création de rapports" style="border:1px solid #4a4a4a" />

## Garde-fous

Consultez la documentation du produit Requête Service pour plus d’informations sur les meilleures pratiques et les garde-fous.
[Guide requête Service](https://experienceleague.adobe.com/docs/experience-platform/query/best-practices/writing-queries.html?lang=en#best-practices)

## Étapes d’implémentation

1. [Créez des schémas pour les données à ingérer.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. [Créez des jeux de données pour les données à ingérer.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html)
1. [Ingérez les données dans Experience Platform.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. Donnez la confirmation que les données sont disponibles dans [!UICONTROL Query Service] et [!UICONTROL Data Science Workspace] pour accès brut et exécution des requêtes.
1. Connectez les outils de Business Intelligence et les clients SQL au [!UICONTROL Query Service] pour la visualisation, les requêtes de données et l’exploration.

## Documentation connexe

* [Description d’Adobe Experience Platform Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* Documentation sur [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr)
