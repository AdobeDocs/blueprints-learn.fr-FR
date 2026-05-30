---
title: Messagerie déclenchée par événement
description: Découvrez comment diffuser des messages contextuels en temps réel en réponse à des événements comportementaux ou système.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 5%

---

# Messages déclenchés par un événement

Ce guide décrit le modèle de cas d’utilisation de messagerie déclenchée par un événement, qui utilise [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP) pour diffuser des messages contextuels en temps réel en réponse à des événements comportementaux ou système. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Ce modèle couvre le cycle de vie complet, de l’ingestion d’événements et de la création de parcours à la diffusion de messages et au compte rendu des performances.

## Modèle de cas d’utilisation

Cette section décrit le modèle de base et le plan d’exécution qui génère la messagerie déclenchée par un événement.

**Messagerie déclenchée par un événement**

Détectez un événement système ou comportemental en temps réel, puis envoyez un message contextuel au profil de déclenchement.

**Plan d&#39;exécution :** Ingestion d&#39;événement > Entrée de Parcours > Évaluation de condition > Diffusion de message > Reporting

## Présentation du cas d’utilisation

Les messages déclenchés par un événement diffusent un message contextuel en réponse à un événement comportemental ou système en temps réel. Contrairement à l’activation des messages sortants par lots, qui envoie à une audience pré-évaluée selon un planning, ce modèle écoute un événement qualifiant, tel qu’un abandon de panier, une session de navigation, un envoi de formulaire ou un changement d’état du système, et entre immédiatement le profil de déclenchement dans un parcours qui évalue les conditions et diffuse un message.

Le modèle repose sur la diffusion en continu d’événements en temps réel dans AEP (via Web SDK, Mobile SDK ou une API côté serveur), un parcours avec une entrée d’événement unitaire dans AJO et une logique d’évaluation des conditions qui détermine si et quoi envoyer. Le message est généralement envoyé dans les minutes qui suivent l’événement de déclenchement, ce qui rend ce modèle idéal pour les communications sensibles au temps et pertinentes au contexte.

Les entreprises utilisent ce modèle pour répondre en temps réel aux actions des clients, ce qui accroît la pertinence et entraîne des taux d’engagement et de conversion plus élevés par rapport aux communications par lots planifiées. Les scénarios courants incluent la récupération de panier abandonné, le suivi après achat, les messages de bienvenue après enregistrement et les notifications sensibles au facteur temps comme les échecs de paiement ou les alertes de chute de prix.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Récupérer les paniers et parcours abandonnés](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Réengagez les utilisateurs qui ont abandonné lors des flux d’achat, de demande ou d’inscription avec des suivis personnalisés et opportuns.

| KPI |
| --- |
| Taux De Conversion, Chiffre D’Affaires Incrémentiel, Engagement |

**[Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

| KPI |
| --- |
| Taux De Conversion, Conversion De Lead, Coût Par Lead |

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

| KPI |
| --- |
| Engagement, taux de conversion, satisfaction des clients (CSAT) |

**[Améliorer l’intégration des clients](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Accélérez la rentabilité pour les nouveaux clients grâce à des expériences de bienvenue et des parcours d’activation rationalisés et personnalisés.

| KPI |
| --- |
| Engagement, rétention, taux de conversion |

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont la messagerie déclenchée par un événement peut être appliquée à différents contextes d’entreprise.

- **E-mail ou SMS d’abandon de panier** — Envoyez un message de rappel lorsqu’un client ajoute des articles à son panier, mais ne procède pas à l’achat dans un délai défini
- **Suivi de l’abandon de la navigation** — Réengagez les visiteurs qui ont consulté des produits ou du contenu, mais n’ont pas effectué d’action de conversion
- **Remerciements après achat ou vente croisée** — Donnez une confirmation et une recommandation de vente croisée immédiatement après un achat
- **Rappel d’expiration de la version d’essai** — Avertissez les utilisateurs approchant de la fin d’un essai gratuit avec des messages de renouvellement ou de conversion
- **Message de bienvenue après l’enregistrement** — Envoyez un message d’intégration immédiat lorsqu’un nouvel utilisateur s’enregistre ou crée un compte
- **Confirmation d’envoi du formulaire** — Acceptez les envois de formulaire (demandes de contact, demandes, inscriptions) avec une confirmation contextuelle
- **Notification d&#39;échec de paiement** — Avertissez les clients lorsqu&#39;un paiement récurrent échoue, les invitant à mettre à jour les informations de paiement
- **Notification push de désinstallation de reconquête de l&#39;application** — Déclenchez un message de reconquête lorsqu&#39;un utilisateur désinstalle une application mobile
- **Confirmation de réservation ou de rendez-vous** — Envoyez une confirmation immédiate après la planification d&#39;une réservation, d&#39;une réservation ou d&#39;un rendez-vous
- **Alerte de chute de prix pour les articles mis en vente** — Avertissez les clients lorsqu&#39;un produit de leur liste de souhaits baisse de prix

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer l’efficacité des implémentations de messagerie déclenchée par un événement.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux de conversion | Pourcentage de destinataires de messages déclenchés qui effectuent l’action souhaitée (achat, inscription, renouvellement) | Conversions/Messages Diffusés * 100 |
| Revenu incrémentiel | Chiffre d’affaires supplémentaire attribuable aux messages déclenchés par un événement par rapport aux populations témoins sans envoi | Chiffre d’affaires d’envois déclenchés - Ligne de base de la population témoin |
| Taux d’ouvertures | Pourcentage de messages diffusés ouverts par les destinataires | Ouvertures / Diffusés * 100 |
| Taux de clic publicitaire (CTR) | Pourcentage de messages diffusés qui génèrent au moins un clic | Clics / Diffusés * 100 |
| Délai jusqu’à la conversion | Temps moyen écoulé entre la diffusion du message et l&#39;événement de conversion | Avg(date et heure de conversion - date et heure de diffusion) |
| Taux d’achèvement du parcours | Pourcentage de profils qui entrent dans le parcours et atteignent l’étape de diffusion du message (non ignorés par les conditions ou les sorties) | Profils atteignant la diffusion / Profils entrant dans le parcours * 100 |
| Taux De Suppression Des Messages | Pourcentage de profils admissibles supprimés en raison des limitations de fréquence, du consentement ou de l’évaluation de la condition | Profils supprimés / Nombre total de profils qualifiés * 100 |
| Taux de rebond | Pourcentage de messages qui n’ont pas pu être délivrés en raison de hard ou soft bounces | Rebonds / Envoyés * 100 |

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** orchestration des Parcours avec entrée unitaire d’événement, évaluation de condition, étapes d’attente, création de messages, configuration des canaux, gouvernance des fréquences et création de rapports de diffusion
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Évaluation de l’audience pour le filtrage basé sur les conditions dans les parcours, l’application du consentement et de la gouvernance, l’enrichissement des profils
- **[!DNL Adobe Experience Platform] (AEP)** — Ingestion d’événements en temps réel via Web SDK, Mobile SDK ou une API côté serveur ; modélisation des données ; résolution d’identité ; Edge Network

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les fonctionnalités utilisées dans cette implémentation.

### Orchestration des parcours

- [Commencer avec les parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Événements généraux](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Créer un SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/create-sms)
- [Concevoir une notification push](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/push/design-push)

### Fréquence et règles métier

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [API de limitation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Gestion des conflits et des priorités

- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Scores de priorité](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Rapports et performances

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Collecte et ingestion de données

- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/fr/docs/experience-platform/edge-network-server-api/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/datastreams/configure)
- [Présentation de l’ingestion par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/streaming/overview)

### Modélisation des données et schémas

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)

### Segmentation et audiences

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Attributs calculés

- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/ui)

### Surveillance et observabilité

- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/guardrails)

### Tutoriels et guides

- [Tutoriel sur la création de parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/install/overview)
