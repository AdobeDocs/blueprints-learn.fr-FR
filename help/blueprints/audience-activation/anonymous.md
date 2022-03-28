---
title: Plan directeur pour l’activation d’audience anonyme
description: Apprenez à cibler des audiences sur le web et les canaux publicitaires en fonction de données client anonymes et comportementales. Cette capacité permet des expériences client en temps réel personnalisées et cohérentes sur tous les appareils.
landing-page-description: Apprenez à cibler des audiences sur le web et les canaux publicitaires en fonction de données client anonymes et comportementales.
solution: Experience Platform, Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 4a46b7a4c278107c806d3ddd14591c7abe1a13d3
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 34%

---

# Plan directeur pour l’activation d’audience anonyme

L’activation de l’audience anonyme est la possibilité de cibler et de personnaliser des audiences sur des canaux web, mobiles et publicitaires basés sur un appareil anonyme et des données comportementales.

## Cas d’utilisation

* Effectuez un ciblage et une personnalisation anonymes d’audience numérique sur le site web, l’application mobile ou sur les canaux publicitaires pris en charge.
* Optimisez les expériences de page d’entrée et de pré-authentification en fonction des caractéristiques connues de l’appareil et du comportement.
* Tirez parti du réseau de données tiers d’Audience Manager pour affiner et développer davantage vos audiences en vue du ciblage.


## Applications

* Audience Manager
* Real-time Customer Data Platform

Audience Manager et Real-time Customer Data Platform peuvent être utilisés pour alimenter l’Audience Activation anonyme pour les destinations sur site et publicitaires. Notez que Real-time Customer Data Platform ne prend en charge qu’un sous-ensemble de destinations publicitaires avec des identifiants d’appareil anonymes, tels que catalogués dans la variable [documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing, Google DV360 et TradeDesk sont les Principales destinations publicitaires Real-time Customer Data Platform prises en charge pour le ciblage anonyme basé sur les appareils. Par ailleurs, Real-time Customer Data Platform prend en charge de nombreuses destinations basées sur les clients connues, telles qu’elles sont cataloguées dans le [documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) et comme décrit dans la section [plan directeur d’activation du client connu](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Architecture

<img src="assets/anonymous_activation.svg" alt="Architecture de référence pour le plan directeur d’activation d’audience anonyme" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Procédure de mise en oeuvre de l’Audience Manager

* Pour plus d’informations sur la mise en oeuvre de l’Audience Manager, voir : [documentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr).

## Procédure de mise en oeuvre de Real-time Customer Data Platform

* Pour connaître les étapes de mise en oeuvre de Real-time Customer Data Platform, voir : [documentation](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Documentation connexe

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=fr)
* [[!UICONTROL Audiences] Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=fr)
* [Intégration d’Audience Manager à Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Plan directeur d’activation du client connu](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
