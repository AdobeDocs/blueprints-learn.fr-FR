---
title: Analyses B2B
description: Découvrez comment inclure des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 2%

---

# Analyses B2B

Ce guide décrit le modèle de cas d’utilisation d’Analytics B2B, qui utilise [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition et [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition pour incorporer des informations au niveau du compte B2B dans l’analyse de parcours client cross-canal. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

B2B Analytics étend les fonctionnalités [!DNL CJA] standard avec des connexions basées sur les comptes, des conteneurs spécifiques au B2B (compte, compte global, opportunité, groupe d’achat) et des rapports au niveau du compte. Cette fonctionnalité permet aux entreprises d’analyser l’engagement marketing et commercial au niveau du compte, de suivre la progression des opportunités, de mesurer l’exhaustivité du groupe d’achats et d’attribuer le chiffre d’affaires aux points de contact marketing sur l’ensemble des cycles de vente B2B étendus.

## Modèle de cas d’utilisation

**Analyse B2B**

Incluez des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal.

**Plan d’exécution :** Connexion de données B2B > Configuration de la vue de données du compte > Analyse Workspace > Publication sur tableau de bord

## Présentation du cas d’utilisation

Les organisations B2B sont confrontées à un défi analytique fondamental : leurs clients ne sont pas des personnes individuelles, mais des comptes composés de plusieurs parties prenantes, de groupes d’achat et d’opportunités. L’analyse standard basée sur la personne ne peut pas répondre à des questions du type « Quels comptes sont les plus engagés ? », « Dans quelle mesure nos groupes d’achats sont-ils complets ? » ou « Quels points de contact marketing génèrent la progression des opportunités ? »

L’analyse B2B résout ce problème en exploitant [!DNL CJA] B2B edition pour créer des vues analytiques centrées sur les comptes qui combinent des données comportementales au niveau de la personne avec des dimensions de compte, d’opportunité et de groupe d’achat. [!DNL RT-CDP] B2B edition fournit l’unification des profils de compte sous-jacente et la résolution d’identité B2B qui alimente la couche Analytics. Ensemble, ces solutions permettent aux entreprises de créer une analyse de parcours cross-canal au niveau du compte, de corréler l’engagement marketing à la progression du pipeline et de fournir des informations exploitables aux équipes marketing et commerciales.

L’audience cible comprend les équipes opérationnelles marketing B2B, les responsables de la génération de la demande, les analystes des opérations de chiffre d’affaires et le leadership commercial qui ont besoin de visibilité sur l’engagement au niveau du compte et l’intégrité des pipelines.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Amélioration des analyses et des rapports

Améliorez les fonctionnalités de création de rapports pour obtenir des informations marketing plus rapides et plus exploitables grâce à des tableaux de bord unifiés et des outils en libre-service. L’analyse B2B permet aux entreprises de consolider des données d’engagement au niveau du compte provenant de plusieurs sources dans un seul environnement analytique, offrant ainsi une visibilité cross-canal sur la manière dont les programmes marketing influencent le pipeline et le chiffre d’affaires.

**KPI : Efficacité** productivité

[En savoir plus sur l’amélioration des analyses et des rapports](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Activer la prise de décision pilotée par les données

Donnez aux équipes les moyens d’utiliser des analyses en libre-service, des informations sur les clients en temps réel et des prédictions basées sur l’IA pour orienter la stratégie. L’analyse au niveau des comptes dote les équipes marketing et commerciales des données nécessaires pour hiérarchiser les comptes, optimiser les stratégies d’engagement et s’aligner sur les opportunités de pipeline.

**KPI : Efficacité** productivité

[En savoir plus sur comment activer la prise de décision pilotée par les données](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé. CJA B2B edition offre des intervalles de recherche en amont de 13 mois étendus, spécialement conçus pour les cycles de vente B2B, ce qui permet une attribution multipoint précise sur l’ensemble du parcours des comptes.

**KPI : Efficacité** revenus incrémentiels

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Analyse de notation de l’engagement du compte** — Mesurez et classez les comptes par leur engagement agrégé sur le web, les e-mails, les événements et les interactions de contenu afin d’identifier les comptes à forte intention pour le suivi des ventes
- **Suivi de l&#39;exhaustivité du groupe d&#39;achats** — Analysez la composition du groupe d&#39;achats sur les comptes pour identifier les lacunes dans la couverture des rôles et hiérarchisez l&#39;acquisition de leads pour les groupes d&#39;achats incomplets
- **Corrélation des pipelines d’opportunités** — Corrélez les données d’engagement marketing avec la progression de la phase d’opportunité pour comprendre quelles campagnes et quels points de contact génèrent l’avancement du pipeline
- **Attribution B2B multipoint** : appliquez des modèles d’attribution avec des intervalles de recherche en amont de 13 mois pour créditer les points de contact marketing sur l’ensemble du parcours d’achat B2B, du premier contact à l’expérience confirmée
- **Mappage du parcours de compte** — Visualisez le parcours de compte cross-canal depuis la connaissance initiale jusqu’à la création et la fermeture de l’opportunité, en identifiant les chemins communs et les points de friction
- **L’influence de la campagne sur le pipeline** — Mesurez la manière dont des campagnes spécifiques influencent la création du pipeline de compte, l’avancement des opportunités et la génération de revenus
- **Progression de l’engagement du groupe d’achat** - Suivez l’évolution des scores d’engagement du groupe d’achat au fil du temps et corrélez les seuils d’engagement avec les résultats des opportunités
- **Performances du contenu basé sur les comptes** — Analysez quelles ressources et rubriques de contenu correspondent à des segments de compte, des secteurs d’activité ou des rôles de groupe d’achat spécifiques
- **Tableaux de bord d’alignement des ventes et du marketing** — Créez des tableaux de bord partagés qui offrent aux équipes marketing et commerciales une vue unifiée de l’engagement du compte, de l’intégrité du pipeline et de l’attribution des recettes
- **Segmentation de compte pour l’activation** — Créez des segments B2B basés sur l’analyse au niveau du compte (par exemple, « comptes à fort engagement sans opportunités ouvertes ») et publiez-les pour l’activation en aval

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Account Engagement Score | Mesure d’engagement agrégée pour tous les contacts d’un compte | Mesure calculée combinant les visites web, les interactions par e-mail, la participation à des événements et les téléchargements de contenu au niveau du compte |
| Exhaustivité du groupe d&#39;achat | Pourcentage de rôles requis remplis dans un groupe d&#39;achats | Ratio des rôles renseignés par rapport au total des rôles requis par groupe d&#39;achat, suivi au fil du temps |
| Pipeline influencé par le marketing | Chiffre d’affaires de pipeline ayant été touché par des activités marketing | Valeur de l’opportunité où les contacts de compte associés ont des points de contact marketing dans la fenêtre d’attribution |
| Taux de conversion compte à opportunité | Pourcentage de comptes engagés qui génèrent des opportunités qualifiées | Comptes avec opportunités divisés par le total des comptes engagés sur une période définie |
| Durée moyenne du cycle de l’affaire | Temps écoulé entre la première touche marketing et la conclusion de l’appel | Durée moyenne du premier point de contact attribué à la date de fermeture de l’opportunité |
| Chiffre d’affaires de l’attribution marketing | Chiffre d’affaires attribué aux points de contact marketing | Chiffre d’affaires d’opportunités closes avec des contacts marketing, distribué par modèle d’attribution |
| Portée et pénétration du compte | Nombre de contacts engagés par compte cible | Contacts uniques avec interactions marketing par compte, par rapport au nombre total de contacts connus |
| Engagement du contenu par rôle d’achat | Mesures d’engagement segmentées par rôle de groupe d’achat | Pages vues, téléchargements et temps passé ventilé par persona/rôle dans les groupes d’achats |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Customer Journey Analytics]B2B edition** — Fournit des connexions basées sur les comptes, des conteneurs de vues de données spécifiques au B2B, une analyse de l’espace de travail au niveau du compte, une analyse des groupes d’achats, une analyse des opportunités, une segmentation B2B et une attribution B2B avec des intervalles de recherche en amont étendus
- **[!DNL Real-Time CDP]B2B edition** — Fournit la base de données B2B, y compris l’unification des profils de compte, la résolution des identités B2B, les classes de schéma B2B (compte, opportunité, groupe d’achat) et l’intégration [!DNL Marketo Engage] pour l’ingestion de données d’engagement B2B

## Documentation connexe

Les ressources suivantes apportent des informations supplémentaires sur l’implémentation de ce modèle de cas d’utilisation.

**[!DNL CJA]B2B edition**

- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

**Connexions**

- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

**Vues de données**

- [Présentation des vues de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Paramètres de format](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Champs dérivés](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Paramètres de session](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace et analyse**

- [Présentation de Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualisation de flux](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Partager des projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Composants**

- [Présentation des filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Création de filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Présentation des annotations](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Périodes](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Audiences**

- [Présentation des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestion des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

**Tableaux de bord et cartes de performance**

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Analyse guidée**

- [Aperçu des analyses guidées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue Tendances](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vue de rétention](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [Présentation de RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [Schémas B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Présentation des sources B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/sources/b2b)

**AEP data foundation**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Vue d’ensemble des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

**Gouvernance et cycle de vie des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Tutoriels et guides**

- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
