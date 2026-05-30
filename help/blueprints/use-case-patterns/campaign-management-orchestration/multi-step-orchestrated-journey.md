---
title: Parcours Orchestré À Plusieurs Étapes
description: Découvrez comment guider un profil à travers un parcours d’embranchement multipoint avec des attentes, des conditions et plusieurs actions de message au fil du temps.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 5%

---

# Parcours orchestré à plusieurs étapes

Ce guide décrit le modèle de cas d’utilisation de parcours orchestré en plusieurs étapes, qui utilise [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Real-Time Customer Data Platform] (RT-CDP) pour orchestrer des parcours client multi-touch d’embranchement qui diffusent plusieurs messages au fil du temps. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

## Modèle de cas d’utilisation

**Parcours orchestré en plusieurs étapes**

Guidez un profil à travers un parcours multi-touch d’embranchement avec des attentes, des conditions et plusieurs actions de message au fil du temps.

**Plan d’exécution :** Évaluation d’audience > Exécution de Parcours (multi-nœud) > Branchement de condition > Diffusion de message (xN) > Critères de sortie > Rapports

## Présentation du cas d’utilisation

Les parcours orchestrés en plusieurs étapes traitent des scénarios commerciaux où un seul message est insuffisant pour atteindre le résultat souhaité par le client. Au lieu d’un envoi unique, le parcours guide chaque profil à travers une séquence de points de contact (e-mails, SMS, notifications push ou messages in-app) espacés sur plusieurs jours ou semaines, avec une logique d’embranchement qui adapte le chemin en fonction des attributs de profil, des signaux comportementaux ou des données d’événement.

Ces parcours constituent le modèle de campagne le plus complexe d’AJO. Ils combinent une entrée basée sur une audience ou sur un événement avec une zone de travail de nœuds d’action (messages), de nœuds de condition (logique de branchement), de nœuds d’attente (retards) et de critères de sortie (événements de conversion ou délais). Chaque profil progresse dans le parcours indépendamment, à son propre rythme, recevant du contenu contextuellement pertinent à chaque étape.

Ce modèle intègre les modèles plus simples : activation des messages sortants par lots pour les campagnes à envoi unique et messagerie déclenchée par événement pour les réponses à événement unique. Utilisez ce modèle lorsque le cas d’utilisation nécessite d’entretenir un profil par le biais de plusieurs interactions au fil du temps.

>[!NOTE]
>Si votre parcours nécessite une sélection dynamique de l’offre, du contenu ou du canal optimal à des points de décision individuels, consultez la section [parcours cross-canal avec prise de décision](cross-channel-journey-with-decisioning.md). Ce modèle l’étend à l’intégration d’AJO Decisioning.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Amélioration de la fidélisation client

Maintenez l’engagement et le renouvellement des clients existants grâce à des expériences axées sur la valeur et à l’entretien continu des relations.

**KPI : rétention** valeur client sur toute la durée de vie, engagement

[En savoir plus sur l’amélioration de la fidélisation des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Améliorer l’intégration des clients

Accélérez la rentabilité pour les nouveaux clients grâce à des expériences de bienvenue et des parcours d’activation rationalisés et personnalisés.

**KPI : engagement** rétention et taux de conversion

[En savoir plus sur l’amélioration de l’intégration des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Réengager les clients inactifs

Récupérez les clients inactifs ou obsolètes avec des campagnes de réactivation ciblées basées sur des signaux comportementaux.

**KPI : engagement** rétention et taux de conversion

[En savoir plus sur l’amélioration de la fidélisation des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Récupérer les paniers et les parcours abandonnés

Réengagez les utilisateurs qui ont abandonné lors des flux d’achat, de demande ou d’inscription avec des suivis personnalisés et opportuns.

**KPI :** taux de conversion, revenu incrémentiel, engagement

[En savoir plus sur la récupération des paniers et des parcours abandonnés](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent les applications courantes du modèle de parcours orchestré à plusieurs étapes.

- **Série d’intégration des clients** — E-mail de bienvenue, suivi d’une formation sur les fonctionnalités, puis d’une invite d’activation au cours des 14 premiers jours suivant l’enregistrement
- **Campagne de réengagement au goutte-à-goutte** — Un e-mail de rappel, puis une offre incitative, puis un avis final pour les clients non engagés depuis plus de 3 semaines
- parcours jalon de fidélité&#x200B;**— Notification de mise à niveau du niveau, suivie d’une offre exclusive, puis d’un rappel de renouvellement à l’approche de l’anniversaire de l’abonnement**
- **Séquence de reconquête** : e-mail « Vous nous manquez », puis offre de remise par e-mail, puis dernier rappel par SMS pour les acheteurs obsolètes
- parcours d’adoption du produit **— Bienvenue d’essai, conseils d’utilisation, puis une invite de mise à niveau au fur et à mesure de la période d’essai**
- **Séquence de renouvellement d’abonnement** — Avis de 30 jours, rappel de 7 jours, puis message de jour d’expiration pour les renouvellements d’abonnement à venir
- **Formation après achat** - e-mail de remerciement, guide d’utilisation, recommandation de vente croisée, puis demande de révision 30 jours après l’achat

## Indicateurs clés de performance

Utilisez les KPI suivants pour mesurer l’efficacité de votre mise en œuvre de parcours orchestré à plusieurs étapes.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’achèvement du parcours | Pourcentage de profils qui terminent le parcours complet sans sortie anticipée | Rapport de parcours : sorti (terminé) / Entré |
| Taux de conversion de l’étape | Pourcentage de profils qui passent d’une étape à l’autre | Mesures par nœud dans le rapport de parcours |
| Taux d’engagement du canal | Taux d’ouverture, taux de clics publicitaires et taux de réponse à chaque point de contact | Mesures de diffusion et d’engagement par message |
| Taux de conversion des critères de sortie | Pourcentage de profils qui déclenchent l’événement de sortie (par exemple, achat, inscription) avant la temporisation du parcours | Nombre d’accès aux critères de sortie / Total saisi |
| Délai jusqu’à la conversion | Durée moyenne entre l’entrée sur le parcours et l’événement correspondant au critère de sortie | Parcours analytics : horodatage d’entrée en date et heure de l’événement de conversion |
| Taux de restitution des parcours | Pourcentage de profils qui cessent de s’engager à chaque étape (analyse des abandons) | Visualisation des abandons CJA à travers les étapes de parcours |
| Taux de rétention/réengagement | Pourcentage de profils ciblés qui reviennent au statut actif | Analyse comportementale post-parcours dans CJA |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** : moteur d’orchestration des Parcours, création de messages, configuration des canaux, expérimentation de contenu, gestion des fréquences et des conflits, et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Évaluation et définition de l’audience pour les audiences d’entrée de parcours, les données de profil pour la personnalisation et l’embranchement des conditions
- **[!DNL Adobe Experience Platform] (AEP)** — Banque de profils, service d’identités, ingestion des données d’événement et infrastructure de données de base

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les fonctionnalités utilisées dans cette implémentation.

### Parcours

- [Commencer avec les parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Tester votre parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Activités de parcours

- [Activité Lecture d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Événements généraux](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Activité de fin](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Configurer une action personnalisée](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Gestion des entrées et des sorties

- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer des surfaces de canal](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Configurer le canal SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utiliser les composants de contenu Designer d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Fréquence, conflit et priorité

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/api/edge-segmentation)

### Rapports et analyses

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)

### Consentement et gouvernance

- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Base des données

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation du profil](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
