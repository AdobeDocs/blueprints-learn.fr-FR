---
title: Plan directeur sur la data science personnalisée pour l’enrichissement de profil
description: Découvrez comment les informations issues de la science des données peuvent être ingérées dans  [!DNL Experience Platform]  pour enrichir le profil client en temps réel.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 63%

---

# Science des données personnalisées pour le plan directeur d’enrichissement des profils

Le plan directeur personnalisé de science des données pour l’enrichissement des profils illustre la manière dont les données peuvent être utilisées pour entraîner, déployer et noter des modèles afin de fournir des informations de machine learning sur les [!DNL Experience Platform] et les [!DNL Real-Time Customer Data Platform] issus de la science des données et des outils de machine learning.

Les informations modélisées peuvent être ingérées dans [!DNL Experience Platform] pour enrichir le profil client en temps réel. Des exemples d’informations de machine learning incluent la valeur de durée de vie, l’affinité au produit et l’affinité catégorielle, la propension à convertir ou à se désabonner.

## Cas d’utilisation

* Extrayez des données et découvrez des modèles à partir de données client, et entrainez et notez des modèles à partir de ces données.
* Enrichir le [!UICONTROL profil client en temps réel] avec des informations et des attributs basés sur le modèle pour une personnalisation plus granulaire et une optimisation des parcours.
* Former et évaluer des modèles pour déterminer les informations sur les clients telles que la valeur durée de vie client, la propension à convertir ou à se désabonner, les affinités de produit et de contenu et les scores d’engagement.

## Architecture

<img src="assets/data_science.svg" alt="Architecture de référence pour le plan directeur sur la data science personnalisée pour l’enrichissement de profil" style="width:90%; border:1px solid #4a4a4a" />

## Garde-fous

* Pour obtenir des mécanismes de sécurisation détaillés et des latences de bout en bout sur l’ingestion de résultats de science des données dans [!DNL Experience Platform] et le profil client en temps réel, reportez-vous aux graphiques de latence et de mécanismes de sécurisation de l’ingestion de données référencés dans le document [&#x200B; Mécanismes de sécurisation de déploiement &#x200B;](../experience-platform/guardrails.md).

## Considérations relatives à la mise en œuvre

* Dans la plupart des cas, le résultat du modèle doit être ingéré dans les attributs de profil et non en tant qu’événements d’expérience. Les résultats du modèle peuvent être une chaîne d’attribut simple. Si plusieurs résultats de modèle doivent être ingérés, il est recommandé d’utiliser un champ de type tableau ou map.
* Les jeux de données des instantané de profils quotidiens, qui correspondent à l’exportation quotidienne des données d’attribut de profil unifié, peuvent être utilisés pour entraîner des modèles sur les données d’attribut de profil. La documentation concernant les jeux de données des instantanés de profils est accessible [ici](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=fr#profile-attribute-datasets).

## Documentation connexe

* [Description du produit Adobe [!DNL Experience Platform] Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr)

## Articles de blog connexes

* [IA pour le commerce et les contenus : personnalisation de vos interactions avec vos clients grâce à l’intelligence de contenu](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Présentation de l’analyse exploratoire des données sur Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Tour d’horizon des produits Adobe Experience avec le machine learning pour une expérience utilisateur améliorée](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI : Automated Audience-Clustering-as-a-Service dans Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)