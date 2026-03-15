---
title: Activation du compte B2B vers des destinations Advertising et des destinations de fichiers
description: Utilisez l’engagement basé sur un compte pour créer des audiences et les cibler via des destinations.
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 4%

---

# Activation du compte B2B vers des destinations publicitaires et des destinations de fichiers

L’engagement basé sur les comptes permet aux spécialistes du marketing B2B de créer des audiences de comptes (c’est-à-dire des listes d’entreprises) et de cibler ces entreprises via des destinations comme LinkedIn qui acceptent des listes d’entreprises comme entrées ou exportations vers des destinations de stockage dans le cloud à des fins de ciblage et de promotion des ventes.

## Cas d’utilisation

Grâce à l’engagement basé sur les comptes, les spécialistes marketing peuvent déverrouiller trois cas d’utilisation clés :

* **Combler les lacunes du groupe d’achat :** un spécialiste marketing peut faire de la publicité pour des comptes où il n’a pas encore de contacts pour les rôles de directeur marketing ou de directeur informatique. Ils peuvent d&#39;abord créer une audience de comptes sans contact avec le titre « CMO » ou « CIO » puis activer l&#39;audience sur LinkedIn. Au sein de la destination, LinkedIn, ils peuvent ensuite lancer une campagne ciblant cette audience et des personnes spécifiques ayant des titres de poste « CMO » ou « CIO » pour atteindre ces nouveaux contacts et mettre en évidence les avantages de leurs offres.
* **Vente incitative ou croisée à d’autres divisions d’une société qui est un client existant :** un spécialiste marketing peut créer une audience de compte qui a acheté le produit X il y a entre 3 et 9 mois, mais qui ne possède pas encore le produit Y. Ils peuvent ensuite activer le produit Y, en soulignant les avantages pour cette audience cible.
* **Cibler les entreprises qui utilisent des produits concurrents :** un spécialiste marketing peut commercialiser sur des comptes pour remplacer les produits d’un concurrent, même sans contact sur ces comptes. Ils peuvent créer une audience de comptes basée sur les données des partenaires indiquant la propriété ou l’utilisation du produit d’un concurrent, puis activer via LinkedIn les contacts sources au niveau des comptes cibles pour l’expansion.

## Applications

* Édition B2B Real-time Customer Data Platform

## Modèles d’intégration

* Sources de données B2B (Marketo, Salesforce, etc.) -> B2B edition Real-time Customer Data Platform -> Destinations.
* Plusieurs sources de données B2B peuvent être utilisées pour mapper les données de compte, de prospect, d’opportunité et de personnes au B2B edition de Real-time Customer Data Platform.

## Architecture

![Architecture de référence pour le plan directeur Audience Activation de compte B2B](assets/b2b-blueprint-account-audience-activation.png)

## Destinations d’audience de compte

* (Entreprises) Audiences appariées LinkedIn
* Destinations de stockage dans le cloud
   * Lac de données Azure
   * Zone de destination des données
   * SFTP
   * Azure Blob
   * AWS S3

## Garde-fous

* Limité à 50 segments de compte par sandbox.
* Évaluation de la segmentation par lots.
   * Automatiquement évalué toutes les 24 heures après la fin de l’exécution de l’audience par lots et des tâches d’exportation de profils.
   * Aucune prise en charge de l’évaluation Edge, en flux continu ou ad hoc.
* Les attributs de compte sont disponibles pour l’exportation.
* Événements de personnes.
   * Jusqu’à 30 jours de recherche en amont d’événement, aucun ordre de prédicats d’événement.
   * ET / OU sont pris en charge (de sorte que vous pouvez dire « A et B doivent se produire »,  mais on ne peut pas dire « A doit arriver 3 jours avant B »).
* Pour les destinations de stockage dans le cloud, le planning d’exportation prend en charge l’option « Après l’évaluation du segment ».
* Mécanismes de sécurisation [Profil B2B et segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Étapes d’implémentation de Real-time Customer Data Platform B2B edition, création et activation d’audiences de compte

* Pour connaître les étapes d’implémentation de Real-time Customer Data Platform B2B edition, consultez la documentation [Prise en main de Real-Time Customer Data Platform B2B Editiond](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial).
* Pour connaître les étapes de création d’une audience de compte, consultez la documentation [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences).
* Pour connaître les étapes d’Audience Activation de compte, consultez la documentation [ Activer les audiences de compte ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences).
   * Mappage obligatoire pour la destination [(Entreprises) Audiences appariées LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Considérations relatives à la mise en œuvre

Les audiences correspondantes LinkedIn ont quelques exigences, notamment la taille minimale d’audience de 300 membres correspondants. Si l’audience de compte activée pour la destination d’audience associée de l’entreprise ne répond pas à cette exigence, la définition de l’audience doit être modifiée pour augmenter la taille de l’audience afin de lancer une campagne LinkedIn.

## Documentation connexe

* [B2B edition de Real-time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Tutoriel vidéo sur la création et l’activation d’audiences de compte](https://experienceleague.adobe.com/fr/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [Créer des audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)
* [Activer les audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - Connecteur de destination LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
