---
title: Parcours cross-canal avec prise de décision
description: Découvrez comment orchestrer un parcours à plusieurs étapes incorporant la prise de décision en temps réel pour sélectionner un canal, un contenu ou une offre optimal.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 5%

---

# Parcours cross-canal avec prise de décision

Ce guide décrit le parcours cross-canal avec modèle de cas d’utilisation de prise de décision, qui utilise [!DNL Adobe Journey Optimizer] et [!DNL Adobe Real-Time Customer Data Platform] pour orchestrer des parcours multicanaux à plusieurs étapes qui intègrent la prise de décision en temps réel à un ou plusieurs nœuds de parcours. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Le parcours cross-canal avec prise de décision est le modèle d’orchestration de campagne le plus sophistiqué de l’écosystème [!DNL Adobe Experience Platform]. Il étend les parcours orchestrés à plusieurs étapes en incorporant la prise de décision en temps réel, à l’aide de [!DNL AJO] Decisioning pour évaluer le contexte actuel d’un profil et sélectionner de manière dynamique le canal, le contenu ou l’offre optimal à un ou plusieurs points de décision dans la zone de travail du parcours.

## Modèle de cas d’utilisation

parcours cross-canal avec prise de décision ****

Orchestrez un parcours multicanal à plusieurs étapes qui incorpore la prise de décision en temps réel sur un ou plusieurs nœuds pour sélectionner le canal, le contenu ou l’offre optimal.

**Plan d’exécution :** Évaluation de l’audience > Exécution du Parcours > Nœud de décision > Sélection du canal > Diffusion des messages > Reporting

## Présentation du cas d’utilisation

Les entreprises ont de plus en plus besoin de fournir des parcours clients adaptatifs et personnalisés qui répondent dynamiquement au contexte en temps réel de chaque individu plutôt que de suivre une séquence fixe et prédéterminée. Le canal préféré d’un client, son historique d’engagement, son niveau de fidélité, sa valeur de durée de vie prévue et ses intérêts actuels en matière de produits sont autant d’éléments qui déterminent la meilleure action à entreprendre à chaque point de contact.

Le parcours cross-canal avec prise de décision répond à ce besoin en combinant deux puissantes fonctionnalités de [!DNL AJO] : l&#39;orchestration des parcours (qui gère le flux à plusieurs étapes, le timing, les conditions et la diffusion de canal) et la prise de décision (qui évalue les règles d&#39;éligibilité, applique des stratégies de classement et sélectionne l&#39;offre ou la variante de contenu optimale à chaque point de décision).

Ce modèle est approprié dans les cas suivants :

- Le parcours doit s’adapter dynamiquement au statut en temps réel de chaque profil plutôt que de suivre un canal fixe ou une séquence de contenu
- Plusieurs offres, variantes de contenu ou canaux sont candidats au niveau d’un ou de plusieurs nœuds de parcours. La meilleure option doit être sélectionnée en fonction du contexte du profil
- Le classement assisté par l’IA ou basé sur des formules est nécessaire pour optimiser la sélection des offres sur le parcours
- L’entreprise souhaite consolider la logique de sélection des canaux et la gestion des offres dans un cadre de décision centralisé plutôt que de maintenir une logique d’embranchement complexe

Le public cible comprend des spécialistes du marketing qui gèrent des programmes de cycle de vie, des parcours de fidélité, des séquences de reconquête et des flux d’intégration pour lesquels la personnalisation à grande échelle nécessite une prise de décision automatisée à chaque point de contact.

>[!NOTE]
>Si votre parcours ne nécessite pas de prise de décision dynamique au niveau des nœuds individuels (par exemple, un programme d’apprentissage ou d’intégration à séquence fixe), consultez [parcours orchestré à plusieurs étapes](multi-step-orchestrated-journey.md). Ce modèle est plus simple à configurer et ne nécessite pas AJO Decisioning.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.
**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

**[Augmenter la fidélité du client et la valeur de durée de vie](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondissez les relations client et optimisez la valeur à long terme par le biais de programmes de fidélité, de récompenses et d’un engagement personnalisé.
**KPI :** de la valeur de durée de vie du client, conservation, montée en gamme/vente croisée %

**[Améliorez la fidélisation client](../../business-objectives/customer-experience/improve-customer-retention.md)**
Maintenez l’engagement et le renouvellement des clients existants grâce à des expériences axées sur la valeur et à l’entretien continu des relations.
**KPI : rétention** valeur client sur toute la durée de vie, engagement

**[Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.
**KPI :** % de montée en gamme/ventes croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont le parcours cross-canal avec la prise de décision peut être appliqué dans la pratique.

- parcours de reconquête adaptative **: parcours à plusieurs étapes dans lequel la prise de décision sélectionne le canal (e-mail, notification push ou SMS) en fonction de l’historique d’engagement de chaque profil, et sélectionne de manière dynamique la meilleure offre d’incitation en fonction de la valeur de durée de vie prévue**
- parcours du cycle de vie de la meilleure action à venir **— La prise de décision détermine les éléments à communiquer à chaque étape du cycle de vie du client, en effectuant une sélection parmi le contenu d’intégration, les offres de vente croisée, les récompenses de fidélité ou les incentives de fidélisation**
- **Intégration personnalisée avec sélection dynamique de contenu** — Nouveau parcours d’intégration des clients où chaque point de contact utilise la prise de décision pour sélectionner le contenu de formation au produit, les conseils ou les offres d’activation les plus pertinents
- parcours de programme de fidélité cross-canal avec récompenses personnalisées **— Les membres du programme de fidélité progressent dans un parcours où Decisioning sélectionne des offres de récompense personnalisées en fonction du niveau, de l&#39;historique d&#39;achat et de l&#39;affinité catégorielle**
- **Réengagement dynamique avec optimisation du canal et de l’incitation** — Réengagement client dormant où le canal d’approche et l’incitation sont sélectionnés de manière dynamique pour maximiser la probabilité de réponse
- **Développement du cycle de vie du client avec des recommandations de contenu classées par l’IA** — parcours de développement continu dans lequel la prise de décision classée par l’IA sélectionne le contenu ou les recommandations de produit les plus pertinents à chaque point de contact

## Indicateurs clés de performance

Utilisez les indicateurs de performance clés suivants pour mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’achèvement du parcours | Pourcentage de profils qui ont terminé le parcours complet | Rapport de parcours : terminé / saisi |
| Taux d’acceptation de l’offre | Pourcentage d&#39;offres sélectionnées pour la prise de décision qui sont engagées avec (ayant fait l&#39;objet d&#39;un clic, ayant été échangées) | Rapport Decisioning : clics sur les offres/impressions des offres |
| Taux d’engagement du canal | Taux d’ouvertures et de clics sur chaque canal utilisé dans le parcours | Mesures de diffusion par canal dans le rapport de parcours |
| Taux de conversion | Pourcentage d&#39;acteurs du parcours qui effectuent l&#39;action de conversion cible | Parcours du suivi des événements de sortie pour l’analyse de CJA funnel |
| Taux d’offres de secours | Pourcentage de requêtes de décision renvoyant l’offre de secours au lieu d’une offre personnalisée | Rapport Decisioning : sélections de secours/total de sélections |
| Impact sur la valeur de la durée de vie du client | Variation de la CLV des participants au parcours par rapport à la population témoin | Analyse des cohortes CJA avec comparaison des exclusions |
| Chiffre d’affaires de ventes croisées/incitatives | Chiffre d’affaires incrémentiel attribué aux offres sélectionnées pour la prise de décision | Analyse de l’attribution CJA sur les conversions pilotées par les offres |
| Efficacité du classement des décisions | Différence de performances entre les offres classées par l’IA et la sélection aléatoire/basée sur les priorités | Expérience A/B comparant les stratégies de classement |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer]([!DNL AJO])** : orchestration des Parcours (conception de zone de travail à plusieurs étapes, conditions d’entrée, attentes, conditions, critères de sortie), création de messages sur plusieurs canaux, configuration de la surface de canal, gestion des conflits et des priorités
- **[!DNL Adobe Journey Optimizer]Decisioning** — Gestion des offres et des éléments de contenu, règles d&#39;éligibilité, stratégies de classement (priorité, formule, IA), politiques de décision, emplacements, offres de secours
- **[!DNL Adobe Real-Time Customer Data Platform]([!DNL RT-CDP])** — Évaluation des audiences pour les segments d’entrée sur le parcours et d’éligibilité des offres, enrichissement du profil avec des attributs calculés et des scores de propension, application du consentement et de la gouvernance
- **[!DNL Adobe Experience Platform]([!DNL AEP])** — Banque de profils client en temps réel, Service d’identités pour la résolution cross-canal, la modélisation des données et l’infrastructure d’ingestion

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

### Orchestration des parcours

- [Commencer avec les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Activité Lecture d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Gestion des conflits, des priorités et des fréquences

- [Gestion des conflits et des priorités - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Rapports et analyses

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profil et identité

- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
