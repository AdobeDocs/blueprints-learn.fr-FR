---
title: Recommandation comportementale
description: Découvrez comment générer des recommandations d’éléments et de contenu à l’aide de stratégies de sélection et de modèles de classement.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7545'
ht-degree: 2%

---

# Recommandation comportementale

Ce guide explique comment implémenter des recommandations comportementales de produits et de contenu à l’aide de [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de fournir des expériences de recommandations personnalisées sur les canaux web, des applications mobiles et des e-mails.

Il présente toutes les options de mise en œuvre viables, les considérations relatives aux décisions à chaque phase et des liens vers la documentation [!DNL Adobe Experience League]. La recommandation comportementale génère des recommandations au niveau de l’élément ou du contenu à l’aide de signaux comportementaux (consultations de produits, achats, interactions de contenu, requêtes de recherche) associés à des stratégies de sélection et à des modèles de classement AJO Decisioning. Contrairement à Offer Decisioning , qui régit un ensemble limité d’offres, de promotions ou d’incitations à l’aide de règles d’éligibilité et de contraintes commerciales, ce modèle fonctionne sur de grands catalogues d’articles en constante évolution (produits, articles, vidéos) où la sélection est pilotée par des signaux d’affinité comportementale plutôt que par l’éligibilité régie.

## Présentation du cas d’utilisation

Les entreprises qui disposent de catalogues de produits, de bibliothèques de contenu ou de bibliothèques de médias doivent afficher les éléments les plus pertinents pour chaque visiteur en fonction de son historique comportemental et de son activité au cours de la session. Qu’il s’agisse d’un carrousel « recommandé pour vous » sur une page d’accueil, d’un widget de vente croisée sur une page de détails du produit ou de recommandations de produits intégrées dans une campagne par e-mail, le défi sous-jacent est le même : faites correspondre le profil comportemental de chaque visiteur aux éléments les plus pertinents d’un catalogue, puis diffusez ces recommandations sur le bon canal au bon moment.

Ce modèle résout ce problème en ingérant des signaux comportementaux en temps réel via [!DNL Web SDK] ou [!DNL Mobile SDK], en les traitant au moyen de stratégies de sélection AJO Decisioning qui combinent des attributs d’élément avec du contexte comportemental, et en diffusant les éléments recommandés par le biais de canaux web, in-app ou e-mail. Les modèles de classement peuvent être basés sur une formule (par exemple, trier par score d’affinité de catégorie) ou classés par l’IA (par exemple, modèle de recommandation personnalisé). Le modèle gère également les scénarios de démarrage à froid pour les nouveaux visiteurs sans historique comportemental en configurant des recommandations de secours.

L’audience cible de ce modèle comprend les équipes de marchandisage e, les équipes de personnalisation du contenu et les équipes d’expérience digitale qui cherchent à améliorer l’engagement, la conversion et la valeur moyenne des commandes par le biais de recommandations personnalisées basées sur le comportement réel de l’utilisateur.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### [Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.

**KPI :** % de montée en gamme/ventes croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

### [Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

**KPI :** taux de conversion, conversion de lead, coût par lead

### [Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

## Exemples de cas d’utilisation tactiques

Voici quelques implémentations tactiques courantes de ce modèle :

- Widget de vente croisée de produits sur la page des détails du produit (« les clients ont également acheté »).
- Carrousel « Recommandé pour vous » sur la page d’accueil en fonction de l’historique de navigation
- Recommandations de contenu sur le site multimédia en fonction du comportement de lecture
- Widget « Récemment consultés » associé à des éléments similaires
- Recommandations de produits complémentaires après achat
- Recommandations de produits par e-mail basées sur l’affinité comportementale
- Recommandations spécifiques à une catégorie basées sur le comportement de navigation en session
- Reclassement de résultats de recherche basé sur des signaux comportementaux

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité des implémentations de recommandations comportementales.

| KPI | Approche de mesure |
| --- | --- |
| Taux de clic publicitaire (CTR) des recommandations | Clics sur les éléments recommandés divisés par les impressions de recommandation |
| Taux de conversion recommandé | Achats ou actions souhaitées à partir des clics de recommandation divisés par le nombre total de clics de recommandation |
| Chiffre d’affaires influencé par Recommendations | Chiffre d’affaires total des commandes comprenant au moins un produit piloté par des recommandations |
| Effet élévateur de la valeur d’ordre moyenne (AOV) | Augmentation de la valeur d’opportunité pour les sessions qui ont impliqué des recommandations par rapport aux sessions sans |
| Articles par commande | Nombre d’éléments par commande pour les sessions avec recommandations |
| Couverture des recommandations | Pourcentage de pages vues éligibles ou de sessions ayant reçu des recommandations personnalisées (sans secours) |
| Taux de secours du démarrage à froid | Pourcentage de requêtes de recommandations traitées par une logique de secours en raison d’un historique comportemental insuffisant |

## Modèle de cas d’utilisation

**Recommandation comportementale**

Générez des recommandations au niveau de l’élément ou du contenu en fonction de signaux comportementaux, à l’aide de stratégies de sélection et de modèles de classement AJO Decisioning pour diffuser du contenu contextuel.

**Chaîne de fonction :** Ingestion de signaux comportementaux > Évaluation de la stratégie de prise de décision > Diffusion de recommandations > Rapports

Consultez la section Composition des modèles sous Considérations relatives à l’implémentation pour obtenir des conseils sur la combinaison de modèles.

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO) Prise de décision** — Stratégies de sélection, modèles de classement, catalogues d’éléments et politiques de décision qui évaluent les signaux comportementaux et renvoient les éléments les plus pertinents pour chaque visiteur
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Accumulation des données de profil comportemental, évaluation de l’audience pour la portée des recommandations et attributs calculés pour la notation de l’affinité comportementale
- **[!DNL Adobe Experience Platform] (AEP)** — Ingestion d’événements comportementaux via [!DNL Web SDK] et [!DNL Mobile SDK], traitement des [!DNL Edge Network], gestion des schémas XDM pour les données d’événement et de catalogue

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction Fondamentale | Etat | Éléments devant être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Sandbox AJO avec autorisations Decisioning activées. Rôles utilisateur configurés avec un accès à la gestion du catalogue d&#39;articles, à la configuration de la stratégie de sélection et à l&#39;administration de la surface de canal. | [Présentation des sandbox](https://experienceleague.adobe.com/fr/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/fr/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schéma d’événement d’expérience capturant des signaux comportementaux (consultations de produits, ajout au panier, achats, interactions de contenu) avec des identifiants d’article/de produit. Schéma de catalogue d&#39;articles (attributs de produit, catégories, images, prix) pour le jeu d&#39;articles de recommandation. Schéma de profil avec champs d’identité. Tous les schémas activés pour [!DNL Real-Time Customer Profile]. | [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition), [Créer un jeu de données](https://experienceleague.adobe.com/fr/docs/experience-platform/catalog/datasets/create) |
| Sources et collecte de données | Obligatoire | La diffusion en continu d’événements comportementaux en temps réel via [!DNL Web SDK] ou [!DNL Mobile SDK] est essentielle ; la qualité des recommandations dépend de nouveaux signaux comportementaux. Les données de catalogue d’articles doivent être ingérées (par lots ou par flux). Flux de données configurés avec le service AJO activé pour la prise de décision Edge. | [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home), [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configurer les flux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/datastreams/configure) |
| Configuration des identités et des profils | Obligatoire | Les signaux comportementaux doivent être associés à une identité (connue ou anonyme via ECID) pour créer des profils comportementaux. Pour les recommandations de visiteurs connus, l’identité authentifiée (identifiant CRM, adresse e-mail) doit être configurée. Politique de fusion activée sur Edge pour la diffusion de recommandations en temps réel. | [présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Recommandé | Les audiences peuvent être utilisées pour définir la portée des recommandations (par exemple, recommander uniquement des produits Premium aux membres Premium) ou pour le filtrage. Non strictement requis si les recommandations sont purement comportementales. Obligatoire pour les recommandations par e-mail (option C) afin de définir l’audience cible. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Importance de la résolution | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que les scores d’affinité de catégorie, la fréquence d’interaction de produit, la récence d’achat et les dépenses totales améliorent la qualité du classement des recommandations. [!DNL Customer AI] les scores de propension peuvent encore améliorer la pertinence en prédisant la probabilité d’achat. | [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview), [Présentation de l’IA dédiée aux clients](https://experienceleague.adobe.com/fr/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Gestion du cycle de vie des données | Recommandé | Les données comportementales doivent avoir des politiques d’expiration appropriées — la pertinence des recommandations se dégrade avec les données obsolètes. La définition de politiques d’expiration de jeu de données sur les jeux de données d’événements comportementaux garantit l’actualisation et gère le stockage. L’application du consentement garantit la conformité de l’utilisation des données comportementales. | [Expiration des jeux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les libellés de gouvernance sur les données comportementales garantissent une utilisation conforme de l’historique des interactions pour les recommandations. Particulièrement important lorsque les données comportementales incluent les habitudes de navigation, l’historique d’achat ou les signaux d’intérêt pour les produits de santé/financiers. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Recommandé | La latence de diffusion des recommandations, les taux de secours et l’intégrité de l’ingestion du catalogue d’articles doivent être surveillés. Les alertes sur les échecs d’ingestion d’événements comportementaux et les erreurs de prise de décision permettent de maintenir la qualité des recommandations. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home), [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview) |
| Rapports et analyses | Inclus | Les rapports de rendement recommandés font partie de l&#39;étape 4 de la chaîne de fonctions. [!DNL Customer Journey Analytics] l’analyse de l’efficacité des recommandations, de l’impact sur le chiffre d’affaires et des performances au niveau des éléments sur les surfaces et les segments fournit des informations d’optimisation. | [Présentation de &#x200B;](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview) [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Prise de décision. | Configuration du catalogue d&#39;articles et de la stratégie de sélection | Configurez des catalogues d’éléments (éléments de décision), des stratégies de sélection avec des modèles de classement comportementaux, des règles de filtrage et des recommandations de secours |
| Configuration de canal | Configuration des canaux et de la surface | Configurez des surfaces de diffusion pour les canaux web (expériences basées sur du code), in-app, de carte de contenu ou d’e-mail où des recommandations seront rendues |
| Création de messages | Configuration du contenu et de la diffusion | Concevoir des modèles de rendu de recommandation, des dispositions d’affichage d’élément et des expressions de personnalisation pour les éléments recommandés |
| Rapports et analyse des performances | Rapports et optimisation | Surveillez les mesures de clics publicitaires, de conversion et de recettes des recommandations grâce aux rapports natifs d’AJO et à l’intégration de [!DNL Customer Journey Analytics] |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Définition De La Portée De L’Audience (Option C) | Évaluez les segments d’audience utilisés pour définir la portée des recommandations ou la population cible des campagnes de recommandations par e-mail. |
| Enrichissement de profil | Enrichissement Du Signal Comportemental | Enrichir les profils avec des attributs calculés (scores d’affinité de catégorie, fréquence d’interaction) qui améliorent le classement des recommandations |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation :

- [ ] AJO Decisioning est configuré et activé dans le sandbox cible
- [ ] [!DNL Web SDK] ou [!DNL Mobile SDK] est déployé et collecte des événements comportementaux avec des identifiants de produit/contenu
- [ ] données de catalogue de produits ou de contenus sont disponibles pour l’ingestion (nom du produit, catégorie, prix, URL de l’image, disponibilité)
- [ ] schémas d’événement comportementaux incluent des identifiants d’article/produit qui sont liés à des articles de catalogue
- [ ] flux de données est configuré avec le service [!DNL Adobe Journey Optimizer] activé (obligatoire pour la prise de décision Edge)
- [ ] politique de fusion avec `isActiveOnEdge: true` est configurée (requise pour les recommandations web/d’application en temps réel).
- [ ] Pour les recommandations par e-mail (option C) : la surface de canal e-mail est configurée et validée
- [ ] Pour les recommandations par e-mail (option C) : l’audience cible est définie et l’évaluation est effectuée

## Options de mise en œuvre

Les options suivantes décrivent différentes approches de mise en œuvre des recommandations comportementales. Choisissez l’option qui correspond le mieux aux exigences et aux contraintes techniques de votre canal.

### Option A : recommandations Web en temps réel

**Idéal pour** recommandations de produits ou de contenus sur des pages web : widgets de vente croisée de pages de détails de produits, carrousels de recommandation de page d’accueil, listes personnalisées de pages de catégories et personnalisation des résultats de recherche.

**Fonctionnement :**

Les signaux comportementaux sont collectés en temps réel via [!DNL Web SDK] lorsque les visiteurs naviguent sur le site. Chaque page vue, interaction de produit ou requête de recherche est diffusée en continu vers AEP et associée au profil du visiteur (via ECID pour les visiteurs anonymes ou identité authentifiée pour les visiteurs connus). Lorsqu’une page contenant une surface de recommandation se charge, le [!DNL Web SDK] demande une évaluation de prise de décision à AJO via l’[!DNL Edge Network] . Le moteur de décision évalue le profil comportemental du visiteur par rapport à la stratégie de sélection, applique la logique de classement, filtre les éléments inéligibles (déjà achetés, en rupture de stock) et renvoie les éléments recommandés.

Les recommandations sont rendues sur la page par le biais d’expériences basées sur du code ou de surfaces de canal web. Le rendu peut être un carrousel, une grille, un widget à un seul élément ou toute disposition personnalisée définie dans le modèle de recommandation. Les événements d’impression et de clic sont automatiquement suivis vers AEP pour le compte rendu des performances.

**Considérations principales :**

- Edge decisioning nécessite que la politique de fusion soit active sur Edge
- La latence des recommandations dépend du temps de réponse [!DNL Edge Network] (SLA inférieur à 500 ms pour les requêtes à portée unique)
- Les visiteurs anonymes reçoivent des recommandations en fonction du comportement en session ; les visiteurs connus bénéficient de l’historique comportemental intersessions
- Les visiteurs démarrés à froid sans historique de comportement reçoivent des recommandations de secours

**Avantages :**

- Personnalisation en temps réel basée sur le comportement en session
- Diffusion de recommandations de sous-seconde via [!DNL Edge Network]
- Fonctionne pour les visiteurs anonymes et connus
- Suivi automatique des impressions et des clics
- Aucun rechargement de page requis pour les nouvelles recommandations

**Limitations :**

- Le magasin de profils Edge contient un sous-ensemble d’attributs de profil complets
- Des modèles de classement complexes avec de nombreux attributs de profil peuvent nécessiter une évaluation côté hub
- Nécessite un déploiement [!DNL Web SDK] avec suivi des événements comportementaux

**Experience League:**

- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)

### Option B : recommandations pour les applications mobiles

**Idéal pour** : recommandations de produits in-app, flux de contenu personnalisés, recommandations basées sur des notifications et expériences commerciales mobiles.

**Fonctionnement :**

Les signaux comportementaux sont collectés via l’[!DNL Mobile SDK] lorsque les utilisateurs interagissent avec l’application. Les consultations de produits, les interactions de contenu, les recherches et les achats sont diffusés en continu vers AEP. Lorsqu’un écran contenant une surface de recommandation se charge, le [!DNL Mobile SDK] demande une évaluation de prise de décision. Les recommandations sont diffusées par le biais de messages in-app, de cartes de contenu ou d’expériences basées sur du code dans l’application mobile.

Les cartes de contenu sont particulièrement adaptées aux cas d’utilisation de recommandations dans les applications mobiles, car elles persistent dans une expérience de flux que les utilisateurs peuvent parcourir à leur guise. Les messages in-app peuvent être utilisés pour des recommandations contextuelles déclenchées par des comportements spécifiques (par exemple, afficher des produits complémentaires après l’ajout d’un article au panier).

**Considérations principales :**

- [!DNL Mobile SDK] doit être configuré avec le suivi comportemental des événements pour les interactions pertinentes
- Les cartes de contenu fournissent une surface de recommandation persistante ; les messages in-app sont éphémères
- Le suivi du comportement hors ligne nécessite la gestion des files d’attente SDK pour l’envoi différé des événements
- Les cycles de mise à jour de l’App Store affectent la vitesse de déploiement des modifications de rendu des recommandations

**Avantages :**

- Expérience mobile native avec rendu de recommandation fluide intégré à l’application
- Les cartes de contenu fournissent un flux de recommandations persistant et navigable
- Les messages in-app activent des recommandations contextuelles déclenchées par le comportement
- Exploite les signaux au niveau de l’appareil (emplacement, schémas d’utilisation des applications) pour une pertinence accrue

**Limitations :**

- Nécessite une intégration [!DNL Mobile SDK] et des ressources de développement d’applications
- Le rendu des modifications nécessite des mises à jour de l’application (sauf si vous utilisez des expériences basées sur le code avec des dispositions pilotées par serveur)
- Les périodes hors ligne créent des écarts dans la collecte des signaux comportementaux

**Experience League:**

- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Option C : recommandations comportementales par e-mail

**Idéal pour :** les recommandations de produits dans les campagnes par e-mail : parcourez les e-mails abandonnés contenant des recommandations de produits consultées, les e-mails de vente croisée post-achat, les résumés « choix pour vous » périodiques et les e-mails de réengagement contenant des suggestions de produits personnalisées.

**Fonctionnement :**

Les données de profil comportemental accumulées à partir des sessions précédentes orientent la sélection de recommandations au moment de l’envoi des e-mails ou au moment du rendu. Une audience est définie pour cibler les destinataires appropriés (par exemple, les visiteurs qui ont parcouru le site mais n’ont pas effectué d’achat, les clients qui ont effectué un achat récent). Une campagne ou un parcours est configuré pour envoyer un e-mail contenant des emplacements de recommandations. Au moment de l’envoi, AJO Decisioning évalue le profil comportemental de chaque destinataire par rapport à la stratégie de sélection et injecte les éléments recommandés dans le contenu de l’e-mail.

Cette option repose sur l’historique comportemental accumulé plutôt que sur les signaux en session. Les attributs calculés (scores d’affinité de catégorie, consultations de produits récentes, fréquence d’achat) améliorent considérablement la qualité des recommandations par e-mail, car ils transforment l’historique comportemental en signaux au niveau du profil que la stratégie de sélection peut évaluer efficacement.

**Considérations principales :**

- Les recommandations par e-mail sont évaluées au moment de l’envoi, et non au moment de l’ouverture ; l’état du profil comportemental au moment de l’envoi détermine les recommandations
- Les attributs calculés sont vivement recommandés pour améliorer la qualité du classement
- Les limitations de rendu des emails (pas de JavaScript, CSS limité) limitent les formats d’affichage de recommandation
- Nécessite une surface de canal e-mail configurée et validée

**Avantages :**

- Tire parti de l’historique complet des comportements entre les sessions pour une personnalisation plus approfondie
- S’intègre aux workflows de campagne et de parcours existants
- Efficace pour les scénarios de réengagement et de reconquête où les points de contact web/app ne sont pas disponibles
- Peut inclure plusieurs emplacements de recommandations dans un seul e-mail

**Limitations :**

- Les recommandations sont statiques au moment de l’envoi - elles ne sont pas mises à jour à l’ouverture de l’e-mail
- Contraintes de rendu des emails limitant les formats d’affichage des recommandations
- Nécessite l’évaluation des audiences et une infrastructure d’orchestration des campagnes et des parcours
- Complexité d’implémentation accrue due à des dépendances supplémentaires (configuration du canal, définition de l’audience, exécution de la campagne)

**Experience League:**

- [Créer un e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/create-email)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Comparaison des options

Le tableau suivant résume les principales différences entre les options d’implémentation.

| Critères | Option A : Temps Réel Web | Option B : application mobile | Option C : Comportement des e-mails |
| --- | --- | --- | --- |
| Idéal pour | Recommandations de pages web (PDP, page d’accueil, catégorie) | Recommandations in-app et flux de contenu | Campagnes par e-mail avec recommandations de produits |
| Source de signal comportemental | En session + intersession ([!DNL Web SDK]) | Interactions in-app ([!DNL Mobile SDK]) | Historique comportemental cumulé (profil) |
| Latence des recommandations | Sous-seconde ([!DNL Edge Network]) | Sous-seconde ([!DNL Edge Network]) | À l’heure d’envoi (évaluation côté hub) |
| Type de visiteur | Anonyme et connu | Connu (utilisateurs de l’application) | Connu (destinataires de l’e-mail) |
| Complexité | Moyenne | Medium-Grand | Élevée |
| Dépendance de canal | [!DNL Web SDK] de surface d’expérience basée sur du code | [!DNL Mobile SDK], surface de carte in-app/de contenu | Surface du canal e-mail, audience, campagne/parcours |
| Requiert | [!DNL Web SDK] le déploiement, politique de fusion Edge | [!DNL Mobile SDK] le déploiement, politique de fusion Edge | Surface d’e-mail, définition d’audience, configuration de campagne |

### Choisir la bonne option

Suivez les conseils suivants pour sélectionner la meilleure option pour votre situation :

- **Commencez par l’option A** si votre objectif principal est de générer des recommandations de produits en temps réel sur votre site web. Il s’agit du point de départ le plus courant qui fournit une valeur immédiate avec une complexité d’implémentation minimale.
- **Choisissez l’option B** si votre application mobile est un canal d’engagement principal et que les recommandations in-app génèrent une augmentation significative de la conversion. L&#39;option B peut être exécutée en parallèle avec l&#39;option A en utilisant les mêmes stratégies de sélection et les mêmes catalogues d&#39;articles.
- **Ajoutez l’option C** lorsque vous souhaitez étendre les recommandations comportementales aux campagnes par e-mail. Il est généralement superposé à l’option A ou B, en utilisant les mêmes catalogues d’éléments et stratégies de sélection, mais avec des modèles de rendu spécifiques aux e-mails et un ciblage basé sur les audiences.
- **Combinez les options A et C** pour obtenir un modèle commun : des recommandations web en temps réel pour les visiteurs actifs, ainsi que des recommandations de navigation ou d’e-mail post-achat abandonnées pour les visiteurs qui quittent sans effectuer de conversion.

## Phases de mise en œuvre

Les phases suivantes vous guident tout au long de l’implémentation de bout en bout des recommandations comportementales.

### Phase 1 : configuration du schéma d’événement comportemental et de la collecte de données

**Fonction d’application :** AEP : modélisation et préparation des données (F2), AEP : sources et collecte de données (F3)

Cette phase établit les schémas XDM, les jeux de données et les mécanismes de collecte de données qui capturent les signaux comportementaux et les données de catalogue d’articles. Toute logique de recommandation dépend de cette base de données.

#### Décision : conception d’un schéma d’événement comportemental

Quels signaux comportementaux devraient générer des recommandations ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Consultations de produit uniquement | Recommandations simples de vente croisée/de montée en gamme | Effort d’implémentation le plus faible ; profondeur de signal limitée |
| Consultations de produit + achats | Recommandations avec logique d’exclusion des achats et de vente croisée | Effort modéré ; active le filtrage « exclure les achats déjà effectués » |
| Suite comportementale complète (vues, achats, ajout au panier, recherches, interactions de contenu) | Recommandations sophistiquées avec classement multi-signal | Qualité de signal maximale ; nécessite une instrumentation [!DNL Web SDK]/[!DNL Mobile SDK] complète |

#### Décision : méthode d&#39;ingestion du catalogue d&#39;articles

Comment le catalogue de produits ou de contenu sera-t-il ingéré dans AEP ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Ingestion par lots via le connecteur source | Les mises à jour du catalogue sont périodiques (quotidiennes/hebdomadaires) | Configuration plus simple ; les modifications du catalogue ne sont pas répercutées en temps réel |
| Ingestion par flux | Le catalogue nécessite des mises à jour en temps quasi réel (variations de prix, disponibilité) | Plus complexe ; garantit que les recommandations reflètent l’inventaire actuel. |
| Chargement manuel/API | Petit catalogue avec des modifications peu fréquentes | Configuration la plus simple ; non évolutive pour les catalogues dynamiques ou volumineux |

**Navigation dans l’interface utilisateur :** Gestion des données > Schémas > Créer un schéma ; Collecte de données > Flux de données > Nouveau flux de données

**Détails de configuration clés :**

- Le schéma d’événement d’expérience doit inclure des identifiants de produit/élément (SKU, ID de produit, ID de contenu) dans la payload d’événement
- Le schéma de catalogue d&#39;articles doit inclure les attributs utilisés pour le filtrage et le classement : catégorie, prix, URL de l&#39;image, statut de disponibilité, balises
- Le service [!DNL Adobe Journey Optimizer] du flux de données doit être activé pour la prise de décision Edge
- [!DNL Web SDK] appels `sendEvent` doivent inclure des données d’interaction de produit mappées à des champs XDM commerce

**Documentation Experience League :**

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition)
- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/datastreams/configure)
- [Définir une relation entre deux schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/tutorials/relationship-api)

### Phase 2 : configuration de l’identité et du profil

**Fonction D’Application :** AEP : Configuration D’Identité Et De Profil (F4)

Cette phase met en place des espaces de noms d’identité, des désignations d’identité principale et des politiques de fusion qui garantissent que les signaux comportementaux sont correctement associés aux profils des visiteurs et qu’ils sont disponibles pour la diffusion de recommandations en temps réel.

#### Décision : politique de fusion pour la prise de décision Edge

Le cas d’utilisation de recommandation nécessite-t-il une évaluation d’Edge en temps réel ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Politique de fusion Active-On-Edge | Options A et B (recommandations web et mobiles en temps réel) | Obligatoire pour la diffusion de recommandations inférieure à deux ; une seule politique de fusion Edge par sandbox |
| Politique de fusion standard (pas sur Edge) | Option C uniquement (évaluation des recommandations d’e-mail au moment de l’envoi) | Suffisant pour l’évaluation côté hub ; ne consomme pas le slot de politique de fusion d’Edge |

#### Décision : identité anonyme ou identité de visiteur connue

Comment les signaux comportementaux provenant de visiteurs anonymes doivent-ils être traités ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| ECID uniquement (anonyme) | Recommandations destinées principalement aux visiteurs anonymes en fonction du comportement en session | Configuration plus simple ; aucune continuité entre sessions à moins que le visiteur ne s’authentifie |
| ECID + identité authentifiée (identifiant CRM, e-mail) | Recommandations entre sessions pour les visiteurs connus avec l’assemblage des identités | Profils comportementaux plus riches ; nécessite un flux d’authentification |
| Les deux avec liaison de graphiques d’identités | Parcours complet anonyme à connu avec groupement d’identités | La plus complète. Nécessite une configuration des règles de liaison d’identités. |

**Navigation dans l’interface utilisateur :** Identités > Espaces de noms d’identité ; Profils > Politiques de fusion

**Détails de configuration clés :**

- L’espace de noms ECID est préconfiguré et utilisé automatiquement par [!DNL Web SDK] et [!DNL Mobile SDK]
- Des espaces de noms d’identité personnalisés (identifiant CRM ou identifiant de fidélité) doivent être créés pour l’identité authentifiée
- L’identité du Principal sur le schéma Événement d’expérience doit être ECID pour les événements comportementaux web/mobiles
- La politique de fusion doit utiliser un graphique d’appareil privé pour regrouper les identités entre les appareils

**Documentation Experience League :**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/identity-linking-logic)

### Phase 3 : configuration du catalogue d&#39;articles et de la stratégie de sélection

**Fonction d’application :** AJO : prise de décision

Cette phase configure le catalogue d&#39;éléments (éléments de décision), les stratégies de sélection qui combinent des signaux comportementaux avec des attributs d&#39;élément pour le classement, les règles de filtrage pour exclure les éléments inéligibles et les recommandations de secours pour les profils de démarrage à froid.

#### Décision : portée du catalogue d&#39;articles

Quels éléments sont disponibles pour recommandation ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Catalogue de produits (e-commerce) | Recommander des produits physiques ou numériques à l’achat | Les attributs d’article incluent le prix, la catégorie, la disponibilité et les images |
| Catalogue de contenu (média/publication) | Recommandations d’articles, de vidéos ou de contenus éducatifs | Les attributs d’élément incluent le topic, l’auteur, la date de publication et le type de contenu |
| Catalogue hybride | Recommandation de produits et de contenu | Nécessite un schéma d’élément unifié prenant en charge les deux types |

#### Décision : approche de classement

Comment les éléments éligibles doivent-ils être classés pour déterminer les meilleures recommandations ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Classement basé sur une formule | Une logique commerciale claire pour le classement (par exemple, trier par score d’affinité de catégorie multiplié par la popularité de l’élément) | Classement transparent et vérifiable. Nécessite une formule de classement définie. |
| Classement par l’IA (optimisation automatique) | Le machine learning doit déterminer un classement optimal en fonction des données de conversion | Nécessite au moins 1 000 événements de conversion pour la formation des modèles ; moins transparent |
| Basé sur la priorité (manuel) | Commande de recommandation simple et manuellement organisée | Plus facile à configurer ; ne s’adapte pas au comportement individuel |

#### Décision : règles de filtrage

Quels éléments doivent être exclus des recommandations ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Exclure les articles déjà achetés | Recommandations relatives aux ventes croisées et aux découvertes | Nécessite un historique d’achat dans le profil comportemental |
| Exclure les éléments en rupture de stock | E-commerce avec inventaire dynamique | Nécessite des mises à jour de catalogues en temps réel ou quasi réel |
| Exclure les éléments précédemment ignorés | Recommandations de contenu où les utilisateurs peuvent ignorer les suggestions | Nécessite le suivi des rejets dans les événements comportementaux |
| Filtrage à l&#39;échelle des catégories | Recommandations limitées à des catégories spécifiques | Utilise les attributs d&#39;élément pour le filtrage |

#### Décision : stratégie de démarrage à froid

Que doit-on montrer aux nouveaux visiteurs qui n’ont aucun historique comportemental ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Objets populaires (best-sellers mondiaux) | Secours à usage général | Facile à gérer ; non personnalisé |
| Éléments populaires spécifiques à une catégorie | Le visiteur est arrivé sur une page de catégorie. | Secours contextuellement pertinent ; nécessite un contexte de page |
| Sélections éditoriales organisées | La marque souhaite un contrôle éditorial sur l’expérience de démarrage à froid | Nécessite un traitement et des mises à jour manuels |
| Éléments de tendance (popularité pondérée par le temps) | Secours dynamique reflétant les tendances actuelles | Nécessite le calcul du signal de tendance |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Décisions ; [!DNL Journey Optimizer] > Composants > Gestion des décisions > Offres ; [!DNL Journey Optimizer] > Composants > Gestion des décisions > Emplacements

**Détails de configuration clés :**

- Créez des éléments de décision représentant chaque produit ou élément de contenu du catalogue, avec des attributs (catégorie, prix, URL de l’image, balises).
- Définir des stratégies de sélection qui combinent le filtrage de catalogue d&#39;articles avec la logique de classement comportemental
- Configurer des modèles de classement : les expressions basées sur une formule peuvent référencer des attributs de profil (par exemple, les scores d&#39;affinité de catégorie à partir d&#39;attributs calculés)
- Créer des offres/éléments de secours qui servent de recommandations par défaut pour les profils de démarrage à froid
- Organisez les éléments en collections à l’aide de qualificateurs de collection (balises) pour le regroupement logique
- Configurer des règles de filtrage dans des stratégies de sélection pour appliquer des règles métier (exclure les achats, en stock uniquement)

**Documentation Experience League :**

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4 : configuration du canal et de la surface

**Fonction d’application :** AJO : configuration de canal

Cette phase configure les surfaces de diffusion sur lesquelles des recommandations seront rendues. La configuration varie considérablement selon l’option d’implémentation.

#### Décision : type de surface de diffusion

Où les recommandations s’affichent-elles ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Expérience basée sur le code (web) | Widget de recommandation sur les pages web avec rendu personnalisé | Flexibilité maximale pour le rendu ; nécessite un développement front-end. |
| Surface de canal web | Surface de personnalisation web standard | Utilise le concepteur web d’AJO ; moins flexible que le code ; |
| Message in-app | Recommandations contextuelles déclenchées par le comportement de l’application | Éphémère ; disparaît après interaction ou rejet |
| Carte de contenu (mobile) | Flux de recommandations persistant dans l’application mobile | Persiste jusqu’à ce que l’utilisateur agisse ; expérience de flux navigable |
| E-mail | Recommandations de produits intégrées dans les campagnes par e-mail | Statique à l&#39;envoi; soumis aux contraintes de rendu des emails |

**Là où les options divergent :**

**Pour L’Option A (Recommandations En Temps Réel Sur Le Web) :**
Configurez une surface d’expérience ou une surface de canal web basée sur du code. Les expériences basées sur le code offrent la plus grande flexibilité pour le rendu de recommandation personnalisé (carrousels, grilles, cartes d’éléments). L’URI de surface identifie l’endroit où les recommandations apparaissent sur la page.

**Pour L’Option B (Recommandations Relatives Aux Applications Mobiles) :**
Configurez les surfaces des messages in-app ou des cartes de contenu. Les cartes de contenu sont recommandées pour les flux de recommandations persistants. Les messages in-app fonctionnent bien pour les recommandations contextuelles déclenchées par un comportement.

**Pour L’Option C (Recommandations Comportementales Par E-Mail) :**
Configurez une surface de canal e-mail avec la délégation de sous-domaine, l’affectation de groupe d’adresses IP et les paramètres d’expéditeur. Assurez-vous que la surface est validée pour la délivrabilité.

**Navigation dans l’interface utilisateur :** Administration > Canaux > Surfaces des canaux > Créer une surface

**Documentation Experience League :**

- [Configurer des surfaces de canal](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer le canal SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5 : configuration du contenu et de la diffusion

**Fonction d’application :** AJO : création de messages

Cette phase définit les modèles de rendu de recommandation qui contrôlent l’affichage des éléments recommandés pour le visiteur. Cela inclut la conception de mise en page des articles, les expressions de personnalisation qui extraient les attributs d’article (nom, image, prix, lien) et la conception globale de l’expérience de recommandation.

#### Décision : format d’affichage des recommandations

Comment les éléments recommandés doivent-ils être rendus ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Carrousel (défilement horizontal) | Page d’accueil ou page de catégorie avec un espace vertical limité | Modèle UX familier ; affiche plusieurs éléments dans un espace compact |
| Grille (à plusieurs lignes) | Section de recommandation dédiée avec beaucoup d’espace | Affiche plus d’éléments à la fois ; fonctionne bien pour les sections « recommandé pour vous » |
| Widget pour un seul élément | Recommandation contextuelle à un emplacement spécifique de la page (par exemple, dans la barre latérale) | Empreinte minimale ; emplacement à fort impact |
| Bloc d’e-mail intégré | Recommandations incorporées dans le corps de l’e-mail | Soumis aux contraintes HTML/CSS de messagerie ; généralement 2 à 4 éléments |

#### Décision : nombre de recommandations à afficher

Combien d’éléments la décision doit-elle renvoyer par emplacement ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| 3-4 éléments | Widget de recommandation standard | Équilibre pertinence et densité visuelle |
| 6-8 éléments | Carrousel avec défilement ou disposition en grille | Plus d’options pour le visiteur ; nécessite une profondeur de catalogue suffisante. |
| 1 élément | Recommandation contextuelle pour un seul produit | Impact de la pertinence le plus élevé ; rendu le plus simple |
| 10 éléments et plus | Expérience de recommandation de style de flux | Cas d’utilisation lourds de contenu (médias, publication) |

**Là où les options divergent :**

**Pour L’Option A (Recommandations En Temps Réel Sur Le Web) :**
Concevez le rendu des recommandations à l’aide de modèles d’expérience basés sur du code. Utilisez HTML/CSS/JavaScript pour créer la disposition du carrousel, de la grille ou du widget. Les expressions Personalization font référence aux attributs de réponse de décision (nom de l’élément, URL de l’image, prix, URL du produit). Le suivi des impressions et des clics est géré automatiquement par le [!DNL Web SDK] .

**Pour L’Option B (Recommandations Relatives Aux Applications Mobiles) :**
Configurez les modèles de carte de contenu ou de message in-app avec la logique d’affichage des éléments. Utilisez des structures de contenu basées sur JSON que l’application mobile rend en mode natif. Incluez des liens profonds pour chaque élément recommandé.

**Pour L’Option C (Recommandations Comportementales Par E-Mail) :**
Concevoir du contenu d’e-mail à l’aide du Designer d’e-mail. Insérez des emplacements de recommandations à l’aide de blocs de contenu orientés décision. Configurez des expressions de personnalisation pour les attributs d’élément dans le modèle d’e-mail. La personnalisation de ligne d&#39;objet peut référencer les éléments recommandés principaux.

**Navigation dans l’interface utilisateur :** Gestion de contenu > Modèles de contenu ; Campagne/Parcours > Modifier le contenu > Designer d’e-mail

**Détails de configuration clés :**

- Chaque emplacement de recommandation doit faire référence à la décision créée à la phase 3
- Les expressions Personalization utilisent la syntaxe Handlebars pour effectuer le rendu des attributs d’élément
- Pour le web : configurez l’expérience basée sur le code pour appeler la décision et effectuer le rendu de la réponse
- Pour les e-mails : incorporation de la décision dans l’action d’e-mail de la campagne ou du parcours
- Prévisualiser les recommandations à l’aide de profils de test avec un historique comportemental connu

**Documentation Experience League :**

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Phase 6 : configurer la portée de l’audience et la campagne/le parcours (option C uniquement)

**Fonction de l’application :** RT-CDP : évaluation de l’audience, AJO : exécution de campagne ou Journey Orchestration

Pour les recommandations par e-mail (option C), cette phase définit l’audience cible et configure la campagne ou le parcours qui diffuse l’e-mail de recommandation. Les options A et B ignorent cette phase, car les recommandations sont diffusées en temps réel au chargement de la page ou de l’écran.

#### Décision : méthode d’évaluation de l’audience

Comment l’audience cible des e-mails de recommandation doit-elle être évaluée ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Évaluation par lots | Campagnes par e-mail de recommandation planifiées (résumé quotidien et hebdomadaire) | Délai d’envoi prévisible ; audience évaluée avant envoi |
| Évaluation en flux continu | E-mails de recommandation déclenchés par un événement (navigation abandonnée, après achat) | Qualification des audiences en temps quasi réel ; association avec l’orchestration des parcours |

#### Décision : mécanisme de diffusion

L’e-mail doit-il être diffusé via une campagne ou un parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Campagne planifiée | E-mail de recommandation unique ou récurrent envoyé à une audience définie | Configuration plus simple ; évaluation et envoi d’audiences par lots |
| Parcours avec entrée d’audience | E-mails de recommandations en cours déclenchés par la qualification d’audience | Active des flux à plusieurs étapes (par exemple, e-mail de recommandation suivi d’un rappel) |
| Parcours déclenché par un événement | E-mail de recommandation déclenché par un événement spécifique (abandon de navigation, achat) | Déclenchement en temps réel ; nécessite une entrée de parcours basée sur un événement |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle ; Campagnes > Créer une campagne ; Parcours > Créer un parcours

**Détails de configuration clés :**

- Définissez l’audience cible à l’aide d’expressions de règle de segment faisant référence à un historique comportemental (par exemple, « a consulté des produits au cours des 7 derniers jours, mais n’a pas effectué d’achat »).
- Configurez la campagne ou le parcours avec l’action d’e-mail référençant la surface de canal de la phase 4
- Incorporer la décision de la phase 3 dans le contenu de l’e-mail
- Définir des règles de planification et de fréquence pour éviter la sur-messagerie

**Documentation Experience League :**

- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Phase 7 : configuration des rapports et de l’optimisation

**Fonction d’application :** AJO : Rapports et analyse des performances, S5 : Rapports et analyses

Cette phase établit la surveillance des performances pour les mesures de clics publicitaires, de conversion et de chiffre d’affaires relatives aux recommandations. Il crée l’infrastructure de création de rapports pour mesurer l’efficacité des recommandations et identifier les opportunités d’optimisation.

#### Décision : Profondeur des rapports

Quel niveau d’analyse des rapports est nécessaire ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rapports natifs AJO uniquement | Suivi des performances des recommandations de base | Configuration rapide (limitée aux mesures suivies par AJO) |
| Intégration d’AJO + [!DNL Customer Journey Analytics] | Analyse de l’impact des recommandations cross-canal et attribution des revenus | Nécessite [!DNL Customer Journey Analytics] connexion et une vue de données ; fournit des informations plus détaillées |
| Espace de travail [!DNL Customer Journey Analytics] complet avec tableaux de bord personnalisés | Programme d’optimisation en cours avec analyse au niveau de l’élément, du segment et de la surface | La plus complète ; nécessite une expertise et une configuration [!DNL Customer Journey Analytics] |

**Navigation dans l’interface utilisateur :** Campagnes > Sélectionner une campagne > Rapport à toute heure ; Parcours > Sélectionner un parcours > Rapport à toute heure ; [!DNL Customer Journey Analytics] > Projets > Créer un projet

**Détails de configuration clés :**

- Consultez les rapports de campagne et de parcours AJO pour les mesures de diffusion et d’engagement
- Pour [!DNL Customer Journey Analytics] intégration, créez une connexion comprenant des jeux de données d’événement d’expérience AJO (commentaires des messages, suivi des e-mails, prise de décision)
- Créez une vue de données [!DNL Customer Journey Analytics] avec des dimensions spécifiques à la recommandation (nom de l’élément, catégorie d’éléments, surface de recommandation) et des mesures (impressions, clics, conversions, chiffre d’affaires)
- Créer des mesures calculées pour le taux de clics de recommandation, le taux de conversion et le chiffre d’affaires par impression
- Créer des panneaux d’espace de travail [!DNL Customer Journey Analytics] comparant les performances des recommandations sur les surfaces, les segments et les périodes

**Documentation Experience League :**

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/create-connection)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Considérations relatives à la mise en œuvre

Examinez les mécanismes de sécurisation, les pièges à éviter, les bonnes pratiques et les compromis suivants avant et pendant la mise en œuvre.

### Mécanismes de sécurisation et limites

- Maximum de 10 000 offres personnalisées approuvées (éléments de décision) par sandbox — [&#x200B; Mécanismes de sécurisation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 30 emplacements par décision
- Maximum de 30 portées de collection par demande de décision
- SLA du temps de réponse de diffusion des offres : moins de 500 ms à l’adresse P95 pour les requêtes Edge à portée unique
- Les modèles de classement par l’IA nécessitent au moins 1 000 événements de conversion pour la formation
- Les compteurs de limitation d’offre peuvent présenter un retard de quelques secondes maximum dans les scénarios à débit élevé
- les décisions Edge sont limitées aux attributs de profil disponibles dans le magasin de profils edge
- Une seule politique de fusion peut être active sur Edge par sandbox : [&#x200B; Mécanismes de sécurisation de profil &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- Maximum de 25 attributs calculés actifs par sandbox — [Mécanismes de sécurisation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- Ingestion par flux : maximum de 20 000 enregistrements par seconde par connexion HTTP - [&#x200B; Mécanismes de sécurisation d’ingestion &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/guardrails)

### Pièges courants

- **La décision renvoie uniquement les éléments de secours :** vérifiez que les éléments de décision personnalisés sont approuvés, dans leur période de validité, et que les règles d’éligibilité correspondent aux attributs de profil du visiteur. Vérifiez que les limites de limitation n’ont pas été atteintes.
- **La diffusion Edge renvoie une personnalisation vide :** assurez-vous que le flux de données est configuré avec le service [!DNL Adobe Journey Optimizer] activé et que la portée de décision est correctement formatée dans la requête [!DNL Web SDK].
- **Formule de classement non appliquée :** vérifiez que la formule est valide sur le plan syntaxique et fait référence à des attributs de profil accessibles. Les erreurs de formule reviennent silencieusement au classement par priorité.
- **Recommandations obsolètes :** si les données comportementales sur les événements ne circulent pas en temps réel, les recommandations seront basées sur des profils comportementaux obsolètes. Vérifiez que [!DNL Web SDK] ou [!DNL Mobile SDK] diffuse activement des événements.
- **Le taux de reprise après sinistre est trop élevé :** si un grand pourcentage de visiteurs reçoivent des recommandations de secours, envisagez d’enrichir la stratégie de démarrage à froid avec des signaux contextuels (catégorie de page actuelle, source de référence) plutôt que de vous fier uniquement à l’historique comportemental.
- **Les recommandations ne s’affichent pas sur la page :** vérifiez que l’URI de surface d’expérience basé sur le code correspond au modèle d’URL de la page et que l’[!DNL Web SDK] demande et effectue correctement le rendu de la réponse de décision.
- **Éléments de catalogue manquants dans les recommandations :** assurez-vous que tous les éléments de catalogue ont été ingérés en tant qu’éléments de décision, balisés avec les qualificateurs de collection appropriés et inclus dans les collections appropriées référencées par la stratégie de sélection.

### Bonnes pratiques

- Commencez avec un modèle de classement basé sur des formules utilisant des attributs calculés (affinité catégorielle, récence interaction) avant d’investir dans des modèles classés par l’IA. Les modèles basés sur des formules sont transparents, auditables et fournissent une base de comparaison solide.
- Implémentez le suivi des impressions et des clics dès le premier jour. Sans données d’interaction, les modèles de classement par l’IA ne peuvent pas s’entraîner et vous ne pouvez pas mesurer l’efficacité des recommandations.
- Créez des stratégies de sélection distinctes pour différentes surfaces de recommandation (page d’accueil, PDP, e-mail) au lieu de réutiliser une seule stratégie partout. Différentes surfaces desservent différentes intentions utilisateur.
- Utilisez des attributs calculés pour convertir l’historique comportemental en signaux de classement. Les données brutes des événements sont trop granulaires pour un classement efficace basé sur une formule ; les signaux agrégés tels que « score d’affinité de catégorie » et « jours depuis le dernier achat » sont plus efficaces.
- Testez les recommandations de secours séparément des recommandations personnalisées. Assurez-vous que les éléments de secours sont des valeurs par défaut de haute qualité et appropriées à la marque, qui offrent une bonne expérience aux nouveaux visiteurs.
- Surveillez le taux de secours de démarrage à froid en tant que mesure d’intégrité clé. Une diminution du taux de repli au fil du temps indique une couverture comportementale croissante.
- Pour les recommandations par e-mail, planifiez les envois aux moments où le profil comportemental est le plus complet (par exemple, après les heures de pointe de navigation, et non pendant ces heures).

### Décisions de compromis

Les compromis suivants doivent être évalués en fonction de vos besoins spécifiques.

#### Signaux en temps réel par rapport à l&#39;historique cumulé

Les signaux comportementaux en session fournissent une pertinence immédiate mais une profondeur limitée. L&#39;anamnèse comportementale accumulée fournit des informations détaillées mais peut être obsolète. L’équilibre entre ces sources affecte la qualité des recommandations.

- **L’option A privilégie :** des signaux en temps réel pour une pertinence immédiate, complétés par l’historique accumulé pour les visiteurs connus
- **L’option C privilégie :** l’historique cumulé uniquement, car les e-mails sont envoyés de manière asynchrone
- **Recommandation :** pour le Web et les appareils mobiles (options A, B), combinez les signaux en session avec les attributs calculés dérivés du comportement historique. Pour l’e-mail (option C), investissez massivement dans des attributs calculés qui résument l’historique comportemental en signaux au niveau du profil exploitables.

#### Modèles basés sur des formules par rapport aux modèles classés par l’IA

Le classement basé sur une formule est transparent et immédiat. Les modèles classés par l’IA s’adaptent automatiquement, mais nécessitent des données d’identification et offrent moins de visibilité sur les décisions de classement.

- **Favoris basés sur une formule :** transparence, vérifiabilité, déploiement immédiat et contrôle affiné de l’entreprise sur la logique de classement
- **Favoris classés par l’IA :** optimisation automatisée, découverte de motifs non évidents et réduction de l’effort de réglage manuel
- **Recommandation :** commencez par un classement basé sur une formule pour établir une référence de performances et accumuler les données de conversion. Passez aux modèles classés par l’IA une fois que vous disposez de suffisamment de données de formation (plus de 1 000 événements de conversion) et que vous souhaitez les optimiser au-delà de ce que l’optimisation manuelle des formules peut réaliser.

#### Couverture des recommandations par rapport à la pertinence

L’élargissement du catalogue d’éléments et l’assouplissement des règles de filtrage augmentent le pourcentage de requêtes qui reçoivent des recommandations personnalisées, mais peuvent réduire la pertinence par recommandation.

- **Favoris à forte couverture :** optimisation du nombre de visiteurs qui consultent des recommandations personnalisées. Utile lorsque l’objectif principal est l’engagement.
- **Favoris de haute pertinence :** affichage uniquement des éléments très pertinents, même si cela signifie que davantage de visiteurs voient des recommandations de secours ; utile lorsque l’objectif principal est la conversion
- **Recommandation :** Commencez par un filtrage modéré (exclure les articles achetés, les articles en rupture de stock) et surveillez le taux de secours et le taux de conversion. Resserrez les règles de filtrage uniquement si les données de conversion les prennent en charge.

#### Profondeur de Personalization par rapport à la complexité d’implémentation

Des signaux comportementaux plus riches et des modèles de classement plus sophistiqués améliorent la qualité des recommandations, mais augmentent la complexité de l’implémentation et la charge de maintenance.

- **Une implémentation plus simple favorise :** un délai d’évaluation plus rapide, une maintenance plus faible, un débogage et une itération plus faciles
- **Avantages d’une personnalisation plus approfondie :** augmentation du taux de conversion, meilleure expérience client, différenciation concurrentielle.
- **Recommandation :** implémentation par phases. Commencez par les signaux de consultation de produit et le classement basé sur les formules (phase 1). Ajoutez les attributs calculés pour l’enrichissement comportemental (phase 2). Évaluez les modèles classés par l&#39;IA une fois que les bases sont matures et que des données suffisantes sur la formation sont disponibles (phase 3).

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les technologies et fonctionnalités utilisées dans ce modèle.

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Création de qualificateurs de collection](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Collecte de données et Web/Mobile SDK

- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/install/overview)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/datastreams/configure)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/fr/docs/experience-platform/edge-network-server-api/overview)

### XDM et modélisation des données

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition)
- [Créer un jeu de données](https://experienceleague.adobe.com/fr/docs/experience-platform/catalog/datasets/create)
- [Définir une relation entre deux schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/tutorials/relationship-api)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/edge-segmentation)

### Attributs calculés et enrichissement du profil

- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/ui)
- [Présentation de Customer AI](https://experienceleague.adobe.com/fr/docs/experience-platform/intelligent-services/customer-ai/overview)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer des surfaces de canal](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Création et personnalisation de messages

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Rapports et analyses

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Gouvernance et cycle de vie des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home)
- [Expirations des jeux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Surveillance et observabilité

- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)
- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/guardrails)

### Tutoriels et guides

- [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)
- [Présentation des balises](https://experienceleague.adobe.com/fr/docs/experience-platform/tags/home)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/field-groups/profile/consents)
