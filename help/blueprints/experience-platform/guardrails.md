---
title: Experience Platform et garde-fous d’application
description: Les garde-fous définissent les attentes en matière de performances et l’impact pour les composants et services dans Adobe Experience Platform et les applications.
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 13%

---


# Garde-fous

Les mécanismes de sécurisation reflètent les contraintes système, les latences attendues et les attentes en matière de performances afin d’optimiser l’architecture client et les performances du cas d’utilisation. Ils permettent également d’assurer la stabilité, d’éviter les erreurs ou les résultats inattendus.

## Types de mécanismes de sécurisation

| Type de mécanisme de sécurisation | Description |
|---|---|
| Mécanisme de sécurisation des performances (limite soft) | Les mécanismes de sécurisation de performances sont des limites d’utilisation liées à la portée de vos cas d’utilisation et décrivent les performances attendues dans des conditions normales. Une fois dépassées, les performances peuvent se dégrader et une latence peut survenir. Les mécanismes de sécurisation de performances sont documentés dans les documents Experience League sous les sections de mécanisme de sécurisation pour chaque solution, comme indiqué ci-dessous. |
| Limite statique (limite Hard) | Il s’agit de limites appliquées par le système qui ne peuvent pas être dépassées. Les limites statiques sont généralement liées et décrites contractuellement dans le contrat client et la [Description du produit](https://helpx.adobe.com/legal/product-descriptions.html). |

>[!NOTE]
>
> Les mécanismes de sécurisation ne sont pas destinés à être des accords de niveau de service, mais plutôt des conseils pour des configurations optimales et un comportement système attendu. Tous les mécanismes de sécurisation qui sont des limites système ou contractuelles ou des accords de niveau de service seront documentés spécifiquement dans les contrats clients et les descriptions des produits. Si vous souhaitez en savoir plus sur les limites personnalisées, contactez votre représentant de l’assistance clientèle.

>[!NOTE]
>
> Pour les cas d’utilisation présentant des besoins stricts en termes de latence ou de performances, Adobe suggère de discuter des détails avec l’équipe de votre compte Adobe et le partenaire d’implémentation. Chaque configuration client peut varier entre les modèles d’ingestion de données, le nombre et la richesse de profils, les règles de segment et les canaux d’activation. Il est donc important d’architecturer et de tester votre cas d’utilisation pour optimiser ses performances et comprendre pleinement les caractéristiques de performances attendues.

## Documentation de référence sur les garde-fous pour Adobe Experience Platform et les applications

Les pages suivantes fournissent des informations sur les mécanismes de sécurisation pour les fonctionnalités, services et applications Adobe Experience Platform :

**Applications Experience Platform**

* [Présentation des mécanismes de sécurisation de Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Mécanismes de sécurisation du partage d’audience Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Mécanismes de sécurisation de l’ingestion des données de Customer Journey Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Services Experience Platform**

* [Mécanismes de sécurisation de l’ingestion des données](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network]  Mécanismes de sécurisation des API ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Mécanismes de sécurisation du profil client et de la segmentation en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Garde-fous des identités](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=fr)
* [Garde-fous de Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=fr)
* [Garde-fous de l’activation de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=fr)

## Diagrammes de latence de bout en bout {#end-to-end-latency}

### Latences observées dans Experience Platform Edge Network et le Principal Hub {#edge-hub-latencies}

Le diagramme suivant illustre les latences principales observées sur les serveurs Edge et le hub à prendre en compte lors de l’architecture du cas d’utilisation sur Experience Platform et les applications.

![Latences observées principales des [!DNL Edge Network] Experience Platform et du hub.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Latences principales observées pour Experience Platform Edge Network et le hub"){width="1000" zoomable="yes"}