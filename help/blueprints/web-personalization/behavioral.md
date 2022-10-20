---
title: Plan directeur pour la personnalisation comportementale web
description: Découvrez comment personnaliser du contenu en fonction du comportement en ligne et des données d’audience.
landing-page-description: Découvrez comment personnaliser en fonction du comportement en ligne et des données d’audience.
solution: Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7085thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
source-git-commit: 83f1f5e0e508d35d6711710cdb4d367f67e4f715
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plan directeur pour la personnalisation comportementale web ou mobile

Réalise une personnalisation en fonction du comportement en ligne et des données d’audience.

## Cas d’utilisation

* Optimisation de la page de destination
* Ciblage comportemental
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit / contenu, des attributs environnementaux, des données d’audience tierces et des données démographiques

## Applications

* Adobe Target
* Adobe Analytics (facultatif)
* Adobe Audience Manager (facultatif)
* Adobe Real-time Customer Data Platform (facultatif)

## Architecture

<img src="assets/behavioral_personalization.svg" alt="Architecture de référence pour le plan directeur de personnalisation web" style="width:90%; border:1px solid #4a4a4a" />


## Modèles d’implémentation

Le plan directeur de personnalisation web / mobile peut être mis en œuvre par les approches suivantes, comme indiqué ci-dessous.

1. Utilisation du [!UICONTROL SDK web Experience Platform] ou du [!UICONTROL SDK mobile Experience Platform] et de [!UICONTROL Edge Network]. [Reportez-vous au plan directeur du SDK web et mobile d’Experience Platform](../data-ingestion/websdk.md)
1. Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AppMeasurement.js). [Reportez-vous au plan directeur des SDK spécifiques aux applications.](../data-ingestion/appsdk.md)

## Étapes d’implémentation

1. [Implémentation d’Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles.

### Procédure de mise en œuvre - Audience Manager ou Adobe Analytics

1. [Implémentez Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr)
1. [Implémentez Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=fr)
1. [Implémentez le service d’identités Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=fr)

   >[!NOTE]
   >
   >Chaque application doit utiliser l’Experience Cloud ID et faire partie de la même organisation Experience Cloud pour que soit possible le partage d’audience entre les applications.

1. [Demander le provisionnement des services de partage de public et d’audience (audiences partagées)](https://www.adobe.com/go/audiences)
1. Créez des segments dans [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=fr) ou [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html?lang=fr) et [configurez ces audiences pour les partager dans Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)  (si vous utilisez Audience Manager ou Adobe Analytics)
1. Une fois que les audiences sont disponibles dans Adobe Target, elles peuvent être utilisées pour [cibler des expériences avec Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=fr)

### Procédure de mise en œuvre - Real-time Customer Data Platform

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Ingérez des données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) dans Experience Platform.
1. [Réalisez un partage de segments [!UICONTROL Real-time Customer Data Platform]](https://www.adobe.com/go/audiences) entre Experience Platform et Audience Manager pour les audiences définies dans Experience Platform à partager avec Audience Manager.
1. [Créez des segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr) dans Experience Platform. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. [Configurez les destinations](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=fr) pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.


## Documentation connexe

* [Audiences Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=fr)
* [Intégration d’Audience Manager à Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* Présentation de [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* Description de [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)

## Articles de blog connexes

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
