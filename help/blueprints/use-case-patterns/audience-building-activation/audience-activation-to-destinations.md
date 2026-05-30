---
title: Activation de l’audience vers les destinations
description: Découvrez comment évaluer et publier des segments d’audience vers des destinations externes à des fins de ciblage ou de suppression à l’aide d’Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 4%

---

# Activation de l’audience vers les destinations

Ce guide décrit le modèle de cas d’utilisation de l’activation de l’audience vers les destinations , qui évalue les segments d’audience dans Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) et les publie sur des plateformes publicitaires, un espace de stockage dans le cloud, des systèmes de gestion de la relation client ou des partenaires de données pour le ciblage, la suppression, la modélisation semblable ou l’enrichissement des analyses. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Ce modèle couvre le cycle de vie complet de l’activation des audiences, depuis la définition et l’évaluation des segments d’audience jusqu’à la surveillance de l’intégrité de l’activation et l’application de la conformité de la gouvernance, en passant par la configuration des connexions de destination et la publication des audiences.

## Modèle de cas d’utilisation

**Audience Activation vers les destinations** — Évaluez et publiez un segment ciblé vers des destinations externes à des fins de ciblage ou de suppression.

**Plan d’exécution :** Évaluation d’audience > Configuration de la destination > Audience Activation > Surveillance

## Présentation du cas d’utilisation

Les entreprises ont besoin de diffuser des données d’audience vers des systèmes externes pour alimenter des campagnes multimédia payantes, enrichir les enregistrements CRM, partager des données avec des partenaires ou alimenter des analyses en aval. Audience Activation vers les destinations est le modèle d’activation fondamental de RT-CDP : il évalue les profils qui remplissent les critères d’une audience cible, se connecte à une ou plusieurs destinations externes, mappe les attributs de profil aux champs spécifiques à la destination et publie l’audience pour la consommation en aval.

Ce modèle s’applique chaque fois que l’objectif est d’envoyer les données d’audience à un système externe dans le bon format au bon moment. Il n’implique pas de diffusion de messages, de personnalisation sur site ou d’analyse. Il s’agit du point de départ le plus courant pour les implémentations de RT-CDP et sert de bloc de création que d’autres modèles complètent.

Les parties prenantes incluent généralement les équipes de marketing numérique qui gèrent les médias achetés, les équipes de données qui enrichissent les entrepôts, les équipes de gestion de la relation client qui préparent les listes de contacts pour les campagnes et les équipes de confidentialité qui assurent la conformité de la gouvernance sur les flux de données sortants.

>[!NOTE]
>Si votre organisation utilise [!DNL Real-Time CDP] B2B edition et active les audiences vers des destinations basées sur un compte, voir [Activation des audiences B2B](../b2b/account-audience-activation.md). Ce modèle partage les mêmes mécanismes d’activation, mais utilise un modèle de données compte-personne B2B et nécessite la licence B2B edition.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Réduire le coût d’acquisition du client

Améliorez l’efficacité du ciblage, supprimez les clients existants des campagnes d’acquisition et optimisez les dépenses multimédia.

**KPI :** coût d’acquisition client, coût par lead, efficacité

[En savoir plus sur la réduction du coût d’acquisition des clients](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace.

**KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels

[En savoir plus sur l’optimisation des dépenses marketing et du retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

- **Ciblage des audiences de plateforme publicitaire** — Envoyez les segments qualifiés par push aux plateformes de médias payants pour le ciblage des campagnes
- **Suppression payante des médias des clients existants** — Excluez les clients connus des campagnes d’acquisition sur les plateformes publicitaires afin d’éliminer le gaspillage
- **Audiences de contrôle semblables** — Intégrez les segments clients à forte valeur ajoutée à Facebook, Google Ads ou The Trade Desk en tant qu’audiences de contrôle pour le développement semblables
- **Synchronisation CRM pour l’activation des ventes** — Activez les audiences à forte intention ou à forte valeur afin que les équipes commerciales puissent donner la priorité à la sensibilisation.
- **Partage d’audiences des partenaires de données** — Partagez des segments d’audience qualifiés avec des partenaires de données pour le ciblage ou la mesure de coopération
- **Exportation de l’espace de stockage pour l’enrichissement de l’entrepôt de données** — Exportez les attributs d’appartenance et de profil de l’audience vers Amazon S3, Azure Blob, Google Cloud Storage ou SFTP pour les analyses en aval
- **Activation du reciblage d’audience** — Activez les visiteurs du site qui n’ont pas effectué de conversion vers des plateformes de reciblage
- **Synchronisation de la liste de contacts avec les fournisseurs de services de messagerie** — Intégrer l’appartenance de l’audience aux plateformes de messagerie tierces pour une diffusion coordonnée

## Indicateurs clés de performance

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Coût d’acquisition client (CAC) | Coût d’acquisition d’un nouveau client via des audiences activées | Total des dépenses média / nouveaux clients attribués aux audiences activées |
| Taux de correspondance d’audience | Pourcentage de profils activés correspondant avec succès à la destination | Profils correspondants à la destination / profils exportés depuis RT-CDP |
| Économies de suppression | Dépenses de médias évitées en supprimant les clients existants des campagnes d’acquisition | CPM estimée x taille d’audience supprimée |
| Taux De Diffusion D’Activation | Pourcentage de profils envoyés avec succès à la destination | Profils diffusés / profils dans l’audience source |
| Délai d’activation | Temps écoulé entre la définition de l’audience et la première diffusion à la destination | Mesure de la création du segment à la première exécution confirmée du flux de données |
| Précision de la population d’audience | Alignement entre les tailles d’audience attendue et réelle au niveau de la destination | Nombre de profils des audiences de destination/nombre de profils des audiences RT-CDP |

## Applications

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — Évaluation de l’audience, gestion de la destination, activation de l’audience, consentement et application de la gouvernance
- **Adobe [!DNL Experience Platform] (AEP)** — Banque de profils, service d’identités, moteur de segmentation, gouvernance des données

## Architecture

L’architecture de référence suivante illustre la manière dont les données d’audience et de profil circulent de Real-Time CDP vers les destinations d’entreprise, y compris l’espace de stockage, les points d’entrée de flux continu et les applications SaaS.

![Architecture de référence pour l’activation des audiences et des profils vers les destinations d’entreprise](/help/blueprints/audience-activation/assets/known_activation.png)

## Documentation connexe

**Destinations**

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations d’exportation de profils par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activer les audiences à la demande vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Mécanismes de sécurisation des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Présentation de Destination SDK](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/overview)

**Audiences et segmentation**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Identité et profil**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Modélisation des données et schémas**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Gouvernance des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Politiques de gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [Application des politiques](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Surveillance et observabilité**

- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Tableau de bord d’utilisation des licences](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Attributs calculés**

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**Collecte de données et sources**

- [Vue d’ensemble des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**Administration**

- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)
- [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Contrôle d’accès basé sur les attributs](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**Mécanismes de sécurisation**

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
