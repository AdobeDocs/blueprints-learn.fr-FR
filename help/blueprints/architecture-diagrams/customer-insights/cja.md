---
title: Customer Journey Analytics avec Real-time Customer Data Platform
description: Unifiez et analysez les données et les comportements des clients sur l’ensemble du parcours client dans Customer Journey Analytics, publiez l’audience de CJA vers RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
TQID: https://experienceleague.adobe.com/gbNXsco0cQIcn5O83ofB-rb0PF65v7kaTZ7mTngqHks
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
feature_v2:
  - id: ce577701-5b9e-4fe4-8fa3-4eedea976da4
    internal-label: Components
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 8%
---

# Adobe Customer Journey Analytics

Adobe Customer Journey Analytics unifie les données d’interaction client de Adobe Experience Platform et d’autres sources dans un service d’analyse basé sur des parcours. Cette architecture fournit la référence principale pour l’analyse cross-canal, les dérivations de CJA B2B et la publication d’audiences CJA dans Real-Time CDP.

## Architecture de Customer Journey Analytics

Ce diagramme présente le flux principal des données d’interaction client dans Customer Journey Analytics pour les connexions, les vues de données, l’analyse et la création d’audiences.

![Architecture principale d’](assets/cja.png){width="1000" zoomable="yes"}

## Dérivations de l’architecture

- Le Customer Journey Analytics B2B étend l’architecture principale avec des dimensions de compte, d’opportunité, de groupe d’achats et de personne pour l’analyse basée sur les comptes.
- Le partage d’audiences CJA publie les audiences créées depuis Customer Journey Analytics dans Real-Time CDP pour l’activation et l’exécution du parcours en aval.

## Flux de données de Principal et points d’intégration

- Les données d’interaction client sont collectées à partir de sources web, mobiles, commerciales, CRM et d’autres sources dans Adobe Experience Platform.
- Les jeux de données Experience Platform sont sélectionnés dans une connexion Customer Journey Analytics.
- Les vues de données présentent des mesures, des dimensions et des champs calculés pour une analyse cross-canal.
- Les audiences Customer Journey Analytics peuvent être publiées dans Real-Time CDP pour activation.
- Customer Journey Analytics insights peut être utilisé avec Journey Optimizer via l’architecture d’intégration dédiée.

## Modèles de cas d’utilisation pris en charge

- [Analyse B2B](/help/blueprints/use-case-patterns/b2b/account-analytics.md) — Analysez les parcours au niveau du compte, de l’opportunité et de la personne avec des dimensions B2B.
- [Customer Analytics et génération insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) — Analysez le comportement cross-canal et générez des informations de parcours.

## Informations complémentaires

- [Présentation de Customer Journey Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Connexions Customer Journey Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/create-connection)
- [Publication d’audiences Customer Journey Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/publish)
