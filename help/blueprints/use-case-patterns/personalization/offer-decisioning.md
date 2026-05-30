---
title: Offer Decisioning
description: Découvrez comment utiliser une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur plusieurs canaux.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 5%

---

# Offer Decisioning

Ce guide décrit le modèle de cas d’utilisation d’Offer Decisioning, qui utilise [!DNL Adobe Journey Optimizer] (AJO) Decisioning et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) pour implémenter une logique de sélection d’offres centralisée qui détermine la meilleure offre suivante pour chaque profil client sur l’ensemble des canaux. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Le modèle découple la décision « ce qu’il faut afficher » de la logique de canal « où l’afficher », ce qui permet une sélection d’offres cohérente et optimisée sur les e-mails, le web, les applications mobiles et tout autre point de contact. AJO Decisioning gère l&#39;ensemble du cycle de vie des offres : la création d&#39;offres et la gestion des catalogues, les règles d&#39;éligibilité (qui peut voir chaque offre), les stratégies de classement (comment sélectionner parmi les offres éligibles), les emplacements (où les offres apparaissent) et les politiques de décision (qui lient tout).

## Modèle de cas d’utilisation

Cette section décrit le plan d’exécution et la définition de modèle pour Offer Decisioning.

**Offer Decisioning**

Utilisez une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur l’ensemble des canaux.

**Plan d&#39;exécution :** Évaluation de l&#39;audience > Éligibilité de l&#39;offre > Stratégie de classement > Exécution des décisions > Diffusion > Reporting

## Présentation du cas d’utilisation

Les entreprises ont souvent besoin de présenter l’offre, la promotion ou l’incitation la plus pertinente à chaque client au moment de l’interaction. Que l’interaction se produise dans une campagne par e-mail, sur la page d’accueil d’un site web, dans une application mobile ou à un point de décision dans un parcours à plusieurs étapes, le défi est le même : sélectionnez l’offre optimale dans un catalogue d’options disponibles en fonction de l’identité du client, de ses qualifications et de l’offre la plus susceptible de générer le résultat souhaité.

Offer Decisioning résout ce problème en centralisant toute la logique de sélection des offres dans le moteur de gestion des décisions d&#39;AJO. Plutôt que de coder en dur les affectations d’offres dans des campagnes ou des canaux individuels, le moteur de décision évalue les attributs de chaque profil, l’appartenance à l’audience et les signaux contextuels afin de déterminer la meilleure offre en temps réel. Cette centralisation garantit que le même client reçoit des offres cohérentes et optimisées, quel que soit le canal par lequel il s’engage.

Ce modèle diffère de la personnalisation web/de l’application pour les visiteurs connus en termes de portée : la prise de décision des offres est indépendante du canal et centralisée, tandis que la personnalisation des visiteurs connus se concentre sur la personnalisation des surfaces numériques. Elle diffère de la recommandation comportementale dans le modèle de catalogue : utilisez Offer Decisioning lorsque le jeu d’éléments éligibles est régi par des règles métier, des contraintes d’éligibilité ou des exigences réglementaires (promotions, produits financiers, incentives). Utilisez la recommandation comportementale lorsque l’ensemble d’éléments est volumineux, change en permanence et que la sélection est pilotée par des signaux de similarité ou d’affinité comportementale (catalogues de produits, bibliothèques de contenu).

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.
**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

**[Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.
**KPI :** % de montée en gamme/ventes croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

**[Augmenter la fidélité du client et la valeur de durée de vie](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondissez les relations client et optimisez la valeur à long terme par le biais de programmes de fidélité, de récompenses et d’un engagement personnalisé.
**KPI :** de la valeur de durée de vie du client, conservation, montée en gamme/vente croisée %

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont Offer Decisioning peut être appliqué dans la pratique.

- Prochaine meilleure offre dans les campagnes par e-mail — Sélectionnez la promotion la plus pertinente par destinataire au moment de l’envoi
- Bannière promotionnelle en temps réel sur le site web : la prise de décision sélectionne l’offre au chargement de la page en fonction du profil du visiteur.
- Carte in-app personnalisée offrant le meilleur incentives pour l’étape du cycle de vie de l’utilisateur
- Cohérence des offres cross-canal : la même logique de prise de décision sert les e-mails, le web et les notifications push afin que le client bénéficie d’une expérience d’offre unifiée
- Sélection dynamique de coupons ou de remises basée sur le niveau de valeur client (par exemple, les clients à forte valeur reçoivent une offre premium).
- Sélection d’offres de mise à niveau ou de vente incitative de produits en fonction du niveau d’abonnement actuel
- La récompense de fidélité offre une personnalisation basée sur le niveau et l’historique des activités

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer l’efficacité d’une implémentation d’Offer Decisioning.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’acceptation de l’offre | Pourcentage d’offres diffusées qui entraînent un clic, un échange ou une conversion | Clics ou rachats d’offres / Total des offres diffusées |
| Distribution de la sélection des offres | Proportion de chaque offre sélectionnée dans toutes les décisions | Nombre par offre / Nombre total de décisions rendues |
| Taux de secours | Pourcentage de décisions pour lesquelles aucune offre personnalisée n’a été qualifiée et la solution de secours a été diffusée | Impressions de secours/Nombre total de décisions |
| Taux de conversion | Pourcentage de destinataires de l&#39;offre qui ont effectué l&#39;action souhaitée (achat, inscription, échange) | Conversions/impressions d’offres |
| Revenu incrémentiel | Chiffre d’affaires attribuable aux offres sélectionnées pour la prise de décision par rapport à une population témoin ou une offre de secours | Chiffre d’affaires provenant d’offres personnalisées - Chiffre d’affaires de secours/contrôle |
| Score de cohérence cross-canal | Pourcentage de profils recevant la même offre sur plusieurs canaux dans une fenêtre définie | Offres cohérentes/Nombre total d’impressions multicanaux |
| Taux De Clics Publicitaires De L’Offre | Pourcentage d’impressions d’offres qui génèrent un clic | Clics sur les offres/impressions des offres |

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer](AJO)** — Moteur de gestion des décisions pour la création d’offres, les règles d’éligibilité, les stratégies de classement, les emplacements et les politiques de décision ; la configuration des canaux et la création de messages pour la diffusion d’offres ; l’exécution de campagnes et de parcours
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Évaluation des audiences pour les segments d’éligibilité des offres ; données de profil et attributs calculés utilisés dans l’éligibilité et le classement
- **[!DNL Adobe Experience Platform](AEP)** : banque de profils unifiée, résolution d’identité et base de données prenant en charge AJO et RT-CDP

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les composants utilisés dans ce modèle de cas d’utilisation.

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

### Diffusion d’offres

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Diffuser des offres à l’aide de l’API Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Création et personnalisation de messages

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campagnes et parcours

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Créer une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Commencer avec les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profil et identité

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Modélisation et collecte des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Rapports et analyses

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Gouvernance et cycle de vie des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutoriels

- [Prise en main de l’API Decision Management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
