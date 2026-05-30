---
title: Personalization Web/App Connu Des Visiteurs
description: Découvrez comment diffuser du contenu, des offres ou des promotions personnalisés à des visiteurs identifiés en fonction de l’appartenance à un profil et à un segment en temps réel.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 4%

---

# Personnalisation web/d’application de visiteurs connus

Ce guide décrit le modèle de cas d’utilisation de la personnalisation web/de l’application visiteur connu, qui utilise [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) pour diffuser du contenu personnalisé aux visiteurs identifiés sur des surfaces numériques. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

La personnalisation web/de l’application d’un visiteur connu est le modèle de personnalisation principal pour les expériences digitales authentifiées. Contrairement à la personnalisation du visiteur anonyme, qui repose uniquement sur des signaux comportementaux en session, ce modèle exploite le profil unifié complet : données comportementales historiques, appartenance à un segment, niveau de fidélité, historique d’achats, étape du cycle de vie, attributs calculés et scores de propension. Il prend en charge la personnalisation sur plusieurs pages web (via le canal web d’AJO), les messages in-app mobiles et les cartes de contenu.

## Modèle de cas d’utilisation

Cette section décrit le modèle de base et son plan d’exécution.

**Personnalisation web/d’application de visiteurs connus**

Diffusez du contenu, des offres ou des promotions personnalisés à un visiteur identifié en fonction du profil en temps réel et de l’appartenance à un segment sur des surfaces web, mobiles in-app et de cartes de contenu.

**Plan d’exécution :** Évaluation de l’audience > Prise de décision Personalization > Configuration de la surface/du canal > Diffusion de contenu > Suivi des impressions > Rapports

## Présentation du cas d’utilisation

Les entreprises disposant de propriétés numériques authentifiées (sites d’e-commerce, portails bancaires, services d’abonnement, programmes de fidélité, applications mobiles) doivent offrir des expériences personnalisées qui reflètent la relation de chaque client avec la marque. Lorsqu’un visiteur se connecte ou est reconnu par la résolution d’identité, la plateforme peut accéder à son profil unifié complet et diffuser du contenu adapté à ses attributs, comportements et préférences spécifiques.

Ce modèle résout le scénario où un visiteur identifié arrive sur une propriété web ou ouvre une application mobile et où le système doit déterminer le contenu, l’offre ou la promotion optimal à afficher en fonction des données de profil en temps réel et de l’appartenance à l’audience. La décision de personnalisation se produit à la périphérie de l’application, en millisecondes, ce qui permet la diffusion de contenu pendant une sous-seconde sans latence perceptible.

Le modèle prend en charge la personnalisation déterministe (où un contenu spécifique correspond à des segments d’audience spécifiques) et la prise de décision dynamique (où AJO Decisioning évalue les règles d’éligibilité et les stratégies de classement pour sélectionner le contenu optimal par profil). Il s’étend sur plusieurs surfaces numériques (pages web, messages in-app mobiles et cartes de contenu), ce qui permet une personnalisation cohérente sur le parcours numérique du client.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Offrir des expériences personnalisées aux clients

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus. Pour plus d’informations, voir [Offrir des expériences client personnalisées](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

### Augmenter l’engagement du site web

Améliorez le temps passé sur le site, les pages par session et l’interaction avec le contenu web grâce à des expériences pertinentes. Pour plus d’informations, voir [Augmenter l’engagement du site web](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPI :** de la page (web), engagement, taux de conversion

### Augmenter l’engagement des applications mobiles

Stimulez l’utilisation active quotidienne, l’adoption des fonctionnalités et les conversions in-app par le biais d’expériences in-app personnalisées.

**KPI : engagement** rétention et taux de conversion

## Exemples de cas d’utilisation tactiques

Voici quelques implémentations tactiques courantes de ce modèle :

- Personnalisation du héros de la page d’accueil par niveau de fidélité ou étape du cycle de vie : affichez différentes bannières principales selon que le client est nouveau, actif, à risque ou VIP
- Carrousel de recommandations de produits basé sur l’historique des achats — suggestions de produits pertinentes à la surface utilisant les données d’achat passées et les scores d’affinité du produit
- Bannière promotionnelle personnalisée par segment de clients — afficher différentes promotions sur des segments à forte valeur, à risque et nouveaux clients
- Message in-app pour les utilisateurs et utilisatrices mobiles basé sur l’adoption des fonctionnalités : guide les utilisateurs et utilisatrices vers des fonctionnalités sous-utilisées en fonction de leurs schémas d’utilisation
- Carte de contenu avec offre personnalisée sur le tableau de bord du compte — offres persistantes, non admissibles adaptées au profil du client
- Affichage personnalisé des prix ou des remises en fonction du niveau client : affichez des prix spécifiques au niveau ou des remises exclusives aux membres du programme de fidélité.
- Widget de recommandation de vente croisée basé sur les produits détenus — suggérez des produits ou services complémentaires basés sur le portefeuille actuel
- Navigation ou ordre de contenu personnalisé en fonction des intérêts : réorganisez les modules de contenu ou les éléments de navigation en fonction des préférences démontrées.

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Approche de mesure | Conseils pour l’évaluation des performances |
| --- | --- | --- |
| Taux d’engagement Personalization | Clics et interactions avec des éléments de contenu personnalisés divisés par des impressions | Le contenu personnalisé doit surpasser le contenu par défaut de 20 à 50 % |
| Augmentation du taux de conversion | Taux de conversion des expériences personnalisées par rapport aux expériences de contrôle/par défaut | Cible 10 à 30 % d’effet élévateur sur les expériences non personnalisées |
| Taux de clic publicitaire (CTR) | Clics sur des appels à l’action, des offres et des recommandations personnalisés divisés par des impressions | Surveiller par surface (web, in-app, carte de contenu) et par segment |
| Chiffre d’affaires par visite | Chiffre d’affaires attribué aux sessions avec expériences personnalisées | Comparaison des cohortes de visiteurs personnalisées et non personnalisées |
| Taux d’interaction des cartes de contenu | Clics et rejets de cartes de contenu relatifs aux impressions | Suivi par type de carte et segment d’audience |
| Engagement Des Messages In-App | Interactions de messages in-app (clics CTA, rejets) relatives aux impressions | Comparer les segments d’audience et les types de messages |
| Temps passé sur la page | Temps moyen passé sur des pages avec du contenu personnalisé par rapport au temps par défaut | Les pages personnalisées doivent afficher un temps d’affichage plus long. |
| Taux d’acceptation de l’offre | Pourcentage d’offres sélectionnées pour la prise de décision qui génèrent un événement de conversion | Suivi par offre, par emplacement et par stratégie de classement |

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer](AJO)** : configuration du canal web, configuration du canal in-app, configuration du canal de carte de contenu, prise de décision (sélection d’offres et classement), création de messages (création de contenu personnalisé), exécution de campagnes, expérimentation de contenu et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Évaluation d’audience (Edge, streaming et lot), recherche de profil en temps réel via Edge Network, enrichissement du profil avec des attributs calculés et des scores de propension
- **[!DNL Adobe Experience Platform](AEP)** — Banque de profils, service d’identités, Web SDK, Mobile SDK, configuration des flux de données, diffusion sur le réseau Edge

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les technologies et configurations référencées dans ce guide.

### Personnalisation des canaux web

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Configuration du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### Canaux in-app et de carte de contenu

- [Présentation du canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Conditions préalables relatives au canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Créer des messages in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Canal de la carte de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configuration des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Créer des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Créer des règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization et contenu

- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Collecte de données et SDK

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campagnes et expérimentation

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Créer une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Attributs calculés et enrichissement

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Rapports et analyses

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Gouvernance et confidentialité

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
