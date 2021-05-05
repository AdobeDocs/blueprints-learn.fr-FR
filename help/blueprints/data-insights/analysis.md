---
title: Modèle d'Analyse des données et de renseignement
description: Ce plan directeur montre la capacité d’Adobe Experience Platform à effectuer des requêtes exploratoires et une analyse des données existant dans un lac de données.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 6365fa00a77ba22774b2d6de3e882a3e09dcae0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Modèle d&#39;Analyse des données et de renseignement

L&#39;Analyse des données et le renseignement permettent à Adobe Experience Platform d&#39;effectuer une requête exploratoire et une analyse des données qui existent dans le lac des données.

L&#39;Experience Platform [!UICONTROL Requête Service] permet l&#39;exécution de requêtes SQL sur les données. [!UICONTROL L’] espace de travail Data Science permet l’exploration des données, la science des données et les charges de travail d’apprentissage automatique sur les données.

En outre, Experience Platform permet des connexions avec des clients SQL tiers, des interfaces et des outils de Business Intelligence (BI) pour se connecter directement aux données dans l&#39;Experience Platform, y accéder et les requête, en utilisant le protocole [!DNL PostgreSQL].

Certains garde-fous s&#39;appliquent au délai d&#39;expiration de la requête et à la quantité de données incluses dans le résultat de la requête, comme indiqué dans les détails du plan directeur.

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

1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) des schémas pour que les données soient assimilées.
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) des jeux de données pour que les données soient assimilées.
1. [Ingérez les données dans Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion).
1. Vérifiez que les données sont disponibles pour [!UICONTROL Requête Service] et [!UICONTROL Data Science Workspace] pour l&#39;accès brut et la requête.
1. Connectez les outils de Business Intelligence et les clients SQL à [!UICONTROL Requête Service] pour la visualisation, la requête de données et l&#39;exploration.

## Documentation connexe

* [Description d’Adobe Experience Platform Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentation sur Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr)
