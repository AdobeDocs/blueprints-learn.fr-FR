---
title: Marketing et gestion de Parcours par groupe d'achats
description: Découvrez comment développer des parcours au niveau du compte qui qualifient les prospects en groupes d’achats afin d’améliorer l’efficacité du marketing B2B.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# Gestion des parcours et marketing par groupe d&#39;achat

Ce guide décrit le modèle de cas d&#39;utilisation de la gestion des parcours et du marketing basé sur les groupes d&#39;achats, qui utilise [!DNL Adobe Journey Optimizer B2B Edition] et [!DNL Real-Time CDP B2B Edition] pour mettre en œuvre l&#39;orchestration des parcours au niveau du compte avec la gestion des groupes d&#39;achats. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Contrairement aux modèles de parcours au niveau de la personne, ce modèle fonctionne au niveau du compte, qualifiant les prospects individuels dans les groupes d’achat associés aux intérêts de la solution, notant l’engagement au niveau du groupe d’achat et orchestrant des parcours de compte à plusieurs étapes qui font progresser les comptes à travers les étapes du pipeline vers la préparation aux ventes.

## Modèle de cas d’utilisation

**Marketing et gestion de parcours par groupe d&#39;achat**

Développez des parcours au niveau du compte qui qualifient les prospects en groupes d’achat afin d’améliorer l’efficacité du marketing B2B.

**Plan d’exécution : Identification de compte** > Définition du groupe d’achat > Qualification du lead > Exécution du Parcours de compte > Notation de l’engagement > Rapports

## Présentation du cas d’utilisation

Les organisations B2B sont confrontées à un défi fondamental : les décisions d’achat sont rarement prises par une seule personne. Les achats B2B complexes impliquent plusieurs parties prenantes (décideurs, influenceurs, champions, détenteurs de budget et évaluateurs techniques) qui forment collectivement un « groupe d’achat ». Le marketing traditionnel basé sur les leads traite chaque personne indépendamment, ce qui néglige le signal essentiel de savoir si la bonne combinaison de rôles au sein d’un compte est engagée et prête à acheter.

Le marketing de groupe et la gestion de parcours permettent d&#39;y remédier en déplaçant l&#39;unité d&#39;orchestration des prospects individuels vers les comptes et les groupes d&#39;achats. Le modèle permet aux spécialistes du marketing B2B de définir les intérêts de la solution (les produits ou services vendus), de créer des modèles de groupe d’achat qui spécifient les rôles nécessaires à une décision d’achat, de qualifier les prospects entrants par rapport à ces rôles, de noter l’engagement au niveau du groupe d’achat et d’orchestrer des parcours de compte qui répondent aux signaux d’exhaustivité et de préparation du groupe d’achat.

Le résultat escompté est l’amélioration de la qualité et de la vitesse du pipeline : le marketing ne livre les comptes aux ventes que lorsque les bonnes personnes au sein du compte sont engagées et que le groupe d’achat est suffisamment complet, ce qui réduit les efforts de vente gaspillés et accélère la progression de l’affaire.

## Objectifs commerciaux clés

Ce modèle de cas d’utilisation prend en charge les objectifs commerciaux suivants.

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé.

**KPI :** conversion de lead, conversion de prospect/lead, efficacité

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Augmenter la génération de leads

Générer davantage de leads qualifiés pour le pipeline de vente par le biais de formulaires, d’événements, de contenu et d’engagements multicanaux.

**KPI :** prospects, coût par lead, conversion de lead

[En savoir plus sur l’augmentation de la génération de pistes](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Augmenter le chiffre d’affaires et les ventes

Stimuler la croissance du chiffre d’affaires de premier plan grâce à des canaux numériques, des campagnes et des parcours client optimisés.

**KPI :** croissance du chiffre d’affaires, vitesse du pipeline, taux de conclusion des affaires

[En savoir plus sur l’augmentation des recettes et des ventes](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des scénarios spécifiques où ce modèle peut être appliqué.

- **Qualification de groupe d’achats spécifique à une solution** — Définissez des groupes d’achats pour chaque ligne de produits (par exemple, « Enterprise CRM », « Data Platform », « Security Suite ») avec des modèles de rôle spécifiant les rôles requis (acheteur économique, évaluateur technique, champion, utilisateur final) et qualifiez les prospects provenant du système de gestion de la relation client et d’automatisation du marketing par rapport à ces rôles.
- parcours de compte pour l’accélération du pipeline **— Orchestrez un parcours de compte à plusieurs étapes qui envoie des e-mails de suivi ciblés aux rôles sous-engagés au sein d’un groupe d’achats, déclenche des alertes de ventes lorsque les seuils d’engagement sont atteints et fait passer le compte à une étape prête pour les ventes.**
- **Campagnes d&#39;exhaustivité du groupe d&#39;achat** — Identifiez les comptes où les groupes d&#39;achat ont des rôles manquants (par exemple, aucun acheteur économique identifié) et lancez des campagnes d&#39;acquisition ciblées pour engager les bonnes personnes au sein de ces comptes.
- parcours de comptes de ventes croisées **— Une fois la transaction initiale conclue, créez de nouveaux groupes d&#39;achat pour des intérêts de solution complémentaires et orchestrez des parcours de comptes qui favorisent l&#39;expansion du comité d&#39;achat.**
- **Réengagement pour les affaires bloquées** — Détectez les comptes où les scores d’engagement du groupe d’achat ont diminué et déclenchez des parcours de réengagement avec du contenu récent, des activités de sensibilisation des dirigeants ou des invitations à des événements.
- **Alignement des ventes et du marketing grâce à des informations CRM** — Affichez le statut du groupe d’achats, les données d’engagement et la progression du parcours de compte directement dans [!DNL Salesforce] ou [!DNL Dynamics 365] afin que les représentants commerciaux aient une visibilité en temps réel sur les comptes qualifiés pour le marketing.
- **Mises à jour des groupes d’achats pilotés par les événements** — Mettez automatiquement à jour les scores d’appartenance et d’engagement des groupes d’achats lorsque les prospects assistent à des webinaires, téléchargent des livres blancs, consultent des pages de tarification ou demandent des démonstrations.
- **Coordination de comptes multi-régions** — Gérez les groupes d&#39;achats sur les comptes mondiaux où différents contacts régionaux ont des rôles différents, unifiant la notation de l&#39;engagement entre les zones géographiques.

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux de complétion du groupe d&#39;achat | Pourcentage de groupes d&#39;achats dont tous les rôles requis sont remplis | Tableaux de bord [!DNL AJO B2B] Analytics : suivre la couverture des rôles par groupe d’achats |
| Score d&#39;engagement du groupe d&#39;achat | Score d’engagement agrégé de tous les membres d’un groupe d’achat | Score de l’engagement [!DNL AJO B2B] : scores au niveau de la personne cumulés dans le groupe d’achat |
| Taux de compte qualifié marketing (MQA) | Pourcentage de comptes qui atteignent le seuil qualifié marketing | Critères de sortie du parcours de comptes : comptes passant à l’étape Prêt pour la vente |
| Vitesse du pipeline | Temps moyen entre la création du groupe d&#39;achat et l&#39;opportunité qualifiée pour la vente | Intégration CRM : suivi des transitions d’étape du pipeline [!DNL AJO B2B] vers CRM |
| Taux de qualification du groupe lead-acheteur | Pourcentage de leads qualifiés pour des rôles de groupe d&#39;achat | [!DNL AJO B2B] Gestion de groupe d&#39;achat : ratio de leads qualifiés par rapport aux leads non qualifiés |
| Taux de réponse aux alertes de ventes | Pourcentage d’alertes de ventes qui entraînent une activité de suivi des ventes | CRM Sales Insights : suivi de la conversion alerte-activité |
| Taux d’achèvement du Parcours de compte | Pourcentage de comptes qui terminent le chemin de parcours prévu | Tableaux de bord [!DNL AJO B2B] Analytics : mesures d’achèvement du parcours |
| Taux D’Engagement Des E-Mails (B2B) | Taux d’ouverture et de clic publicitaire pour les e-mails d’éducation B2B | Création de rapports [!DNL AJO B2B] : diffusion d’e-mails et mesures d’engagement |

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — Orchestre les parcours au niveau du compte, gère les groupes d&#39;achats avec des modèles de rôle et des centres d&#39;intérêt pour les solutions, note l&#39;engagement au niveau de la personne et du groupe d&#39;achats, crée du contenu d&#39;e-mail B2B, envoie des SMS, configure des alertes de ventes et fournit des tableaux de bord d&#39;analyse B2B.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** : unifie les profils de compte à partir de données B2B inter-sources, résout les relations personne à compte, évalue les audiences au niveau du compte, configure les destinations spécifiques au B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) et applique la gouvernance des données sur les données B2B.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les applications et fonctionnalités référencées dans ce guide.

### [!DNL AJO B2B Edition]

- [Accueil de la documentation d’AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Présentation des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Centres d’intérêt des solutions](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modèles de rôle](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Créer des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Étapes du groupe d’achat](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Présentation des parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nœuds de parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [E-mails d’alerte commerciale](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Informations sur les ventes CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### E-mail et contenu B2B

- [Création d’e-mails B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Création de SMS dans AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistant AI pour la création d’e-mails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Analyses et tableaux de bord B2B

- [Tableau de bord des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Tableau de bord de l’engagement](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Tableau de bord intelligent](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [Présentation de RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Connecteur source Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Base des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Vue d’ensemble des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Gouvernance et confidentialité des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinations

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Garde-fous

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutoriels et prise en main

- [Prise en main d’AJO B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Tutoriel sur RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
