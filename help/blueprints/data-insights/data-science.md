---
title: Plan directeur sur la data science personnalisée pour l’enrichissement de profil
description: Ce plan directeur montre comment ingérer des insights basés sur la science des données dans Experience Platform pour enrichir Real-time Customer Profile.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 6d44401fba8cc75402d4303825e32e7948753449
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plan directeur sur la data science personnalisée pour l’enrichissement de profil

Science des données personnalisées pour le plan directeur d’enrichissement des profils illustre la manière dont les données peuvent être utilisées pour former, déployer et noter des modèles afin de fournir des insights d’apprentissage automatique à Experience Platform et Real-time Customer Data Platform à partir de la science des données et des outils d’apprentissage automatique. Les données modélisées peuvent être ingérées dans Experience Platform pour enrichir un profil client en temps réel. Des exemples d’informations de machine learning incluent la valeur de durée de vie, l’affinité au produit et l’affinité catégorielle, la propension à convertir ou à se désabonner.

## Cas d’utilisation

* Extrayez des données et découvrez des modèles à partir de données client, et entrainez et notez des modèles à partir de ces données.
* Enrichir le [!UICONTROL profil client en temps réel] avec des informations et des attributs basés sur le modèle pour une personnalisation plus granulaire et une optimisation des parcours.
* Former et évaluer des modèles pour déterminer les informations sur les clients telles que la valeur durée de vie client, la propension à convertir ou à se désabonner, les affinités de produit et de contenu et les scores d’engagement.

## Architecture

<img src="assets/data_science.svg" alt="Architecture de référence pour le plan directeur sur la data science personnalisée pour l’enrichissement de profil" style="width:90%; border:1px solid #4a4a4a" />

## Étapes d’implémentation

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Ingérez des données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) dans Experience Platform.

Pour que les résultats de modèle soient ingérés dans le profil client en temps réel, suivez les opérations suivantes avant d’ingérer des données :

1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).

## Considérations de mise en œuvre

* Dans la plupart des cas, le résultat du modèle doit être ingéré dans les attributs de profil et non en tant qu’événements d’expérience. Les résultats du modèle peuvent être des chaînes d’attribut simples. Si plusieurs résultats de modèle doivent être ingérés, il est recommandé d’utiliser un champ de type tableau ou map.
* Les jeux de données des instantané de profils quotidiens, qui correspondent à l’exportation quotidienne des données d’attribut de profil unifié, peuvent être utilisés pour entraîner des modèles sur les données d’attribut de profil. La documentation concernant les jeux de données des instantanés de profils est accessible [ici](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=fr#profile-attribute-datasets).
* Pour extraire des données d’Experience Platform, les méthodes suivantes peuvent être utilisées :
   * Le SDK d’accès aux données
      * Les données se présentent sous la forme d’un fichier brut.
      * Les données d’événement d’expérience de profil restent dans leur état brut non unifié.
   * Destinations RTCDP
      * Les attributs de profil et les appartenances aux segments peuvent être effacés.

## Documentation connexe

* [Description d’Adobe Experience Platform Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Service de requête Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr)

## Articles de blog connexes

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)