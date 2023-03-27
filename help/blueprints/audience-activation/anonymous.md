---
title: Plan directeur d’activation d’audience anonyme
description: Apprenez à cibler des audiences sur le web et les canaux publicitaires en fonction de données client anonymes et comportementales. Cette capacité permet des expériences client en temps réel personnalisées et cohérentes sur tous les appareils.
landing-page-description: Apprenez à cibler des audiences sur le web et les canaux publicitaires en fonction de données client anonymes et comportementales.
short-description: Learn to target audiences across web and advertising channels based on anonymous and behavioral customer data.
solution: Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 3a6a98eded28baee2cbb44de2262bbd580fa0c94
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Plan directeur d’activation d’audience anonyme

L’activation de l’audience anonyme permet de cibler et de personnaliser des audiences sur des canaux web, mobiles et publicitaires basés sur un appareil et des données comportementales anonymes.

## Cas d’utilisation

* Effectuez un ciblage et une personnalisation anonymes de l’audience numérique sur un site web, une application mobile ou sur les canaux publicitaires pris en charge.
* Optimisez les expériences de page de destination et de pré-authentification en fonction des caractéristiques connues de l’appareil et du comportement.
* Tirez parti du réseau de données tiers d’Audience Manager pour affiner et développer davantage vos audiences en vue du ciblage.


## Applications

* Audience Manager
* Real-time Customer Data Platform

Audience Manager et Real-time Customer Data Platform peuvent être utilisés pour alimenter l’activation d’audience anonyme pour les destinations sur site et publicitaires. Notez que Real-time Customer Data Platform ne prend en charge qu’un sous-ensemble de destinations publicitaires avec des identifiants d’appareil anonymes, tels que listés dans la [documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=fr).

Microsoft Bing, Google DV360 et TradeDesk sont les principales destinations publicitaires prises en charge par Real-time Customer Data Platform pour le ciblage anonyme basé sur les appareils. Par ailleurs, Real-time Customer Data Platform prend en charge de nombreuses destinations basées sur les clients connus, telles qu’elles sont cataloguées dans la [documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=fr) et comme décrit dans la section [Plan directeur d’activation du client connu](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=fr).

## Architecture

<img src="assets/anonymous_activation.svg" alt="Architecture de référence pour le plan directeur d’activation d’audience anonyme" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

<br>

## Procédure de mise en œuvre d’Audience Manager

* Pour plus d’informations sur la mise en œuvre d’Audience Manager, consultez la [documentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr) suivante.

## Procédure de mise en œuvre de Real-time Customer Data Platform

* Pour connaître les étapes de mise en œuvre de Real-time Customer Data Platform, consultez la [documentation](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=fr) suivante.

## Documentation connexe

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=fr)
* [[!UICONTROL Audiences] Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=fr)
* [Intégration d’Audience Manager à Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Plan directeur d’activation du client connu](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=fr).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=fr)
