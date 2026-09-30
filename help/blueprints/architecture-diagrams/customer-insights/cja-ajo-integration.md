---
title: Intégration d’Adobe Customer Journey Analytics et de Adobe Journey Optimizer
description: Architecture pour l’analyse des campagnes Adobe Journey Optimizer et des informations sur les parcours dans Adobe Customer Journey Analytics, et publication des audiences pour l’exécution des parcours.
solution: Customer Journey Analytics, Journey Optimizer, Experience Platform
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%
---
# Intégration d’Adobe Customer Journey Analytics et de Adobe Journey Optimizer

Cette architecture montre comment les données de diffusion et d’interaction de Adobe Journey Optimizer circulent via Adobe Experience Platform dans Customer Journey Analytics pour obtenir des informations sur les campagnes et les parcours. Les audiences créées dans Customer Journey Analytics peuvent être publiées via Real-Time CDP pour être utilisées dans l’exécution de Journey Optimizer.

## Architecture des informations sur Campaign et parcours

L’architecture connecte les données de diffusion et d’interaction de Journey Optimizer à Experience Platform et Customer Journey Analytics pour la création de rapports, d’analyses et d’audiences.

![Architecture d’intégration d’Adobe Customer Journey Analytics et de Adobe Journey Optimizer](assets/cja_ajo_integration.png){width="1000" zoomable="yes"}

## Flux de données de Principal et points d’intégration

- Les données de diffusion, d’interaction et d’efficacité de Journey Optimizer sont partagées avec les services de données Experience Platform.
- Les données Experience Platform sont ingérées dans Customer Journey Analytics par le biais d’une connexion CJA.
- Les vues et analyses de données Customer Journey Analytics fournissent des insight de campagne et de parcours.
- Les audiences créées dans Customer Journey Analytics sont publiées dans Real-Time CDP.
- Les audiences Real-Time CDP sont disponibles pour l’exécution et la personnalisation du parcours Journey Optimizer.

## Modèles de cas d’utilisation pris en charge

- [Customer Analytics et génération insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) — Analysez le comportement des campagnes et des parcours sur l’ensemble des canaux.
- [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) — Utilisez les signaux du client et du parcours pour prendre en charge la messagerie orchestrée.

## Informations complémentaires

- [Création de rapports Journey Optimizer](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/reports/sharing-overview)
- [Présentation de Customer Journey Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Publication d’audiences Customer Journey Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/publish)
