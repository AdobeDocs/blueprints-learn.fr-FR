---
title: Transfert d’événement
description: Découvrez comment transférer des données d’événement en temps réel collectées via Edge Network vers des destinations autres qu’Adobe à des fins d’analyse, de stockage ou de publicité.
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# Transfert d’événement

Ce guide décrit le modèle de cas d’utilisation du transfert d’événement, qui utilise le traitement côté serveur sur [!DNL Adobe Experience Platform] Edge Network pour distribuer des données d’événement en temps réel à des destinations non Adobe, telles que des plateformes d’analyse tierces, des points d’entrée d’espace de stockage dans le cloud, des réseaux publicitaires ou des webhooks personnalisés. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

## Modèle de cas d’utilisation

Cette section décrit le modèle et le plan d’exécution utilisés pour implémenter le transfert d’événement.

**Transfert d’événement** — Transférez les données d’événement en temps réel collectées via Edge Network vers des destinations autres qu’Adobe à des fins d’analyse, de stockage ou de publicité.

**Plan d’exécution :** Configuration du flux de données > Définition de règle d’événement > Mappage de destination > Transfert de l’exécution > Surveillance

## Présentation du cas d’utilisation

Les entreprises qui collectent des données comportementales par le biais de [!DNL Adobe Experience Platform] Web SDK, Mobile SDK ou de l’API Server doivent souvent partager le même flux d’événement avec des systèmes non Adobe : plateformes d’analyse telles que [!DNL Google Analytics] ou [!DNL Snowflake], réseaux publicitaires pour le suivi des conversions, entrepôts de données pour le stockage à long terme ou services internes personnalisés. Traditionnellement, cela nécessitait une prolifération des balises côté client, ce qui augmente le poids de la page, introduit une latence et crée des risques en matière de confidentialité et de gouvernance.

Le transfert d’événement résout ce problème en opérant côté serveur sur Edge Network. Lorsqu’une interaction d’un visiteur déclenche un événement via le Web SDK ou l’API du serveur, cet événement est acheminé vers Edge Network par le biais d’un flux de données. Les règles de transfert d’événement, configurées dans une propriété de transfert d’événement dédiée, évaluent les données d’événement entrantes et les transfèrent de manière sélective vers une ou plusieurs destinations configurées. Cette approche côté serveur réduit la surcharge des balises côté client, améliore les performances de la page, centralise la gouvernance des données et donne à l’entreprise le contrôle sur les données qui quittent exactement l’écosystème Adobe.

L’audience cible de ce modèle comprend les organisations qui ont déjà déployé (ou prévoient de déployer) l’API [!DNL Adobe Experience Platform] Web SDK ou Server pour la collecte de données et qui souhaitent étendre cet investissement en distribuant des données d’événement aux points d’entrée autres qu’Adobe sans ajouter de balises JavaScript côté client.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Améliorer la qualité et la gouvernance des données

Garantissez des données propres, complètes et conformes pour un ciblage précis, une réduction des déchets et des analyses fiables. Le transfert d’événement centralise la distribution des données côté serveur, ce qui permet à l’organisation de disposer d’un point de contrôle unique pour les données partagées avec des systèmes externes, ce qui réduit le risque de fuite de données et garantit l’application de politiques de gouvernance avant que les données ne quittent [!DNL Adobe] Edge Network.

**KPI : efficacité** économies

Pour plus d’informations, voir [Améliorer la qualité et la gouvernance des données](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolider et moderniser la technologie marketing

Réduisez la fragmentation des outils et la dette technique en migrant vers des plateformes unifiées et évolutives. Le transfert d’événement permet aux entreprises de remplacer plusieurs balises de fournisseur côté client par un seul mécanisme de distribution de données côté serveur, ce qui réduit la surcharge de chargement des pages et simplifie la pile technologique.

**KPI :** des économies, efficacité, rapidité de mise sur le marché

Pour plus d’informations, voir [Consolider et moderniser la technologie marketing](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des scénarios tactiques courants où s’applique ce modèle de cas d’utilisation.

- **Enrichissement d’analyses tierces** — Transférez les événements de page vue, de clic et de conversion vers [!DNL Google Analytics], [!DNL Snowflake] ou d’autres plateformes d’analyse en temps réel sans ajouter de balises côté client
- **Suivi des conversions Advertising** — Envoyez des événements d’achat et de génération de piste à l’API, à l’[!DNL Google Ads], à l’[!DNL TikTok] ou à l’[!DNL Snap] de [!DNL Meta] Conversions pour la mesure et l’optimisation des conversions côté serveur
- **Diffusion en continu de Data Warehouse** - Acheminez les données brutes des événements vers un entrepôt de données cloud ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) pour un stockage à long terme et une analyse hors ligne
- **Intégration webhook personnalisée** - Transférez les données d’événement filtrées ou transformées vers des microservices internes, des systèmes CRM ou des plateformes partenaires via des points d’entrée HTTP
- **Réduction des balises et amélioration des performances des pages** — Remplacez plusieurs balises JavaScript de fournisseur côté client par une seule implémentation de Web SDK, ainsi que des règles de transfert d’événement côté serveur, ce qui réduit le poids de la page et améliore Core Web Vitals
- **Partage de données conforme à la confidentialité** — Appliquez le filtrage des données et les règles de rédaction au niveau du champ côté serveur avant de partager des données d&#39;événement avec des tiers, en vous assurant que les informations d&#39;identification personnelles sont supprimées ou hachées avant d&#39;atteindre des systèmes externes
- **Distribution d’événements multi-cloud** - Transférez simultanément le même flux d’événements vers plusieurs destinations (par exemple, les analyses, la publicité et l’entrepôt de données) à partir d’un seul ensemble de règles côté serveur
- **Transfert de signaux de fraude en temps réel** — Transférer des événements de transaction de grande valeur à des systèmes de détection de fraude pour une évaluation des risques et des alertes en temps réel

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

- **Réduction du temps de chargement des pages** — Amélioration mesurée de la vitesse de chargement des pages et de Core Web Vitals après la migration des balises côté client vers le transfert d’événement côté serveur
- **Taux de succès de la diffusion des données** — Pourcentage d’événements transférés avec succès vers des points d’entrée de destination sans erreurs ni délais
- **Réduction du nombre de balises** — Nombre de balises fournisseur côté client supprimées après l’implémentation d’équivalents côté serveur
- **Actualisation des données/latence** — Temps écoulé entre l’occurrence de l’événement sur le client et l’arrivée de l’événement au point d’entrée de destination (cible : sous-seconde à secondes)
- **Taux de conformité de la gouvernance** — Pourcentage de partages de données sortantes qui passent par des règles de filtrage côté serveur, s’assurant qu’aucune PII ou donnée restreinte n’atteint des destinations non autorisées
- **Efficacité opérationnelle** — Réduction du temps consacré par les développeurs à la gestion des déploiements de balises côté client et à la résolution des conflits de balises

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Experience Platform](Edge Network)** : reçoit et achemine les données d’événement en temps réel depuis Web SDK, Mobile SDK ou l’API du serveur via les flux de données configurés
- **[!DNL Adobe Experience Platform](Transfert d’événement)** — Fournit le moteur de règles côté serveur pour évaluer, filtrer, transformer et transférer des données d’événement vers des destinations externes
- **[!DNL Adobe Experience Platform](Balises/Collecte de données)** — Gère le cycle de vie des propriétés de transfert d&#39;événement, les extensions, les règles et le workflow de publication

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les sujets abordés dans ce guide.

**Transfert d’événement**

- [Présentation du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Prise en main du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Surveillance du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Secrets de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Extensions de transfert d’événement**

- [Catalogue des extensions côté serveur](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Extension Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Extension de l’API de conversions Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Extension Google Cloud Platform](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Extension AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Extension Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Extension Google Ads Enhanced Conversions](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Extension Mailchimp](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Collecte de données et Edge Network**

- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation des flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Présentation des balises](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
