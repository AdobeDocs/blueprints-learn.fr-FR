---
title: Exploration des données d'entreprise et schéma directeur des Rapports
description: Ce plan montre la capacité de Adobe Experience Platform à effectuer une requête exploratoire et l'analyse des données qui existent dans le lac de données.
solution: Experience Platform
kt: 7207
thumbnail: null
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Exploration des données d&#39;entreprise et schéma directeur des Rapports

L&#39;exploration et le Rapports des données d&#39;entreprise comprennent la capacité de Adobe Experience Platform d&#39;effectuer une requête exploratoire et l&#39;analyse des données qui existent dans le lac des données.

Experience Platform Requête Service permet l&#39;exécution de requêtes SQL sur les données. L’espace de travail Data Science permet d’effectuer des travaux d’exploration des données, de science des données et d’apprentissage automatique sur les données.

De plus, Experience Platform permet des connexions avec des clients SQL tiers, des interfaces et des outils de Business Intelligence (BI) pour se connecter directement, accéder et requête aux données dans l&#39;Experience Platform, en utilisant le protocole PostgreSQL.

Certaines garde-fous s’appliquent au délai d’expiration de la requête et à la quantité de données incluses dans le résultat de la requête, comme indiqué dans les détails du scénario.

## Cas d’utilisation

* Requête interactive et agrégation des données
* Accès aux lignes et aux colonnes aux données imbriquées pour exploration et validation
* Tableaux de bord et visualisation des données au moyen de l&#39;outil Business Intelligence

## Applications

* Adobe Experience Platform

## Scénarios

| Scénario | Description | Applications/services Experience Cloud |
|---|---|---|
| **Exploration des données - requête brute des données** | <ul><li>Ecrivez et exécutez des requêtes SQL dans le lac de données à l&#39;aide de l&#39;interface utilisateur de la requête interactive ou d&#39;un client SQL connecté. Data Science Workspace peut également être utilisé pour requête et obtenir des informations à partir des données brutes dans l’Experience Platform.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |
| **Enterprise Dashboard** | <ul><li>Connectez les outils du Business Intelligence à l’Experience Platform pour visualiser les données en vue d’un tableau de bord et de cas d’utilisation de rapports.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Architecture

<img src="assets/dataexplore.svg" alt="Architecture de référence pour l'exploration des données d'entreprise et le plan directeur des Rapports" style="border:1px solid #4a4a4a" />

## Gardiens

* Délai de 10 minutes pour les requêtes interactives
* Limite de 100 enregistrements renvoyée dans l’interface utilisateur
* Limite de 50 000 enregistrements renvoyée via le connecteur SQL

## Etapes de mise en oeuvre

1. Configurez des jeux de données et des schémas pour l&#39;assimilation de données dans le lac de données.
1. Envoi de données.
1. Vérifiez que les données sont disponibles pour Requête Service et Data Science Workspace pour un accès et une requête bruts.
1. Connectez les outils de Business Intelligence et les clients SQL à Requête Service pour la visualisation, la requête de données et l’exploration.

## Documentation connexe

* [Description du produit Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentation de requête Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)