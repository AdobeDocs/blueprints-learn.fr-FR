---
title: Plan directeur sur la data science personnalisée pour l’enrichissement de profil
description: Découvrez comment ingérer des informations basées sur la science des données dans [!DNL Experience Platform] pour enrichir Real-time Customer Profile.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 69%

---

# Science des données personnalisée pour le plan directeur d’enrichissement des profils

La science des données personnalisée du plan directeur d’enrichissement des profils illustre la manière dont les données peuvent être utilisées pour former, déployer et noter des modèles afin de fournir des insights d’apprentissage automatique dans [!DNL Experience Platform] et la variable [!DNL Real-Time Customer Data Platform] à partir de la science des données et des outils d’apprentissage automatique.

Les insights modélisés peuvent être ingérés dans [!DNL Experience Platform] pour enrichir le profil client en temps réel. Des exemples d’informations de machine learning incluent la valeur de durée de vie, l’affinité au produit et l’affinité catégorielle, la propension à convertir ou à se désabonner.

## Cas d’utilisation

* Extrayez des données et découvrez des modèles à partir de données client, et entrainez et notez des modèles à partir de ces données.
* Enrichir le [!UICONTROL profil client en temps réel] avec des informations et des attributs basés sur le modèle pour une personnalisation plus granulaire et une optimisation des parcours.
* Former et évaluer des modèles pour déterminer les informations sur les clients telles que la valeur durée de vie client, la propension à convertir ou à se désabonner, les affinités de produit et de contenu et les scores d’engagement.

## Architecture

<img src="assets/data_science.svg" alt="Architecture de référence pour le plan directeur sur la data science personnalisée pour l’enrichissement de profil" style="width:90%; border:1px solid #4a4a4a" />

## Garde-fous

* Pour des garde-fous détaillés et des latences de bout en bout sur l’ingestion de résultats de science des données dans [!DNL Experience Platform] et le profil client en temps réel se rapportent aux barrières de sécurité et au diagramme de latence de l’ingestion des données référencés dans la variable [document des protections de déploiement](../experience-platform/deployment/guardrails.md).

## Étapes de mise en œuvre

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=fr) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Ingestion de données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) into [!DNL Experience Platform].

Pour que les résultats de modèle soient ingérés dans le profil client en temps réel, suivez les opérations suivantes avant d’ingérer des données :

1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).

## Considérations relatives à la mise en œuvre

* Dans la plupart des cas, le résultat du modèle doit être ingéré dans les attributs de profil et non en tant qu’événements d’expérience. Les résultats du modèle peuvent être une chaîne d’attribut simple. Si plusieurs résultats de modèle doivent être ingérés, il est recommandé d’utiliser un champ de type tableau ou map.
* Les jeux de données des instantané de profils quotidiens, qui correspondent à l’exportation quotidienne des données d’attribut de profil unifié, peuvent être utilisés pour entraîner des modèles sur les données d’attribut de profil. La documentation concernant les jeux de données des instantanés de profils est accessible [ici](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=fr#profile-attribute-datasets).
* Pour extraire des données de [!DNL Experience Platform] Les méthodes suivantes peuvent être utilisées :
   * Le SDK d’accès aux données
      * Les données se présentent sous la forme d’un fichier brut.
      * Les données d’événement d’expérience de profil restent dans leur état brut non unifié.
   * Destinations RTCDP
      * Seuls les attributs de profil et les appartenances aux segments peuvent être effacés.

## Documentation connexe

* [Adobe [!DNL Experience Platform] Description du produit Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=fr)

## Articles de blog connexes

* [IA pour le commerce et les contenus : personnalisation de vos interactions avec vos clients grâce à l’intelligence de contenu](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Présentation de l’analyse des données exploratoires sur Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Tour d’horizon des produits Adobe Experience avec le machine learning pour une expérience utilisateur améliorée](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI : mise en grappe automatisée d’audience en tant que service dans Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)