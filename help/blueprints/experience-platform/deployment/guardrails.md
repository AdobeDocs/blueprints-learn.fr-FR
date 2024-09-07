---
title: Experience Platform et garde-fous d’application
description: Les garde-fous définissent les attentes en matière de performances et l’impact pour les composants et services dans Adobe Experience Platform et les applications.
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 7e37677280c27302e650a96786035169573d9709
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 10%

---


# Garde-fous

Les barrières de sécurité reflètent les contraintes du système, les latences attendues et les attentes de performances afin d’optimiser l’architecture des clients et les performances des cas d’utilisation et d’assurer la stabilité, d’éviter les erreurs ou les résultats inattendus.

## Types de garde-fous

| Type de protection | Description |
|---|---|
| Barrière de sécurité des performances (limite de soft) | Les barrières de performance sont des limites d’utilisation qui se rapportent à la portée de vos cas d’utilisation et mettent en avant les performances attendues dans des conditions normales. En cas de dépassement, vous pouvez subir une dégradation des performances et une latence. Les protections de performances sont documentées dans les documents Experience League sous les sections de barrières de sécurité pour chaque solution, comme indiqué ci-dessous. |
| Limite statique (limite stricte) | Il s’agit de limites appliquées par le système qui ne peuvent pas être dépassées. Les limites statiques sont généralement liées par contrat et décrites dans le contrat client et les [Descriptions des produits](https://helpx.adobe.com/legal/product-descriptions.html). |

>[!NOTE]
>
> Les barrières de sécurité ne sont pas destinées à être des accords de niveau de service, mais plutôt des conseils pour des configurations optimales et le comportement attendu du système. Toute barrière de sécurité qui est une limite du système ou contractuelle ou un accord de niveau de service sera documentée spécifiquement dans les contrats clients et les descriptions de produits. Si vous souhaitez en savoir plus sur les limites personnalisées, contactez votre représentant de l’assistance clientèle.

>[!NOTE]
>
> Pour les cas d’utilisation présentant des besoins stricts en termes de latence ou de performances, Adobe vous suggère de discuter des détails avec votre équipe de compte d’Adobe et votre partenaire d’implémentation. Chaque configuration de client peut varier selon les schémas d’ingestion de données, les règles de segment et les canaux d’activation. Il est important de tester et de passer en revue votre cas d’utilisation avant de le lancer afin de comprendre comment il se comporte.

## Documentation de référence sur les garde-fous pour Adobe Experience Platform et les applications

Les pages suivantes fournissent des informations sur les barrières de sécurité pour les fonctionnalités, services et applications Adobe Experience Platform :

**Applications Experience Platform**

* [Présentation des barrières de sécurité Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Barrières de sécurité de partage d’audience Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Barrières de sécurité de l’ingestion des données du Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Barrières de sécurité Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Services Experience Platform**

* [Mécanismes de sécurisation de l’ingestion des données](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] Barrières de sécurité de l’API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [ Barrières de sécurité du profil client et de la segmentation en temps réel ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Garde-fous des identités](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=fr)
* [Garde-fous de Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=fr)
* [Garde-fous de l’activation de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=fr)

## Diagrammes de latence de bout en bout {#end-to-end-latency}

### Latences observées des Edge Network Experience Platform et des Principal Hub {#edge-hub-latencies}

Le diagramme suivant illustre les latences observées au niveau de la périphérie principale et du hub lors de l’architecture du cas d’utilisation sur l’Experience Platform et les applications.

![Experience Platform [!DNL Edge Network] et hub Principales latences observées.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Edge Network Experience Platform et hub Principales latences observées"){width="1000" zoomable="yes"}

### Ingestion de données {#data-ingestion}

Le diagramme ci-dessous affiche les valeurs de latence d’ingestion de données attendues par [ingestion par flux](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) et [ingestion par lots](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=fr) lors de l’importation de données dans Real-Time CDP. Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau de l’ingestion de données.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Présentation visuelle de haut niveau de l’ingestion de données et valeurs de latence"){width="1000" zoomable="yes"}

### Segmentation {#segmentation}

Le diagramme ci-dessous affiche les valeurs de latence attendues lors de l’utilisation d’audiences dans le [service de segmentation Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr). Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau de segmentation.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Présentation visuelle de haut niveau de segmentation et valeurs de latence"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform &amp; [!DNL Edge Network] {#adobe-edge-latency}

Le diagramme ci-dessous affiche les valeurs de latence attendues lors de l’utilisation de [!DNL Edge Network], par exemple pour exploiter les audiences RTCDP dans [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr). Cliquez sur l’image pour afficher une version haute résolution.

![Présentation visuelle de haut niveau d’Adobe Edge Network et d’Experience Platform.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exportation d’audiences vers un aperçu visuel de haut niveau d’Adobe Target et latence"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

Le diagramme ci-dessous affiche les valeurs de latence attendues lorsque vous utilisez [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Cliquez sur l’image pour afficher une version haute résolution.

![Utilisation d’un aperçu visuel de haut niveau de Customer Journey Analytics.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Utilisation de valeurs de latence et d’aperçu visuel de haut niveau de Customer Journey Analytics"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

Le diagramme ci-dessous affiche les valeurs de latence attendues lorsque vous utilisez [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Cliquez sur l’image pour afficher une version haute résolution.

![Utilisation d’un aperçu visuel de haut niveau de Adobe Journey Optimizer.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Utilisation de la présentation visuelle de haut niveau de Adobe Journey Optimizer et des valeurs de latence"){width="1000" zoomable="yes"}