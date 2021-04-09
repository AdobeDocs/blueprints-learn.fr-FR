---
title: Science des données personnalisées pour le schéma directeur des Enrichissements Profils
description: Ce plan indique comment Adobe Experience Platform Data Science Workspace peut utiliser les données dans l’Experience Platform pour former, déployer et marquer des modèles afin de fournir des informations d’apprentissage automatique à partir des données.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: 2343151a1ed5374c299fb9317f6282c232d5d23b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Science des données personnalisées pour le schéma directeur des Enrichissements Profils

Le plan directeur des sciences des données personnalisées pour l&#39;Enrichissement des Profils illustre comment les données du Adobe Experience Platform peuvent être utilisées dans [!UICONTROL Data Science Workspace] pour former, déployer et marquer des modèles afin de fournir des informations d&#39;apprentissage automatique. Ces modèles peuvent directement être générés dans un jeu de données activé pour [!UICONTROL Profil client en temps réel] afin d’enrichir davantage les profils client. Ces informations peuvent ensuite être utilisées pour la personnalisation. Parmi les exemples d’informations d’apprentissage automatique, citons le score de valeur sur la durée de vie, l’affinité des produits et des catégories, la propension à la conversion ou la propension à l’activité.

## Cas d’utilisation

* Extrayez des informations et découvrez des modèles à partir des données client dans l’Experience Platform. Former et marquer des modèles à partir de ces données.
* Enrichissez le [!UICONTROL Profil client en temps réel] avec des informations et des attributs basés sur le modèle pour une personnalisation plus granulaire et des parcours optimisés.
* Formez et évaluez des modèles afin de déterminer les connaissances des clients, telles que la valeur de durée de vie des clients, la propension à convertir ou générer, les affinités de produits et de contenu et les scores d’engagement.

## Architecture

<img src="assets/datascience.svg" alt="Architecture de référence pour la science des données personnalisées pour le plan directeur des Enrichissements Profils" style="border:1px solid #4a4a4a" />

## Etapes de mise en oeuvre

1. Créez des schémas et des jeux de données.
1. Envoi de données dans l’Experience Platform.
1. Créez un bloc-notes DSW.
1. Choisissez une langue. Python et PySpark sont pris en charge.
1. Modèle d&#39;auteur dans un bloc-notes.
1. Entraînez le modèle.
1. Score le modèle pour générer des prédictions avec les données de cible.
1. Activez le jeu de données des résultats du modèle pour le profil si vous poussez les résultats du modèle vers le [!UICONTROL Profil client en temps réel].

## Documentation connexe

* [Description du produit Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Documentation sur ] l’espace de travail Data Science](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [[!UICONTROL Outils ] de données scientifiques](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Publications de blog connexes

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
