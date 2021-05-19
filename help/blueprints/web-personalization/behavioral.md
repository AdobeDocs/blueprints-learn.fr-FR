---
title: Plan directeur pour la personnalisation comportementale web
description: Réalise une personnalisation en fonction du comportement en ligne et des données d’audience.
solution: Experience Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7085thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
translation-type: ht
source-git-commit: 76fe52d8e83e075f9e7ce6e8596880181b01a7fd
workflow-type: ht
source-wordcount: '532'
ht-degree: 100%

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

## Architecture

<img src="assets/behavioral_personalization.svg" alt="Architecture de référence pour le plan directeur de personnalisation web" style="border:1px solid #4a4a4a" />


## Garde-fous

Par défaut, le service de partage de segments permet de partager un maximum de 75 audiences pour chaque suite de rapports Adobe Analytics Si Audience Manager est utilisé pour le partage d’audience, le nombre d’audiences pouvant être partagées n’est pas limité. 

## Modèles d’implémentation

Le plan directeur de personnalisation web / mobile peut être mis en œuvre par les approches suivantes, comme indiqué ci-dessous.

1. Utilisation du [!UICONTROL SDK web Experience Platform] ou du [!UICONTROL SDK mobile Experience Platform] et de [!UICONTROL Edge Network].
1. Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AppMeasurement.js)

### 1. Approche d’utilisation d’Edge et du SDK web ou mobile de Platform

<img src="assets/web_sdk_flow.svg" alt="Architecture de référence pour l’approche [!UICONTROL Platform Web SDK] ou [!UICONTROL Platform Mobile SDK] et [!UICONTROL Edge Network]" style="border:1px solid #4a4a4a" />

### 2. Approche d’utilisation d’un SDK spécifique à l’application

<img src="assets/app_sdk_flow.png" alt="Architecture de référence pour l’approche d’utilisation d’un SDK spécifique à l’application" style="border:1px solid #4a4a4a" />

## Conditions préalables à la mise en œuvre

| Application / service | Bibliothèque requise | Notes |
|---|---|---|
| Adobe Target | [!UICONTROL SDK web Experience Platform]*, at.js 0.9.1+, ou mbox.js 61+ | at.js est recommandé car mbox.js n’est plus en cours de développement. |
| Adobe Audience Manager (facultatif) | [!UICONTROL SDK web Experience Platform]* ou dil.js 5.0+ |  |
| Adobe Analytics (facultatif) | [!UICONTROL SDK web Experience Platform]* ou AppMeasurement.js 1.6.4+ |  |
| Service d’identités Experience Cloud | [!UICONTROL SDK web Experience Platform]* ou VisitorAPI.js 2.0+ |  |
| SDK mobile Experience Platform (facultatif) | 4.11 ou plus récent pour iOS et Android™ |  |
| SDK web Experience Platform | 1.0, la version actuelle du SDK Experience Platform comprend [des cas d’utilisation qui ne sont pas encore pris en charge pour les applications Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |

## Étapes d’implémentation

1. [Implémentation d’Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles.

   Si vous utilisez Audience Manager ou Adobe Analytics :

1. [Implémentez Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr)
1. [Implémentez Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=fr)
1. [Implémentez le service d’identités Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=fr)

   >[!NOTE]
   >
   >Chaque application doit utiliser l’Experience Cloud ID et faire partie de la même organisation Experience Cloud pour que soit possible le partage d’audience entre les applications.

1. [Demander le provisionnement des services de partage de public et d’audience (audiences partagées)](https://www.adobe.com/go/audiences)
1. Créez des segments dans [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=fr) ou [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html?lang=fr) et [configurez ces audiences pour les partager dans Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)  (si vous utilisez Audience Manager ou Adobe Analytics)
1. Une fois que les audiences sont disponibles dans Adobe Target, elles peuvent être utilisées pour [cibler des expériences avec Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=fr)

## Documentation connexe

* [Audiences Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=fr)
* [Intégration d’Audience Manager à Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)


## Articles de blog connexes

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
