---
title: Secteur de la vente au détail - Activation avec des applications Experience Cloud
description: Diffusion d’expériences client en temps réel sur les médias numériques, par e-mail, par notifications push et sur les canaux web.
solution: Real-time Customer Data Platform, Customer Journey Analytics, Journey Orchestration, Campaign, Analytics, Target
kt: 9474
exl-id: a675bc81-e76c-491a-8718-359867d63351
source-git-commit: f03981dd3fe6ed9e60d2e60ca4eb91e129052a73
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 40%

---

# Problématique relative au secteur de la vente au détail

Cette entreprise d’expérience intégrée a cherché à personnaliser l’ensemble du parcours client afin d’accroître leur fidélité, de réaliser de nouvelles ventes auprès de clients existants et d’optimiser les dépenses marketing pour l’ensemble de leurs campagnes. La stratégie pour atteindre cet objectif consiste à étendre sa capacité numérique afin d’inclure les données client et les données de transaction hors ligne afin de stimuler sa croissance.

## L’approche d’Adobe

* Générez un profil client unifié qui inclut toutes les données en ligne/hors ligne pertinentes qui peuvent être activées en temps réel.
* Orchestrez les interactions client sur les différents canaux web, média et push afin de générer un comportement d’achat pour la première ou la seconde fois.

## Valeur commerciale offerte

| Objectifs | Stratégies | Valeur débloquée |
|---|---|---|
| **Orchestration des parcours client en temps réel **<br></br>** Incitation à des achats récurrents auprès de nouveaux clients **<br></br>** Amélioration de l’efficacité marketing et réduction des coûts liés aux médias**</ul> | <ul><li>Des données et une stratégie d’identité solides pour alimenter un profil en temps réel complet.</li><li>Diffusion de données client et transactionnelles en temps réel incluant une charge historique de 90 jours</li><li>Segmentation par flux vers les réseaux publicitaires et Adobe Target pour augmenter les dépenses publicitaires et les efforts de personnalisation des médias.</li><li>Parcours client en temps réel via Adobe Campaign qui incluent une stratégie de mesure des performances</li></ul> | <ul><li><strong>Real-time Customer Data Platform :</strong> diffusion d’expériences client en temps réel sur les médias, par e-mails, par notifications push et sur le web</li><li><strong>Sources de données :</strong> données en flux continu couvrant le stockage des profils, le système de commande, le catalogue de produits et les points de vente au détail de ce détaillant.</li><li><strong>Activation multimédia en temps réel :</strong>Diffusion en continu de segments vers les réseaux publicitaires pour l’attribution et la suppression des publicités</li><li><strong>Personnalisation web en temps réel :</strong>Segments de diffusion en continu activés vers Adobe Target afin de s’activer sur l’expérience web du détaillant.</li><li><strong>Journey Orchestration à l&#39;échelle :</strong>Messagerie déclenchée en temps réel enrichie des données client disponibles et activée en temps réel sur les canaux email et push</li></ul> |


## Utilisation

| Catégorie | Objectif | Cas pratique | Description |
|:----|:----|:----|:----|
| Parcours clients | Acquisition | Série de bienvenue | Bienvenue aux nouveaux abonnés avec une présentation de l’entreprise, des produits et des services |
| | | 1er programme d&#39;achat | |
| | Améliorer les ventes | Panier/Parcourir abandonné | Récupérer les acheteurs potentiels et les ventes incitatives |
| | | Révision/vente croisée de produits | Vente croisée d’autres articles avec des révisions de produits. |
| | | Promotions de produit |  |
| | | Temps de réorganisation | Rappel récurrent pour les produits/services cycliques |
| | Fidélité de la marque | Revenir en arrière | Récupérez les clients qui ont été inactifs. |
| | | Reminders d’anniversaire | Stimulez une relation plus personnelle avec vos clients en participant à la célébration de leur anniversaire ! |
| Marchandisage | Gérer le stock | Retour en stock | Améliorez l’inventaire en indiquant aux clients que les produits qu’ils souhaitent sont de retour en stock |
| | | Meilleure catégorie suivante | Identification des meilleures catégories/ventes pour les utilisateurs |
| | | Meilleurs vendeurs | |
| | | Reminders de chute de prix | Afficher aux utilisateurs que les articles qu’ils aimaient ont un prix réduit |
| | | Produits similaires |  |
| Personnaliser | Augmenter la conversion | Coupons/Offres | Afficher les meilleures offres/bons aux clients |
| | | Recherche de produit personnalisée | Amélioration de l’expérience de recherche |
| | | Recommendations de produit | Amélioration de l’expérience de navigation des produits |
| | | Expérience omnicanal | Atteindre les clients sur tous les canaux |
| Mesure | Présentation des Parcours client | Campagne cross-canal | Mesure des campagnes cross-canal |
| | | Performances des segments | Comprendre les performances et la contribution des segments |
| | | Rapports sur les abandons | Visualiser les conversions à chaque étape |
| | | Analyse des cohortes | Mesure de l’engagement entre les groupes de segments |
| | | Rapports Clics jusqu’à la marque | Découvrez comment les conversions de clients mènent à l’expérience en magasin |
| | | Attribution | déterminer quel point de contact/expérience a le plus d’influence sur la conversion d’achat ; |
| | | Predictive Insights | En savoir plus sur les affinités des clients |

## Architecture

<img src="../vertical-blueprints/assets/retail-architecture.png" alt="Architecture de référence de vente au détail" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## Plans directeurs associés


| Cas d’utilisation/intégration  | Lien |
|:----|:----|
| CJA + AEP | [Présentation des plans directeurs Customer Journey Analytics](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=fr) |
| | [Customer Journey Analytics - Cas d’utilisation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=fr) |
| AJO + AEP | [Adobe Journey Optimizer - Cas d’utilisation](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer.html?lang=en) |
| | [Gestion des décisions](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=fr) |
| RTCDP + AEP | [Activation d’audience en ligne / hors ligne](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=fr) |
| | [Experience Platform + Activation d’application](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=fr) |
| Marketo + AEP | [Activation et marketing B2B ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/overview.html?lang=en) | |
| Target + AEP | [Cas d’utilisation d’Adobe Target - Personnalisation web/mobile comportementale](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/behavioral.html?lang=fr) | [Personnalisation web/mobile avec des données client connu](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=en) | |
