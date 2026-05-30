---
title: Génération de Customer Analytics et d’Insight
description: Découvrez comment créer des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour l’analyse du comportement et des performances.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 3%

---

# Génération de Customer Analytics et d’insight

Ce guide décrit le modèle de cas d’utilisation de génération de customer analytics et insight, qui connecte [!DNL Adobe Experience Platform] jeux de données à [!DNL Customer Journey Analytics] pour créer des vues de données, des espaces de travail d’analyse de structure libre, des mesures calculées, des tableaux de bord et des cartes de performance mobiles, ainsi que pour publier éventuellement des audiences définies par CJA vers [!DNL Adobe Experience Platform] pour activation.

Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Contrairement aux autres modèles de la taxonomie qui se concentrent sur l’activation et l’engagement (envoi de messages, personnalisation du contenu, activation des audiences), ce modèle se concentre sur la compréhension : l’analyse du comportement des clients, la mesure des performances de la campagne, l’identification des tendances et la génération d’informations qui éclairent les décisions de stratégie et d’optimisation.

## Modèle de cas d’utilisation

**Customer Analytics et génération d’insight**

Créez des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour comprendre le comportement des clients et clientes et les performances des campagnes.

**Plan d’exécution :** Connexion aux données > Configuration des vues de données > Analyse Workspace > Publication sur tableau de bord

## Présentation du cas d’utilisation

Les entreprises doivent comprendre le comportement des clients sur l’ensemble des canaux, les performances des campagnes, l’endroit où les clients chutent dans leurs parcours, le contenu qui résonne et la manière dont les différents segments sont conservés au fil du temps. La génération de Customer Analytics et d’insight répond à ce besoin en connectant les données cross-canal riches en [!DNL Adobe Experience Platform] à [!DNL Customer Journey Analytics], où les analystes peuvent créer des espaces de travail à structure libre, créer des mesures personnalisées, configurer des modèles d’attribution et publier des tableaux de bord à l’intention des parties prenantes.

Ce modèle s’adresse à plusieurs audiences : les analystes marketing qui ont besoin d’une analyse exploratoire approfondie, les responsables de campagne qui ont besoin de tableaux de bord des performances, les chefs de produit qui ont besoin d’informations sur l’engagement et la rétention et les cadres qui ont besoin de cartes de performance d’un coup d’œil. L’approche de mise en œuvre varie en fonction de l’objectif analytique principal : mesure des performances de la campagne, analyse de parcours cross-canal, activation d’audience basée sur une analyse ou informations guidées sur les produits.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**Amélioration des analyses et des rapports**

Améliorez les fonctionnalités de création de rapports pour obtenir des informations marketing plus rapides et plus exploitables grâce à des tableaux de bord unifiés et des outils en libre-service.

- **KPI : Efficacité** productivité

Consultez [Amélioration des analyses et des rapports](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md) pour plus d’informations sur cet objectif commercial.

**Activer la prise de décision pilotée par les données**

Donnez aux équipes les moyens d’utiliser des analyses en libre-service, des informations sur les clients en temps réel et des prédictions basées sur l’IA pour orienter la stratégie.

- **KPI : Efficacité** productivité

Consultez [Activer la prise de décision pilotée par les données](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md) pour plus d’informations sur cet objectif commercial.

**Amélioration de l’attribution marketing**

Mesurez avec précision l’impact des points de contact, des canaux et des campagnes marketing sur les résultats de conversion et de chiffre d’affaires.

- **KPI : Efficacité** revenus incrémentiels

Consultez [Amélioration de l’attribution marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md) pour plus d’informations sur cet objectif commercial.

**Optimiser les dépenses marketing et le retour sur investissement**

Optimisez l’allocation du budget marketing en identifiant les canaux et les campagnes qui offrent le meilleur retour.

- **KPI : Efficacité** revenus incrémentiels

Consultez [ Optimiser les dépenses marketing et le retour sur investissement ](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md) pour plus d’informations sur cet objectif commercial.

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des exemples de cas d’utilisation tactiques pouvant être mis en œuvre avec ce modèle.

- Tableau de bord des performances de la campagne : mesures de diffusion, taux d’engagement, conversion et attribution des recettes dans les campagnes par e-mail, SMS, notification push et médias achetés
- Analyse des abandons du parcours client : identifier où les clients quittent les tunnels d’achat, d’enregistrement ou d’intégration
- Analyse de rétention des cohortes : mesure de la rétention des différentes cohortes d’acquisition sur plusieurs semaines, mois et trimestres
- Modélisation de l’attribution des canaux : comparez l’attribution première touche, dernière touche, linéaire et décroissance temporelle pour comprendre quels canaux génèrent des conversions
- Analyse des performances du contenu : identifiez le contenu qui résonne le plus par segment, canal et étape du cycle de vie
- Analyse de l’utilisation et de l’adoption des produits : suivez l’adoption des fonctionnalités, la fréquence d’engagement et les tendances de croissance des utilisateurs
- Analyse des étapes du cycle de vie des clients : segmentez et analysez les clients par étape du cycle de vie (nouvelle, active, à risque, périmée).
- Tableau de bord d’optimisation du marketing mix - Comparer l’investissement dans les canaux à la contribution au chiffre d’affaires
- Score et reporting d&#39;engagement cross-canal : créez des scores d&#39;engagement composites à partir d&#39;interactions web, d&#39;applications, de courriers électroniques et de campagnes

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Efficacité | Réduction du temps nécessaire à insight et des efforts de création de rapports manuels | Effectuer le suivi du temps passé par les analystes à créer des rapports avant et après l’implémentation de CJA |
| Productivité | Nombre d’analyses en libre-service créées par les utilisateurs professionnels | Surveillance de la création de projets Workspace et de l’utilisation des tableaux de bord |
| Revenu incrémentiel | Chiffre d’affaires attribué aux décisions d’optimisation basées sur les informations | Mesurer l’effet élévateur de revenu des campagnes optimisées en fonction de l’analyse CJA |
| Taux de conversion | Taux d’achèvement de funnel dans les principaux parcours clients | Suivre les taux d’abandons à chaque étape du parcours à l’aide de la visualisation des abandons CJA |
| Engagement | Profondeur et fréquence des interactions des clients sur l’ensemble des canaux | Création de mesures calculées pour le score de l’engagement dans CJA |
| Rétention | Taux de retour client sur des périodes définies | Utilisation de l’analyse des cohortes CJA pour mesurer les courbes de rétention |

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Customer Journey Analytics](CJA)** : connexions, vues de données, analyse de l’espace de travail, analyse guidée, mesures calculées, tableaux de bord, publication d’audiences et analyse de contenu
- **[!DNL Adobe Experience Platform](AEP)** : lac de données, jeux de données, schémas XDM, données de profil et d’événement qui alimentent les connexions CJA

## Documentation connexe

Les ressources suivantes apportent des informations supplémentaires sur ce modèle de cas d’utilisation.

### [!DNL Customer Journey Analytics] — Prise en main

- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Connexions

- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### Vues des données

- [Présentation des vues de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Paramètres de format](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Déduplication des mesures](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Valeurs d’inclusion/exclusion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Paramètres de session](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Champs dérivés](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace et analyse

- [Présentation de Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualisation de flux](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Partager des projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Présentation de l’exportation](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Analyse guidée

- [Aperçu des analyses guidées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue Tendances](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vue de la fréquence d’engagement](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vue de rétention](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Vue de croissance active](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Vue de l’impact de la version](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Première utilisation de la vue d’impact](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Mode Chronologie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Composants

- [Présentation des filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Création de filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Fonctions de mesure calculée](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Présentation des annotations](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Périodes](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Composant Mesures](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Publication d’audiences

- [Présentation des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestion des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### Analyse de contenu

- [Content Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/content-analytics/content-analytics)
- [Configuration de Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Tableaux de bord et cartes de performance

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualisation Synthèse des chiffres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### Principes de base d’AEP

- [Présentation des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Vue d’ensemble des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation d’Audience Portal](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### Intégration de la création de rapports AJO

- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Rapport sur les e-mails de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Parcours du rapport sur les e-mails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutoriels et guides

- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
