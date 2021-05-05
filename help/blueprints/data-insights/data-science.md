---
title: Plan directeur sur la data science personnalisée pour l’enrichissement de profil
description: Ce plan directeur montre comment Data Science Workspace d’Adobe Experience Platform utilise les données dans Experience Platform pour former, déployer et évaluer des modèles afin de fournir des informations de machine learning à partir des données.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: 6365fa00a77ba22774b2d6de3e882a3e09dcae0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plan directeur sur la data science personnalisée pour l’enrichissement de profil

Le plan directeur des sciences des données personnalisées pour l&#39;Enrichissement des Profils illustre comment les données du Adobe Experience Platform peuvent être utilisées dans [!UICONTROL Data Science Workspace] pour former, déployer et marquer des modèles afin de fournir des informations d&#39;apprentissage automatique. Ces modèles peuvent directement être générés dans un jeu de données activé pour [!UICONTROL Profil client en temps réel] afin d’enrichir davantage les profils client. Ces informations peuvent ensuite être utilisées pour la personnalisation. Parmi les exemples d’informations d’apprentissage automatique, citons le score de valeur sur la durée de vie, l’affinité des produits et des catégories, la propension à la conversion ou la propension à l’activité.

## Cas d’utilisation

* Extraire des informations et découvrir des modèles à partir des données client dans Experience Platform. Former et évaluer des modèles à partir de ces données.
* Enrichissez le [!UICONTROL Profil client en temps réel] avec des informations et des attributs basés sur le modèle pour une personnalisation plus granulaire et des parcours optimisés.
* Former et évaluer des modèles pour déterminer les informations sur les clients telles que la valeur durée de vie client, la propension à se convertir ou à se désabonner, les affinités de produit et de contenu et les scores d’engagement.

## Architecture

<img src="assets/data_science.svg" alt="Architecture de référence pour le plan directeur sur la data science personnalisée pour l’enrichissement de profil" style="border:1px solid #4a4a4a" />

## Étapes d’implémentation

1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) des schémas pour que les données soient assimilées.
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) des jeux de données pour que les données soient assimilées.
1. [Ingérez les données dans Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion).
1. Créez un bloc-notes DSW.
1. Sélectionnez une langue. Python et PySpark sont pris en charge.
1. Créez le modèle dans le modèle dans le bloc-notes.
1. Formez le modèle.
1. Évaluez le modèle pour générer des prédictions avec les données cibles.
1. Activez le jeu de données des résultats du modèle pour le profil si vous poussez les résultats du modèle vers le [!UICONTROL Profil client en temps réel].

## Documentation connexe

* [Description d’Adobe Experience Platform Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentation sur Data Science Workspace](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=fr)
* [Tutoriels sur Data Science Workspace](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html?lang=fr)

## Articles de blog connexes

* [[!DNL Simplifying the Data Science Lifecycle with Adobe Platform Experience]](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL Gaining a Deeper Understanding of Churn Using Data Science Workspace]](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [[!DNL Understanding Data Science In Adobe Experience Platform]](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [[!DNL Reimagining Jupyter Notebooks for Enterprise Scale]](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [[!DNL Accelerate Intelligent Insights with Adobe Experience Platform Data Science Workspace]](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [[!DNL A Preview of Time Series Forecasting with Adobe Experience Platform]](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
