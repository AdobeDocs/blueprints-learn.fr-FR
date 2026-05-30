---
title: Expérience de conversation Brand Concierge
description: Découvrez comment transformer les propriétés numériques en expériences de conversation optimisées par l’IA et sécurisées par la marque qui guident la découverte des clients.
solution: Experience Platform, Real-Time Customer Data Platform
exl-id: a9545328-316d-446a-9308-18af61c58d1c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 1%

---

# Expérience de conversation Brand Concierge

Ce guide présente les expériences conversationnelles optimisées par l’IA utilisant [!DNL Adobe Brand Concierge], intégré à [!DNL Adobe Experience Platform] (AEP) et [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de déployer des agents de conversation sécurisés par la marque sur des propriétés numériques.

[!DNL Brand Concierge] permet aux marques de déployer des agents conversationnels intelligents qui comprennent la voix de la marque, d&#39;accéder à des catalogues de produits et à du contenu approuvés, de fournir des recommandations personnalisées basées sur des données de profil en temps réel et de capturer des signaux d&#39;intention et de sentiment dans le profil client unifié. Le résultat est une expérience de conversation qui semble naturelle et sur la marque tout en enrichissant la compréhension de chaque client par l&#39;organisation.

## Modèle de cas d’utilisation

**Expérience de conversation**

Transformez les propriétés numériques en expériences conversationnelles sécurisées, optimisées par l’IA, qui guident la découverte des clients par le biais d’un dialogue naturel, enrichissent les profils avec des signaux d’intention et de sentiment et fournissent des recommandations de produits personnalisées.

**Plan d’exécution :** Configuration de l’agent > Configuration de la gouvernance de marque > Intégration de contenu > Déploiement de l’expérience de conversation > Enrichissement du profil > Analyses et optimisation

## Présentation du cas d’utilisation

Les entreprises cherchent de plus en plus à transformer les expériences digitales statiques en conversations dynamiques basées sur l’IA qui guident les clients tout au long de la découverte, de la sélection de produits et des décisions d’achat. [!DNL Adobe Brand Concierge] résout ce problème en fournissant une couche d’IA conversationnelle orchestrée qui se trouve au-dessus des propriétés numériques existantes, optimisées par AEP Agent Orchestrator.

Ce modèle se distingue des implémentations de chatbot traditionnelles, car il est nativement intégré au profil unifié d’AEP, utilise des mécanismes de sécurisation de la gouvernance de marque pour s’assurer que chaque réponse s’aligne sur les normes de la marque et renvoie des signaux de conversation à la plateforme de données client pour la personnalisation et l’activation en aval.

Le public cible comprend des équipes d’expérience digitale, des gestionnaires d’e-commerce, des stratèges de contenu et des technologues marketing qui doivent déployer des expériences de conversation intelligentes qui stimulent l’engagement, la conversion et l’enrichissement des profils.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Offrir des expériences personnalisées aux clients

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

[En savoir plus sur la diffusion d’expériences client personnalisées](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Améliorer l’engagement client

Augmentez la fréquence et la profondeur des interactions sur tous les points de contact numériques et physiques.

**KPI :** Engagement, Temps passé sur la page (web), Taux d’ouverture

[En savoir plus sur l’amélioration de l’engagement client](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Augmentation des taux de conversion

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

**KPI :** taux de conversion, conversion de lead, coût par lead

[En savoir plus sur l’augmentation des taux de conversion](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Assistant de découverte de produits** — Déployez un agent conversationnel sur les pages de liste des produits qui pose des questions de qualification et limite les recommandations de produits en fonction des besoins, des préférences et du budget des clients
- **Conseiller en comparaison guidé** — Aidez les clients à comparer les produits côte à côte grâce à un dialogue naturel, en mettant en évidence les différences pertinentes par rapport à leurs priorités déclarées
- **Concierge taille et ajustement** — Guidez les acheteurs de vêtements ou de chaussures en sélectionnant leur taille à l&#39;aide de questions-réponses conversationnelles, en réduisant les retours et en augmentant la confiance d&#39;achat
- **Sélecteur d’abonnement ou de formule** : guide les clients à travers les options de niveau de service ou de formule d’abonnement avec des recommandations personnalisées basées sur les schémas d’utilisation et les besoins déclarés
- **Assistant de navigation de site** — Aidez les visiteurs à trouver du contenu, des ressources d’assistance ou des catégories de produits pertinents en fonction de l’intention déclarée, ce qui réduit les taux de rebond sur les sites complexes
- **Consultation avant l&#39;achat** — Fournissez des conseils d&#39;achat à haute considération (par exemple, produits électroniques, produits financiers, assurance) par le biais de conversations à plusieurs tours qui permettent d&#39;élaborer une recommandation
- **Concierge du programme de fidélité** — Aidez les membres du programme de fidélité à découvrir les récompenses, à comprendre les avantages de niveau et à trouver des opportunités de rachat grâce à une interaction conversationnelle
- **Conversation de réengagement** — Lancez une conversation proactive avec les visiteurs récurrents en fonction de l’historique de navigation précédent ou des éléments de panier abandonnés
- **Escalade de l’agent en direct avec contexte** - Transmettez facilement les demandes complexes aux agents commerciaux ou de support en direct tout en préservant le contexte de conversation complet et les données de profil client
- **Assistance après achat et montée en gamme** — Contactez les clients après achat avec une assistance à la configuration, des suggestions de produits complémentaires et des bilans de satisfaction par le biais de canaux de conversation

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’engagement des conversations | Pourcentage de visiteurs et visiteuses qui engagent et soutiennent une conversation | Conversations lancées / pages vues éligibles |
| Taux d’achèvement de la conversation | Pourcentage de conversations qui parviennent à une résolution significative | Conversations terminées / conversations démarrées |
| Taux de conversion de conversation | Pourcentage de conversations qui mènent à une action souhaitée (achat, inscription, formulaire de prospect) | Conversions de la conversation / total des conversations |
| Profondeur de conversation moyenne | Nombre de tours par conversation, indiquant la qualité de l’engagement | Nombre moyen de messages par session |
| Satisfaction du client (CSAT) | Score de satisfaction post-conversation à partir du retour d’expérience | Réponses à un questionnaire ou notes pouces vers le haut/bas |
| Taux d’acceptation des recommandations | Pourcentage de recommandations de produits acceptées ou ayant fait l’objet d’un clic | Recommandations suivies / recommandations diffusées |
| Taux de remise de l’agent actif | Pourcentage de conversations redirigées vers des agents en direct | Remises / total des conversations |
| Taux d’enrichissement du profil | Pourcentage de conversations qui génèrent de nouveaux signaux d’intention ou de préférence | Profils enrichis / total des conversations |
| Chiffre d’affaires influencé par la conversation | Chiffre d’affaires des achats pour lesquels une conversation [!DNL Brand Concierge] a précédé la conversion | Analyse de l’attribution sur les parcours de conversation-achat |
| Délai de résolution | Durée moyenne du début de la conversation à la résolution ou à la remise | Analyse de l’horodatage pour les événements de conversation |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Brand Concierge]** : application d’expérience de conversation optimisée par l’IA fournissant l’agent orchestrator, Product Advisor Agent, l’agent de conseil sur le site, la gouvernance de marque et l’analyse de conversation
- **[!DNL Adobe Experience Platform](AEP)** — Base de données unifiée fournissant des schémas XDM, la résolution d&#39;identité, des profils clients en temps réel et une infrastructure de collecte de données pour les signaux conversationnels
- **[!DNL Real-Time CDP]([!DNL RT-CDP])** — Plateforme de données client permettant la recherche de profils en temps réel pour des conversations personnalisées, la segmentation d&#39;audience à partir de signaux conversationnels et l&#39;enrichissement de profils avec des données d&#39;intention et de sentiment

## Documentation connexe

Pour obtenir des conseils sur la mise en œuvre et des informations supplémentaires, consultez la présentation de Brand Concierge [](https://experienceleague.adobe.com/en/docs/brand-concierge/content/documentation/overview) sur Adobe Experience League.
