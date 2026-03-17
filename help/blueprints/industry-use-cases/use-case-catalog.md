---
title: Catalogue de cas d’utilisation
description: Parcourez les cas d’utilisation du secteur par ordre vertical, niveau de maturité ou modèle d’implémentation pour trouver le bon point de départ pour votre parcours Adobe Experience Platform.
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# Catalogue des cas d’utilisation

Explorez les cas d’utilisation du secteur pour les [!DNL Adobe Experience Platform] et les applications. Parcourez les différents secteurs d’activité pour afficher les cas d’utilisation de votre infrastructure verticale, par niveau de maturité pour trouver le bon point de départ pour votre organisation ou par modèle de mise en œuvre pour comprendre quelle approche technique correspond à vos besoins.

Chaque cas d’utilisation renvoie à des conseils d’implémentation détaillés par le biais d’un modèle de cas d’utilisation, qui décrit la chaîne de fonction, les points de décision et les étapes de configuration nécessaires pour donner vie au cas d’utilisation.

## Parcourir par secteur

>[!BEGINTABS]

>[!TAB Vente au détail]

Les organisations de vente au détail utilisent [!DNL Adobe Experience Platform] pour unifier les données client des magasins en ligne, des emplacements physiques et des programmes de fidélité en une vue unique de chaque acheteur.

| | Cas d’utilisation | Description | Maturité | Modèle |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Recommandations de produits personnalisées" width="40"> | [Recommandations de produits personnalisées](retail/retail-overview.md#personalized-product-recommendations) | Afficher des produits personnalisés en fonction de l&#39;historique de navigation et d&#39;achat | [!BADGE Émergent]{type=Informative} | [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Panier abandonné" width="40"> | [Récupération d’e-mails de panier abandonné](retail/retail-overview.md#abandoned-cart-email-recovery) | Envoyer des rappels personnalisés pour les paniers abandonnés | [!BADGE Fondamental]{type=Neutral} | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgence du stock" width="40"> | [Campagnes d’urgence basées sur les stocks](retail/retail-overview.md#inventory-based-urgency-campaigns) | Déclencher des alertes en temps réel lorsque le stock de produits est faible | [!BADGE Fondamental]{type=Neutral} | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vente Croisée" width="40"> | [Recommandations relatives aux ventes croisées et aux ventes incitatives](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Afficher les produits de vente croisée et de montée en gamme pertinents au passage en caisse et dans les e-mails | [!BADGE Avancé]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Série de bienvenue" width="40"> | [Nouvelle série de bienvenue clients](retail/retail-overview.md#new-customer-welcome-series) | Automatisation d’une série de bienvenue comprenant plusieurs e-mails avec des recommandations personnalisées | [!BADGE Émergent]{type=Informative} | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Baisse De Prix" width="40"> | [Alertes de chute de prix](retail/retail-overview.md#price-drop-alerts) | Informer les clients de la chute du prix des articles mis en vente ou consultés | [!BADGE Fondamental]{type=Neutral} | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Réapprovisionnement" width="40"> | [Rappels de réapprovisionnement](retail/retail-overview.md#replenishment-reminders) | Envoyer des rappels automatisés pour les produits consommables achetés régulièrement | [!BADGE Émergent]{type=Informative} | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pages de catégorie" width="40"> | [Pages de catégorie personnalisées](retail/retail-overview.md#personalized-category-pages) | Réorganiser de manière dynamique les pages de catégories en fonction des préférences de chaque client | [!BADGE Émergent]{type=Informative} | [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-achat" width="40"> | [Campagnes De Suivi Après Achat](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Envoyer des conseils d’assistance, examiner les demandes et des suggestions de produits associées | [!BADGE Émergent]{type=Informative} | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Offres Exclusives Client VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Proposer des offres exclusives et un accès anticipé à des clients à forte valeur ajoutée | [!BADGE Avancé]{type=Caution} | [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [&#x200B; Notifications de rupture de stock &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Avertir les clients lorsque des produits en rupture de stock sont disponibles | [!BADGE Fondamental]{type=Neutral} | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Afficher des évaluations et des avis personnalisés en fonction du profil client | [!BADGE Émergent]{type=Informative} | [Web/App Personalization pour visiteurs connus](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Services financiers]

Les cas d’utilisation des services financiers seront bientôt disponibles. [Affichez les cas d’utilisation actuels de Financial Services](financial-services/financial-services-overview.md).

>[!TAB Santé]

Les cas d’utilisation des soins de santé seront bientôt disponibles. [Affichez les cas d’utilisation actuels de Healthcare](healthcare/healthcare-overview.md).

>[!TAB Automobile]

Des cas d’utilisation automobile seront bientôt disponibles. [Affichez les cas d’utilisation actuels du secteur Automobile](automotive/automotive-overview.md).

>[!TAB Voyage et hébergement]

Les cas d’utilisation Voyage et hébergement seront bientôt disponibles. [Affichez les cas d’utilisation actuels pour les voyages et l’hébergement](travel-hospitality/travel-hospitality-overview.md).

>[!TAB  Télécommunications ]

Les cas d’utilisation des télécommunications seront bientôt disponibles. [Affichez les cas d&#39;utilisation actuels des télécommunications](telecommunications/telecommunications-overview.md).

>[!TAB Médias et divertissement]

Les cas d’utilisation de Media &amp; Entertainment seront bientôt disponibles. [Affichez les cas d’utilisation actuels de Media &amp; Entertainment](media-entertainment/media-entertainment-overview.md).

>[!TAB Assurance]

Les cas d’utilisation d’assurance seront bientôt disponibles. [Affichez les cas d’utilisation d’assurance actuels](insurance/insurance-overview.md).

>[!TAB B2B]

Les cas d’utilisation B2B seront bientôt disponibles. [Affichez les cas d’utilisation B2B actuels](b2b/b2b-overview.md).

>[!ENDTABS]

## Parcourir par niveau de maturité

>[!BEGINTABS]

>[!TAB Fondamental]

Modèles de base éprouvés utilisant la diffusion sur un seul canal. Points de départ idéaux pour les organisations qui commencent leur parcours [!DNL Experience Platform].

| | Cas d’utilisation | Industrie | Impact commercial | Modèle |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Panier abandonné" width="40"> | [Récupération d’e-mails de panier abandonné](retail/retail-overview.md#abandoned-cart-email-recovery) | Grande distribution | Taux de récupération du panier de 25 à 35 % | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgence du stock" width="40"> | [Campagnes d’urgence basées sur les stocks](retail/retail-overview.md#inventory-based-urgency-campaigns) | Grande distribution | Augmentation de 30 à 40 % de la conversion | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Baisse De Prix" width="40"> | [Alertes de chute de prix](retail/retail-overview.md#price-drop-alerts) | Grande distribution | Taux de conversion de 20 à 30 % | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [&#x200B; Notifications de rupture de stock &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Grande distribution | Taux de conversion de 40 à 50 % | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB Émergent]

Modèles multicanaux et à plusieurs étapes qui s’appuient sur des fonctionnalités fondamentales avec une personnalisation et des parcours orchestrés pilotés par l’IA.

| | Cas d’utilisation | Industrie | Impact commercial | Modèle |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Recommandations de produit" width="40"> | [Recommandations de produits personnalisées](retail/retail-overview.md#personalized-product-recommendations) | Grande distribution | Augmentation de 20 à 30 % du taux de clics, effet élévateur de conversion de 15 à 25 % | [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pages de catégorie" width="40"> | [Pages de catégorie personnalisées](retail/retail-overview.md#personalized-category-pages) | Grande distribution | Augmentation de 25 à 35 % de l’engagement | [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Série de bienvenue" width="40"> | [Nouvelle série de bienvenue clients](retail/retail-overview.md#new-customer-welcome-series) | Grande distribution | Taux d’engagement de 40 à 50 % | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Réapprovisionnement" width="40"> | [Rappels de réapprovisionnement](retail/retail-overview.md#replenishment-reminders) | Grande distribution | Taux d’achat de répétition de 30 à 40 % | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-achat" width="40"> | [Campagnes De Suivi Après Achat](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Grande distribution | Taux de révision de 15 à 20 %, achats répétés de 10 à 15 % | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Grande distribution | Augmentation du taux de conversion de 10 à 15 % | [Web/App Personalization pour visiteurs connus](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Avancé]

Orchestration cross-canal avec prise de décision en temps réel et sélection d’offres basée sur l’IA pour les expériences client les plus sophistiquées.

| | Cas d’utilisation | Industrie | Impact commercial | Modèle |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vente Croisée" width="40"> | [Recommandations relatives aux ventes croisées et aux ventes incitatives](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Grande distribution | Augmentation de 25 $ à 75 $ du AOV, augmentation des revenus de 10 à 15 % | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [Offres Exclusives Client VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Grande distribution | Taux d’engagement de 50 à 70 % des VIP | [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## Parcourir par modèle d’implémentation

>[!BEGINTABS]

>[!TAB Gestion et orchestration des campagnes]

### Messagerie déclenchée par événement

Répondez aux événements comportementaux en temps réel avec des messages opportuns à canal unique.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Panier abandonné" width="40"> | [Récupération d’e-mails de panier abandonné](retail/retail-overview.md#abandoned-cart-email-recovery) | Grande distribution | [!BADGE Fondamental]{type=Neutral} | Taux de récupération du panier de 25 à 35 % |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Urgence du stock" width="40"> | [Campagnes d’urgence basées sur les stocks](retail/retail-overview.md#inventory-based-urgency-campaigns) | Grande distribution | [!BADGE Fondamental]{type=Neutral} | Augmentation de 30 à 40 % de la conversion |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Baisse De Prix" width="40"> | [Alertes de chute de prix](retail/retail-overview.md#price-drop-alerts) | Grande distribution | [!BADGE Fondamental]{type=Neutral} | Taux de conversion de 20 à 30 % |
| | [&#x200B; Notifications de rupture de stock &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Grande distribution | [!BADGE Fondamental]{type=Neutral} | Taux de conversion de 40 à 50 % |

### Parcours Orchestré À Plusieurs Étapes

Guidez les clients à travers des séquences multipoint qui s’adaptent en fonction de l’engagement et du comportement.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Série de bienvenue" width="40"> | [Nouvelle série de bienvenue clients](retail/retail-overview.md#new-customer-welcome-series) | Grande distribution | [!BADGE Émergent]{type=Informative} | Taux d’engagement de 40 à 50 % |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Réapprovisionnement" width="40"> | [Rappels de réapprovisionnement](retail/retail-overview.md#replenishment-reminders) | Grande distribution | [!BADGE Émergent]{type=Informative} | Taux d’achat de répétition de 30 à 40 % |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Post-achat" width="40"> | [Campagnes De Suivi Après Achat](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Grande distribution | [!BADGE Émergent]{type=Informative} | Taux de révision de 15 à 20 %, achats répétés de 10 à 15 % |

### Parcours cross-canal avec prise de décision

Orchestrez des expériences cross-canal avec Offer Decisioning en temps réel à chaque point de contact.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| | [Offres Exclusives Client VIP](retail/retail-overview.md#vip-customer-exclusive-offers) | Grande distribution | [!BADGE Avancé]{type=Caution} | Taux d’engagement de 50 à 70 % des VIP |

>[!TAB Personalization]

### Recommandation comportementale

Utilisez des modèles pilotés par l’IA pour afficher du contenu et des produits personnalisés en fonction de signaux comportementaux.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Recommandations de produit" width="40"> | [Recommandations de produits personnalisées](retail/retail-overview.md#personalized-product-recommendations) | Grande distribution | [!BADGE Émergent]{type=Informative} | Augmentation de 20 à 30 % du taux de clics, effet élévateur de conversion de 15 à 25 % |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Pages de catégorie" width="40"> | [Pages de catégorie personnalisées](retail/retail-overview.md#personalized-category-pages) | Grande distribution | [!BADGE Émergent]{type=Informative} | Augmentation de 25 à 35 % de l’engagement |

### Offer Decisioning

Utilisez une logique de décision centralisée pour évaluer et sélectionner la meilleure offre pour chaque client et contexte.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Vente Croisée" width="40"> | [Recommandations relatives aux ventes croisées et aux ventes incitatives](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Grande distribution | [!BADGE Avancé]{type=Caution} | Augmentation de 25 $ à 75 $ du AOV, augmentation des revenus de 10 à 15 % |

### Personalization Web/App Connu Des Visiteurs

Personnalisez le contenu web et l’application pour les visiteurs identifiés en fonction du profil, des préférences et du contexte de navigation.

| | Cas d’utilisation | Industrie | Maturité | Impact commercial |
| --- | --- | --- | --- | --- |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Grande distribution | [!BADGE Émergent]{type=Informative} | Augmentation du taux de conversion de 10 à 15 % |

>[!ENDTABS]
