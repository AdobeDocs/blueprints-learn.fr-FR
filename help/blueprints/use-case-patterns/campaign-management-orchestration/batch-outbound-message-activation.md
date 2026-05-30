---
title: Activation des messages sortants par lots
description: Découvrez comment évaluer une audience et diffuser un message sortant planifié dans une seule exécution par lots.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 4%

---

# Activation des messages sortants par lots

Ce guide décrit le modèle de cas d’utilisation d’activation des messages sortants par lots, qui utilise [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) pour diffuser des messages sortants planifiés vers des segments d’audience définis. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

L’activation des messages sortants par lots est le modèle de campagne fondamental pour les messages sortants un-à-plusieurs. Il couvre l’ensemble du cycle de vie, de la définition de l’audience à la diffusion des messages et l’analyse des performances.

## Modèle de cas d’utilisation

**Activation des messages sortants par lots**

Évaluez une audience, puis diffusez un message sortant planifié (e-mail, SMS, notification push) à tous les profils admissibles dans une seule exécution par lots.

**Plan d’exécution :** Évaluation d’audience > Création de messages > Exécution de campagnes > Reporting

## Présentation du cas d’utilisation

Les entreprises ont souvent besoin de diffuser un seul message à un segment d’audience connu à un moment spécifique ou en réponse à un événement système. Ce modèle répond à cette exigence en combinant l’évaluation des audiences dans [!DNL RT-CDP] avec la création de messages et l’exécution de campagnes dans [!DNL Journey Optimizer].

Le scénario commercial est simple : définissez qui doit recevoir le message, créez le contenu du message avec une personnalisation, liez l&#39;audience et le message dans une campagne ou un parcours et exécutez l&#39;envoi selon un planning, via la qualification de l&#39;audience ou via un déclencheur système. Le résultat est un message diffusé avec des rapports complets sur les mesures de diffusion, d’engagement et de conversion.

Ce modèle s’applique chaque fois qu’un objectif commercial peut être avancé en diffusant un seul message à une audience connue en une seule exécution. Elle se différencie des messages déclenchés par un événement, qui répondent aux événements comportementaux en temps réel, et des parcours orchestrés en plusieurs étapes, qui guident les profils à travers plusieurs points de contact au fil du temps. L’activation par lots est le modèle de campagne le plus simple et le point de départ le plus courant pour les cas d’utilisation de messagerie sortante.

## Objectifs commerciaux clés

Cette section identifie les principaux objectifs commerciaux pris en charge par l&#39;activation des messages sortants par lots.

### Augmenter l’engagement des e-mails et des campagnes

**Description :** améliorer les taux d’ouverture, les taux de clics publicitaires et la réponse globale de la campagne par le biais d’un contenu et d’un ciblage optimisés.

**KPI :** taux d’ouverture, d’engagement, de conversion

### Augmenter le chiffre d’affaires et les ventes

**Description :** stimuler la croissance du chiffre d’affaires de premier plan grâce à des canaux numériques, des campagnes et des parcours client optimisés.

**KPI : Taux de conversion**, Chiffre d’affaires incrémentiel, Valeur de commande moyenne

**Objectif commercial associé :** [Augmenter le chiffre d’affaires et les ventes](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Rationaliser l’exécution des campagnes

**Description :** réduire le temps de création de la campagne et simplifier la diffusion de campagnes multicanaux par le biais de modèles, d’une automatisation et de processus normalisés.

**KPI :** % de vitesse de mise sur le marché, d’efficacité, d’exécution dans les délais

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent les applications courantes de l’activation des messages sortants par lots.

- **Annonce de vente ou explosion d’e-mail promotionnel** — Diffusez une offre promotionnelle à un segment de clients éligibles à une date planifiée
- **Notification push de lancement du produit** — Notifiez les clients intéressés par une nouvelle disponibilité du produit via push
- **Newsletter ou e-mail de résumé** — Diffusez des résumés de contenu périodiques aux audiences abonnées
- **Invitation à l’inscription à un événement** — Invitez des prospects qualifiés à des webinaires, des conférences ou des événements en personne
- **E-mail de rappel de renouvellement d’abonnement** — Rappeler aux clients dont la date de renouvellement approche de prendre des mesures
- **Notification de jalon du programme de fidélité** — Félicitez les membres qui atteignent les niveaux de fidélité ou les seuils de point
- **E-mail call-to-action spécifique** — Entraînez une action ciblée telle que la réalisation d’un achat, la mise à jour des préférences ou l’enregistrement à un programme
- **Campagne SMS pour la vente flash ou l’offre limitée dans le temps** — Envoyez des promotions urgentes et limitées dans le temps par SMS aux audiences inscrites

## Indicateurs clés de performance

Le tableau suivant définit les KPI utilisés pour mesurer l’efficacité des campagnes.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux De Diffusion | Pourcentage de messages envoyés avec succès aux destinataires | Livrés / Envoyés x 100 |
| Taux d’ouvertures | Pourcentage de messages diffusés ouverts par les destinataires | Ouvertures uniques/diffusées x 100 |
| Taux de clic publicitaire (CTR) | Pourcentage de messages diffusés sur lesquels un utilisateur a cliqué sur un lien | Clics uniques / Diffusés x 100 |
| Taux de clic-ouverture (CTOR) | Pourcentage de messages ouverts sur lesquels un utilisateur a cliqué sur un lien | Clics uniques / Ouvertures uniques x 100 |
| Taux de conversion | Pourcentage de destinataires ayant effectué l’action souhaitée | Conversions / Livrés x 100 |
| Taux de désabonnement | Pourcentage de destinataires s’étant désabonnés après réception du message | Désabonnements / Diffusés x 100 |
| Taux de rebond | Pourcentage de messages qui n’ont pas pu être diffusés | Rebonds / Envoyés x 100 |
| Recettes par e-mail envoyé | Chiffre d’affaires attribué à la campagne divisé par les messages envoyés | Chiffre d’affaires total/envoyé |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle.

- **[!DNL Adobe Journey Optimizer](AJO)** — Création de messages, configuration des canaux, exécution de campagnes, orchestration des parcours, expérimentation de contenu, règles de fréquence et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Évaluation de l’audience, consentement et application de la gouvernance
- **[!DNL Adobe Experience Platform](AEP)** — Banque de profils, service d’identités, schémas, jeux de données, collecte de données

## Documentation connexe

Cette section fournit des liens complets vers [!DNL Experience League] documentation organisée par rubrique.

### Campagnes

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Créer une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Campagnes déclenchées par API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Parcours

- [Commencer avec les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Lecture du parcours d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utiliser les composants de contenu Designer d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Importer ou coder du contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Gestion de contenu

- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Envoyer des BAT par e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendu des emails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Gestion des fréquences et des conflits

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Création de rapports

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Modélisation des données et identité

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutoriels et prise en main

- [Prise en main de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Créer votre première campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Créer votre premier parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
