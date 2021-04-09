---
title: Modèle d'Analyse des données et de renseignement
description: Ce plan montre la capacité de Adobe Experience Platform à effectuer une requête exploratoire et l'analyse des données qui existent dans le lac de données.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Modèle d&#39;Analyse des données et de renseignement

L&#39;Analyse des données et le renseignement permettent à Adobe Experience Platform d&#39;effectuer une requête exploratoire et une analyse des données qui existent dans le lac des données.

L&#39;Experience Platform [!UICONTROL Requête Service] permet l&#39;exécution de requêtes SQL sur les données. [!UICONTROL L’] espace de travail Data Science permet l’exploration des données, la science des données et les charges de travail d’apprentissage automatique sur les données.

En outre, Experience Platform permet des connexions avec des clients SQL tiers, des interfaces et des outils de Business Intelligence (BI) pour se connecter directement aux données dans l&#39;Experience Platform, y accéder et les requête, en utilisant le protocole [!DNL PostgreSQL].

Certains garde-fous s&#39;appliquent au délai d&#39;expiration de la requête et à la quantité de données incluses dans le résultat de la requête, comme indiqué dans les détails du plan directeur.

## Cas d’utilisation

* Requête interactive et agrégation des données
* Accès aux lignes et aux colonnes aux données imbriquées pour exploration et validation
* Tableaux de bord et visualisation des données au moyen de l&#39;outil Business Intelligence

## Applications

* Adobe Experience Platform

## Architecture

<img src="assets/dataexplore.svg" alt="Architecture de référence pour l'exploration des données d'entreprise et le plan directeur des Rapports" style="border:1px solid #4a4a4a" />

## Gardiens

* Délai de 10 minutes pour les requêtes interactives
* Limite de 100 enregistrements renvoyée dans l’interface utilisateur
* Limite de 50 000 enregistrements renvoyée via le connecteur SQL

## Etapes de mise en oeuvre

1. Configurez des jeux de données et des schémas pour l&#39;assimilation de données dans le lac de données.
1. Envoi de données.
1. Vérifiez que les données sont disponibles pour [!UICONTROL Requête Service] et [!UICONTROL Data Science Workspace] pour l&#39;accès brut et la requête.
1. Connectez les outils de Business Intelligence et les clients SQL à [!UICONTROL Requête Service] pour la visualisation, la requête de données et l&#39;exploration.

## Documentation connexe

* [Description du produit Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Documentation de requête ] Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
