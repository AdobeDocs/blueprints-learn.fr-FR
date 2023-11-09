---
title: Experience Platform et garde-fous d’application
description: Les garde-fous définissent les attentes en matière de performances et l’impact pour les composants et services dans Adobe Experience Platform et les applications.
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 4379f372241248ea6c70c766f13a182783fcac0c
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 64%

---

# Garde-fous

Les garde-fous sont des seuils recommandés qui fournissent des conseils pour l’utilisation des données et du système dans Adobe Experience Platform et les applications. Les barrières de sécurité reflètent les contraintes de système et les attentes de performances afin d’optimiser l’architecture des clients et les performances des cas d’utilisation, et permettent d’éviter des erreurs ou des résultats inattendus. Les barrières de sécurité ne sont pas destinées à être des contrats de niveau de service.

Pour plus d’informations sur les contrats de niveau de service spécifiques relatifs aux applications et fonctionnalités, reportez-vous à la section [Descriptions des applications et fonctionnalités](#application-feature-descriptions) au bas de cette page.


## Documentation de référence sur les garde-fous pour Adobe Experience Platform et les applications

Les pages suivantes fournissent des informations sur les barrières de sécurité pour les fonctionnalités, services et applications Adobe Experience Platform :

**Applications Experience Platform**

* [Présentation des barrières de sécurité Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Barrières de sécurité de partage d’audience Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=fr-FR#latency)
* [Protections de l’ingestion des données du Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=fr-FR#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Barrières de sécurité Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=fr)

**Services Experience Platform**

* [Mécanismes de sécurisation de l’ingestion des données](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=fr)
* [Garde-fous de l’API réseau Edge](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=fr)
* [Garde-fous du profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Garde-fous des identités](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=fr)
* [Garde-fous de Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=fr)
* [Garde-fous de l’activation de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=fr)



## Diagrammes de latence de bout en bout

### Ingestion de données

<img src="assets/aep_data_flow_guardrails.svg" alt="Flux de données Experience Platform" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Segmentation

<img src="assets/segmentation_guardrails.svg" alt="Garde-fous de la segmentation d’Experience Platform" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Real-time Customer Data Platform et Adobe Target

<img src="assets/RTCDP_Target_guardrails.svg" alt="Garde-fous RTCDP et Target" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Customer Journey Analytics

<img src="assets/CJA_guardrails.svg" alt="Garde-fous CJA" style="border:1px solid #4a4a4a" width="85%" />

<br>

### Journey Optimizer

<img src="assets/AJO_guardrails.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:85%; border:1px solid #4a4a4a" />

<br>

## Descriptions des applications et fonctionnalités {#application-feature-descriptions}

Pour plus d’informations sur les contrats de niveau de service spécifiques à une fonctionnalité, reportez-vous aux descriptions de produit ci-dessous :

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Plateforme de données clients B2B](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform Activation](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform Intelligence](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligent Services](https://helpx.adobe.com/fr/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/fr/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/fr/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Journey Orchestration](https://helpx.adobe.com/fr/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html)
