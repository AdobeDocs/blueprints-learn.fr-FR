---
title: Recommandation comportementale
description: Découvrez comment générer des recommandations d’éléments et de contenu à l’aide de stratégies de sélection et de modèles de classement.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 5%

---

# Recommandation comportementale

Ce guide décrit le modèle de cas d’utilisation de recommandation comportementale, qui utilise [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP) pour fournir des expériences de recommandation personnalisées sur les canaux web, des applications mobiles et des e-mails. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

La recommandation comportementale génère des recommandations au niveau de l’élément ou du contenu à l’aide de signaux comportementaux (consultations de produits, achats, interactions de contenu, requêtes de recherche) associés à des stratégies de sélection et à des modèles de classement AJO Decisioning. Contrairement à Offer Decisioning , qui régit un ensemble limité d’offres, de promotions ou d’incitations à l’aide de règles d’éligibilité et de contraintes commerciales, ce modèle fonctionne sur de grands catalogues d’articles en constante évolution (produits, articles, vidéos) où la sélection est pilotée par des signaux d’affinité comportementale plutôt que par l’éligibilité régie.

## Modèle de cas d’utilisation

**Recommandation comportementale**

Générez des recommandations au niveau de l’élément ou du contenu en fonction de signaux comportementaux, à l’aide de stratégies de sélection et de modèles de classement AJO Decisioning pour diffuser du contenu contextuel.

**Plan d’exécution :** Ingestion des signaux comportementaux > Évaluation de la stratégie de prise de décision > Diffusion des recommandations > Rapports

## Présentation du cas d’utilisation

Les entreprises qui disposent de catalogues de produits, de bibliothèques de contenu ou de bibliothèques de médias doivent afficher les éléments les plus pertinents pour chaque visiteur en fonction de son historique comportemental et de son activité au cours de la session. Qu’il s’agisse d’un carrousel « recommandé pour vous » sur une page d’accueil, d’un widget de vente croisée sur une page de détails du produit ou de recommandations de produits intégrées dans une campagne par e-mail, le défi sous-jacent est le même : faites correspondre le profil comportemental de chaque visiteur aux éléments les plus pertinents d’un catalogue, puis diffusez ces recommandations sur le bon canal au bon moment.

Ce modèle résout ce problème en ingérant des signaux comportementaux en temps réel via [!DNL Web SDK] ou [!DNL Mobile SDK], en les traitant au moyen de stratégies de sélection AJO Decisioning qui combinent des attributs d’élément avec du contexte comportemental, et en diffusant les éléments recommandés par le biais de canaux web, in-app ou e-mail. Les modèles de classement peuvent être basés sur une formule (par exemple, trier par score d’affinité de catégorie) ou classés par l’IA (par exemple, modèle de recommandation personnalisé). Le modèle gère également les scénarios de démarrage à froid pour les nouveaux visiteurs sans historique comportemental en configurant des recommandations de secours.

L’audience cible de ce modèle comprend les équipes de marchandisage e, les équipes de personnalisation du contenu et les équipes d’expérience digitale qui cherchent à améliorer l’engagement, la conversion et la valeur moyenne des commandes par le biais de recommandations personnalisées basées sur le comportement réel de l’utilisateur.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### [Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.

**KPI :** % de montée en gamme/ventes croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

### [Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

**KPI :** taux de conversion, conversion de lead, coût par lead

### [Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

## Exemples de cas d’utilisation tactiques

Voici quelques implémentations tactiques courantes de ce modèle :

- Widget de vente croisée de produits sur la page des détails du produit (« les clients ont également acheté »).
- Carrousel « Recommandé pour vous » sur la page d’accueil en fonction de l’historique de navigation
- Recommandations de contenu sur le site multimédia en fonction du comportement de lecture
- Widget « Récemment consultés » associé à des éléments similaires
- Recommandations de produits complémentaires après achat
- Recommandations de produits par e-mail basées sur l’affinité comportementale
- Recommandations spécifiques à une catégorie basées sur le comportement de navigation en session
- Reclassement de résultats de recherche basé sur des signaux comportementaux

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité des implémentations de recommandations comportementales.

| KPI | Approche de mesure |
| --- | --- |
| Taux de clic publicitaire (CTR) des recommandations | Clics sur les éléments recommandés divisés par les impressions de recommandation |
| Taux de conversion recommandé | Achats ou actions souhaitées à partir des clics de recommandation divisés par le nombre total de clics de recommandation |
| Chiffre d’affaires influencé par Recommendations | Chiffre d’affaires total des commandes comprenant au moins un produit piloté par des recommandations |
| Effet élévateur de la valeur d’ordre moyenne (AOV) | Augmentation de la valeur d’opportunité pour les sessions qui ont impliqué des recommandations par rapport aux sessions sans |
| Articles par commande | Nombre d’éléments par commande pour les sessions avec recommandations |
| Couverture des recommandations | Pourcentage de pages vues éligibles ou de sessions ayant reçu des recommandations personnalisées (sans secours) |
| Taux de secours du démarrage à froid | Pourcentage de requêtes de recommandations traitées par une logique de secours en raison d’un historique comportemental insuffisant |

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer](AJO) Prise de décision** — Stratégies de sélection, modèles de classement, catalogues d’éléments et politiques de décision qui évaluent les signaux comportementaux et renvoient les éléments les plus pertinents pour chaque visiteur
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Accumulation des données de profil comportemental, évaluation de l’audience pour la portée des recommandations et attributs calculés pour la notation de l’affinité comportementale
- **[!DNL Adobe Experience Platform](AEP)** — Ingestion d’événements comportementaux via [!DNL Web SDK] et [!DNL Mobile SDK], traitement des [!DNL Edge Network], gestion des schémas XDM pour les données d’événement et de catalogue

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les technologies et fonctionnalités utilisées dans ce modèle.

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Créer des règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Création de qualificateurs de collection](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Collecte de données et Web/Mobile SDK

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM et modélisation des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Créer un jeu de données](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Définir une relation entre deux schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Attributs calculés et enrichissement du profil

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer des surfaces de canal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Création et personnalisation de messages

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Rapports et analyses

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Gouvernance et cycle de vie des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Expirations des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Surveillance et observabilité

- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutoriels et guides

- [Vue d’ensemble des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation des balises](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
