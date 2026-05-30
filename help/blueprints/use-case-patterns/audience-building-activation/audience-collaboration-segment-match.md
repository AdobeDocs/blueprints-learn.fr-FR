---
title: Audience Collaboration
description: Découvrez comment partager et faire correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de la correspondance de segments.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 3%

---

# Audience Collaboration

Ce guide décrit le modèle de cas d’utilisation de la collaboration avec les audiences, qui utilise [!DNL Segment Match] dans [!DNL Real-Time CDP] et [!DNL Adobe Experience Platform] pour partager et faire correspondre des segments d’audience dans des sandbox ou des organisations de manière à respecter la confidentialité. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

[!DNL Segment Match] permet à plusieurs organisations [!DNL Experience Platform] (ou sandbox au sein d’une organisation) de collaborer sur les données d’audience en partageant les informations d’appartenance à un segment sans exposer les informations d’identification personnelles sous-jacentes. Les participants peuvent estimer le chevauchement, partager des audiences et activer les profils correspondants vers des destinations en aval.

## Modèle de cas d’utilisation

Ce cas d’utilisation suit le modèle d’Audience Collaboration.

Partagez et faites correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de [!DNL Segment Match].

**Plan d’exécution : sélection de segments** > Configuration des correspondances > Estimation des chevauchements > Partage d’audience > Activation

## Présentation du cas d’utilisation

Les entreprises doivent de plus en plus collaborer sur les données d’audience avec des partenaires, des filiales ou plusieurs unités opérationnelles tout en maintenant des contrôles stricts de la confidentialité. La collaboration avec les audiences répond à ce besoin en activant le partage de segments sécurisé par le biais de [!DNL Segment Match], une fonctionnalité de [!DNL Real-Time CDP] qui permet à deux organisations [!DNL Experience Platform] ou plus (ou sandbox) d’échanger des informations sur l’appartenance à une audience à l’aide d’identifiants hachés et sécurisés pour la confidentialité.

Le scénario commercial implique généralement une organisation (l’expéditeur) qui a créé un segment d’audience utile et souhaite le partager avec une organisation partenaire (le destinataire) à des fins de ciblage, de suppression ou d’enrichissement communs. Avant de partager, les deux parties peuvent estimer le chevauchement des audiences pour en évaluer la valeur. Une fois partagée, l’organisation de réception peut activer l’audience correspondante par l’intermédiaire de ses propres destinations.

Ce modèle est distinct de l’activation d’audience standard, car il fonctionne entre des organisations ou des sandbox plutôt qu’avec des destinations publicitaires ou marketing externes. Il se distingue également des salles blanches de données ou des plateformes de collaboration tierces, car il fonctionne en mode natif dans l’écosystème Adobe à l’aide d’une infrastructure d’identités [!DNL Experience Platform].

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés. La collaboration avec les audiences permet aux entreprises de découvrir de nouveaux pools de prospects en comparant leurs segments aux audiences de partenaires, en identifiant les chevauchements à forte valeur ajoutée et en atteignant de nouveaux clients par le biais d’une activation conjointe.

- **KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads
- [Acquérir de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Réduire le coût d’acquisition du client

Améliorez l’efficacité du ciblage, supprimez les clients existants des campagnes d’acquisition et optimisez les dépenses multimédia. En partageant les segments de suppression entre les organisations ou les unités commerciales, les équipes peuvent éviter les dépenses inutiles sur des clients déjà convertis et concentrer les budgets sur des prospects réellement nouveaux.

- **KPI :** coût d’acquisition client, coût par lead, efficacité
- [Réduire le coût d’acquisition du client](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace. [!DNL Segment Match] permet la suppression des audiences entre organisations et le ciblage conjoint, ce qui réduit la duplication et améliore la précision.

- **KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels
- [Optimiser les dépenses marketing et le retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

- **Correspondance entre l’éditeur et l’annonceur et l’audience** — Une marque partage son segment client à forte valeur ajoutée avec un éditeur de médias afin d’estimer le chevauchement et de cibler les utilisateurs appariés avec des annonces personnalisées, ce qui améliore la pertinence de la campagne sans exposer les informations d’identification personnelle.
- **Suppression intermarques au sein d’une société holding** — Plusieurs marques d’une organisation parent partagent des segments de clientèle afin de supprimer les clients existants de marques sœurs des campagnes d’acquisition, ce qui réduit le gaspillage des dépenses publicitaires.
- **Enrichissement de l’audience du réseau de médias de vente au détail** — Un retailer partage des segments basés sur les achats avec les partenaires de marque CPG, ce qui permet aux marques de cibler des acheteurs éprouvés sur le réseau de médias retailer avec des taux de conversion plus élevés.
- **Découverte d’audiences de partenaires de co-marketing** — Deux marques non concurrentes évaluent le chevauchement des audiences pour évaluer le potentiel du partenariat avant de lancer une campagne conjointe, en utilisant une estimation du chevauchement pour valider l’alignement des audiences.
- **Partage de segments coopératif de données** — Les organisations membres d’une coopérative de données partagent des segments d’audience hachés afin d’étendre la portée du ciblage tout en maintenant la conformité en matière de confidentialité et les contrôles de gouvernance des données.
- **Fédération d’audiences multi-sandbox** — Une entreprise mondiale partage des segments d’audience sur plusieurs sandbox régionaux afin de permettre un ciblage cohérent des clients sur l’ensemble des marchés tout en respectant les exigences régionales en matière de résidence des données.
- **Activation entre partenaires du programme de fidélité** — Une coalition de fidélité partage les segments de niveau de fidélité avec les commerçants participants afin que chaque partenaire puisse offrir des promotions adaptées au niveau à la base de clients partagée.
- **Collaboration en matière de mesure et d’attribution** — Un annonceur partage un segment de conversion avec un partenaire multimédia afin que ce dernier puisse mesurer l’efficacité de la campagne en comparant les utilisateurs exposés aux convertisseurs.

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer le succès des implémentations de collaboration avec les audiences.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux de chevauchement des audiences | Pourcentage de profils dans le segment partagé qui correspondent entre l’expéditeur et le destinataire | [!DNL Segment Match] rapport d’estimation de chevauchement |
| Taille d’audience correspondante | Nombre de profils correspondants et disponibles pour l’activation | Statut du partage de [!DNL Segment Match] et nombre de populations de l’audience |
| Nouvelle acquisition de clients à partir des audiences correspondantes | Nouveaux clients acquis par le biais de campagnes ciblant les segments correspondants | Suivi des conversions sur les campagnes à l’aide d’audiences correspondantes |
| Réduction des coûts d&#39;acquisition client | Diminution du coût par acquisition lors de l’utilisation d’audiences appariées par rapport au ciblage large | Analyse des coûts de campagne comparant les performances des audiences appariées aux performances inégalées |
| Économies de suppression | Économie de médias grâce à la suppression des clients connus des campagnes d’acquisition | Comparaison des dépenses des médias avant et après la suppression |
| Effet élévateur des performances de Campaign | Amélioration du taux de conversion, du taux de clics publicitaires ou de l’engagement pour les campagnes utilisant des audiences correspondantes | Test A/B comparant les campagnes d’audience correspondantes au contrôle |
| Délai jusqu’à Collaboration | Temps écoulé entre le lancement du partage de segment et la préparation à l’activation | [!DNL Segment Match] la date et l’heure du workflow |

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Real-Time CDP]** — Fournit la fonctionnalité [!DNL Segment Match] pour le partage d&#39;audience sécurisé par la confidentialité, l&#39;évaluation d&#39;audience pour la création de segments et l&#39;activation de destination pour l&#39;utilisation en aval des audiences correspondantes.
- **[!DNL Adobe Experience Platform]** : fournit l’infrastructure de données de base, notamment la résolution d’identité, l’unification des profils, la gouvernance des données et l’application du consentement dont [!DNL Segment Match] dépend.

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

### [!DNL Segment Match]

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Dépannage de la correspondance de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentation et audiences

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Application des politiques](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### Destinations et activation

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### Modélisation des données et schéma

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Administration et contrôle d’accès

- [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Surveillance et observabilité

- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Garde-fous

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Tutoriels

- [Créer un schéma](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Activer un jeu de données pour Profil](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
