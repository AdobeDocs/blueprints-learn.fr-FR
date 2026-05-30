---
title: Audience Activation B2B
description: Découvrez comment activer les audiences B2B basées sur un compte sur les canaux web, e-mail et publicitaires.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 2%

---

# Activation des audiences B2B

Ce guide décrit le modèle de cas d’utilisation d’activation de l’audience B2B, qui utilise [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition pour créer, évaluer et activer des audiences au niveau du compte sur les canaux web, e-mail, publicitaires et CRM. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Ce modèle couvre le cycle de vie complet, de l’unification du profil de compte à l’évaluation et l’activation des audiences, en passant par les destinations spécifiques au B2B telles que les systèmes [!DNL Marketo Engage], [!DNL LinkedIn] et CRM.

## Modèle de cas d’utilisation

**Activation de l’audience B2B**

Activez les audiences B2B basées sur les comptes sur les canaux web, e-mail et publicitaires.

**Plan d’exécution :** Enrichissement du profil de compte > Évaluation de l’audience du compte > Configuration de la destination > Audience Activation > Surveillance

## Présentation du cas d’utilisation

Les équipes de marketing B2B doivent cibler et activer les audiences au niveau du compte plutôt qu’au niveau de la personne individuelle. Contrairement à l’activation d’audience B2C où l’unité de ciblage est un profil de consommateur unique, l’activation d’audience B2B nécessite de comprendre la relation entre les personnes et les comptes auxquels elles appartiennent, d’évaluer l’appartenance à l’audience en fonction des attributs au niveau du compte combinés à des signaux d’engagement au niveau de la personne, et de diffuser ces audiences vers des destinations qui prennent en charge le ciblage basé sur les comptes.

[!DNL RT-CDP] B2B edition étend la [!DNL Real-Time Customer Data Platform] standard avec des classes XDM spécialisées pour les comptes, les opportunités et les campagnes, ainsi que la résolution d’identité B2B qui mappe les relations personne-compte. Cela permet aux professionnels du marketing de créer des audiences de compte qui combinent des données thermographiques (secteur, chiffre d’affaires, nombre d’employés), des données technographiques (pile technologique, utilisation du produit) et des données comportementales (visites web, engagement par e-mail, présence à un événement) provenant des personnes associées à ces comptes.

Les audiences de compte activées alimentent les cas d’utilisation dans toute la funnel de génération de la demande : campagnes de sensibilisation en haut de funnel sur la publicité [!DNL LinkedIn] et display, programmes de culture mid-funnel en [!DNL Marketo Engage] et activation des ventes en bas de la funnel grâce à l’intégration de la gestion de la relation client (CRM). Les audiences de suppression de compte empêchent les dépenses inutiles en excluant les clients existants, les comptes fermés et perdus ou les comptes figurant déjà dans des cycles de vente actifs.

>[!NOTE]
>Si votre cas d’utilisation implique l’activation des audiences au niveau de la personne (B2C) plutôt qu’au niveau du compte, consultez la section [Activation des audiences vers les destinations](../audience-building-activation/audience-activation-to-destinations.md). Ce modèle utilise le modèle de données RT-CDP standard et ne nécessite pas B2B edition.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Augmenter la génération de leads

Générer davantage de leads qualifiés pour le pipeline de vente par le biais de formulaires, d’événements, de contenu et d’engagements multicanaux.

**KPI :** prospects, coût par lead, conversion de lead

[En savoir plus sur l’augmentation de la génération de pistes](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé.

**KPI :** conversion de lead, conversion de prospect/lead, efficacité

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace.

**KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels

[En savoir plus sur l’optimisation des dépenses marketing et du retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Publicité basée sur un compte sur[!DNL LinkedIn]** — Ciblez les comptes correspondant à votre profil client idéal (ICP) avec du contenu sponsorisé et des campagnes InMail sur [!DNL LinkedIn], à l’aide des listes de comptes activées depuis [!DNL RT-CDP] B2B edition
- **[!DNL Marketo Engage]le ciblage du programme d’éducation** — Activez les audiences de compte pour [!DNL Marketo Engage] à inscrire les prospects et les contacts associés aux flux d’éducation ciblés en fonction des critères de qualification au niveau du compte
- **Synchronisation des listes de comptes CRM** — Intégrez les listes de comptes qualifiés à [!DNL Salesforce] ou à [!DNL Microsoft Dynamics] pour la visibilité de l&#39;équipe des ventes, l&#39;affectation des territoires et les workflows de prospection sortante
- **Suppression de compte pour les médias achetés** — Supprimez les clients existants, les comptes clôturés ou les comptes des cycles de vente actifs des campagnes d’acquisition payantes afin de réduire les dépenses inutiles
- **Ciblage de compte basé sur l’intention** — Combinez les signaux d’intention tiers aux données d’engagement propriétaires au niveau du compte pour identifier et activer les audiences des comptes du marché
- **Vente croisée de produits à des comptes existants** — Créez des audiences de comptes en utilisant une ligne de produits, mais pas une autre, puis activez les canaux e-mail et publicitaires pour les campagnes de vente croisée
- **Ciblage des événements et des webinaires** — Activez les audiences de compte pour les canaux publicité et e-mail afin de générer l’enregistrement d’événements à partir des comptes cibles
- **Campagnes de déplacement compétitif** — Ciblez les comptes à l’aide de produits concurrents avec des messages personnalisés activés par le biais de canaux publicitaires et de messagerie électronique
- **Engagement de compte à plusieurs niveaux** : segmentez les comptes en niveaux d’engagement (élevé, moyen, faible) en fonction de l’activité agrégée au niveau de la personne et activez des campagnes différenciées pour chaque niveau
- **Audiences de co-marketing partenaires** — Partagez des segments d’audience de compte avec des partenaires de canal ou des programmes de co-marketing via des destinations de stockage dans le cloud

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Account Reach | Nombre de comptes cibles atteints sur les canaux d’activation | Suivi des comptes uniques activés par destination |
| Taux d’engagement du compte | Pourcentage de comptes activés affichant des signaux d’engagement | Mesurer l’engagement au niveau de la personne agrégé au compte |
| Influence sur le pipeline | Pipeline de revenus attribué aux campagnes d’activation basées sur les comptes | Suivre les opportunités créées à partir des audiences de compte activées |
| Coût par compte engagé | Dépenses marketing divisées par le nombre de comptes montrant l’engagement | Calculer les coûts sur l’ensemble des canaux publicitaires et de messagerie |
| Taux de conversion des leads | Pourcentage de leads provenant de comptes activés qui sont convertis en opportunités | Suivre la conversion de lead à opportunité pour les audiences activées |
| Économies réalisées lors de la suppression de l’audience | Coût évité en supprimant les comptes inéligibles des campagnes payantes | Mesurer la réduction des dépenses à partir des audiences de suppression |
| Couverture du compte | Pourcentage du marché adressable total (TAM) couvert par les audiences activées | Comparer les comptes activés à l&#39;univers ICP total |

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Real-Time CDP]B2B edition** : plateforme principale pour l’unification des profils de compte, la résolution des identités B2B, l’évaluation des audiences de compte, la configuration de destination spécifique au B2B et l’activation des audiences de compte
- **[!DNL Adobe Experience Platform] (AEP)** : infrastructure de base pour la modélisation des données XDM B2B, l’ingestion des données à partir de sources d’automatisation CRM et marketing, le service d’identités et la gouvernance
- **[!DNL Marketo Engage]** : destination d’automatisation du marketing B2B Principal pour les programmes de formation des prospects, la notation et l’exécution de campagnes alimentés par des audiences de compte activées

## Documentation connexe

Les ressources suivantes fournissent un contexte supplémentaire et des conseils détaillés pour les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

**[!DNL RT-CDP]B2B edition**

- [Présentation de Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b)
- [Audiences de compte](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/types/account-audiences)
- [Description du produit RT-CDP B2B edition](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Évaluation et segmentation des audiences**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Composition de l’audience](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)

**Destinations et activation**

- [Aperçu des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/overview)
- [Destination Marketo Engage](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destination Salesforce CRM](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destination Microsoft Dynamics 365](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Destination Amazon S3](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations par lots](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/guardrails)

**Sources de données et connecteurs**

- [Vue d’ensemble des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)
- [Connecteur Marketo Engage](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connecteur Salesforce](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/crm/salesforce)

**Modélisation des données et identité**

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation du profil](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)

**Gouvernance et confidentialité des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Surveillance et observabilité**

- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)
- [Surveillance des flux de données de destination](https://experienceleague.adobe.com/fr/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Surveiller les flux de données sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/api-tutorials/monitor)
- [Tableau de bord d’utilisation des licences](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Rapports et analyses**

- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation des connexions](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/overview)
- [Présentation des vues de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutoriels et guides**

- [Prise en main de Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Création d’un schéma pour les sources B2B](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b)
- [Outil Sandbox](https://experienceleague.adobe.com/fr/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
