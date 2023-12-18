---
title: Experience Platform et garde-fous d’application
description: Les garde-fous définissent les attentes en matière de performances et l’impact pour les composants et services dans Adobe Experience Platform et les applications.
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 5a4827244b7d8414b1f1a0bf9b3cd8308bde8c60
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 18%

---

# Garde-fous

Les garde-fous sont des seuils recommandés qui fournissent des conseils pour les données, les latences observées et l’utilisation du système dans Adobe Experience Platform et les applications. Les barrières de sécurité reflètent les contraintes de système et les attentes de performances afin d’optimiser l’architecture des clients et les performances des cas d’utilisation, et permettent d’éviter des erreurs ou des résultats inattendus. Les barrières de sécurité ne sont pas destinées à être des contrats de niveau de service, les contrats de niveau de service sont documentés dans les Descriptions de produits ci-dessous et dans les contrats de licence client. Les garde-fous sont destinés à fournir des conseils pour la conception de solutions pour des cas d’utilisation spécifiques des clients afin d’assurer la stabilité et l’exécution.

Pour plus d’informations sur les contrats de niveau de service spécifiques relatifs aux applications et fonctionnalités, reportez-vous à la section [Descriptions des applications et fonctionnalités](#application-feature-descriptions) au bas de cette page.

Notez que pour tout cas d’utilisation client ayant des exigences strictes en termes de latence ou de volume, Adobe recommande d’examiner votre cas d’utilisation en détail avec votre équipe de compte d’Adobe et votre partenaire d’implémentation. Dans certains cas, il est conseillé de tester et d’observer une mise en oeuvre d’un cas d’utilisation spécifique avant le lancement en production du cas d’utilisation afin d’observer et de comprendre le comportement attendu, car chaque mise en oeuvre client comporte différents facteurs en jeu, notamment la nature et la cadence de l’ingestion des données, les spécificités des règles de segment en cours de création et les différents défis et payloads d’activation. Chaque mise en oeuvre de cas d’utilisation aura des performances observées variables. Il est donc préférable d’établir et de tester les performances attendues à l’avance afin d’assurer une architecture et une mise en oeuvre appropriées en fonction des besoins de latence et de performance du cas d’utilisation.


## Documentation de référence sur les garde-fous pour Adobe Experience Platform et les applications

Les pages suivantes fournissent des informations sur les barrières de sécurité pour les fonctionnalités, services et applications Adobe Experience Platform :

**Applications Experience Platform**

* [Présentation des barrières de sécurité Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Barrières de sécurité de partage d’audience Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Protections de l’ingestion des données du Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Barrières de sécurité Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Services Experience Platform**

* [Mécanismes de sécurisation de l’ingestion des données](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [Garde-fous de l’API réseau Edge](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Barrières de sécurité de la segmentation et du profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Garde-fous des identités](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=fr)
* [Garde-fous de Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=fr)
* [Garde-fous de l’activation de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=fr)

## Diagrammes de latence de bout en bout {#end-to-end-latency}

### Ingestion de données {#data-ingestion}

Le diagramme ci-dessous affiche les valeurs de latence d’ingestion de données attendues via [ingestion par flux](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) et [ingestion par lots](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=fr) lors de l’importation de données dans Real-Time CDP. Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau de l’ingestion de données.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Présentation visuelle de haut niveau de l’ingestion de données et valeurs de latence"){width="1000" zoomable="yes"}

### Segmentation {#segmentation}

Le diagramme ci-dessous affiche les valeurs de latence attendues lors de l’utilisation d’audiences dans [Service de segmentation Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr). Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau de la segmentation.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Présentation visuelle de haut niveau de la segmentation et valeurs de latence"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform et Adobe Target {#adobe-target-latency}

Le diagramme ci-dessous affiche les valeurs de latence attendues lors de l’exportation d’audiences de Real-Time CDP vers [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr). Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau de l’exportation vers Adobe Target.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Target_guardrails.svg "Exportation d’audiences vers un aperçu visuel de haut niveau d’Adobe Target et des valeurs de latence"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

Le diagramme ci-dessous affiche les valeurs de latence attendues lorsque vous utilisez [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Cliquez sur l’image pour afficher une version haute résolution.

![Utilisation d’un aperçu visuel de haut niveau de Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Utilisation des valeurs de latence et d’aperçu visuel de haut niveau de Customer Journey Analytics"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

Le diagramme ci-dessous affiche les valeurs de latence attendues lorsque vous utilisez [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Cliquez sur l’image pour afficher une version haute résolution.

![Utilisation d’un aperçu visuel de haut niveau de Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Utilisation des valeurs de latence et d’aperçu visuel de haut niveau de Adobe Journey Optimizer"){width="1000" zoomable="yes"}

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
