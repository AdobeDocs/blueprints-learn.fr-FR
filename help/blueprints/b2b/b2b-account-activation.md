---
title: Activation de compte B2B vers des destinations Advertising et des destinations de fichier
description: Utilisez l’engagement basé sur les comptes pour créer des audiences et les cibler via des destinations.
solution: Real-Time Customer Data Platform
source-git-commit: 074edca2f061459935d5f8b5e59e8cbd69b0fe4f
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 5%

---

# Activation de comptes B2B vers des destinations publicitaires et des destinations de fichier

L’engagement basé sur les comptes permet aux spécialistes du marketing B2B de créer des audiences de comptes (c’est-à-dire des listes d’entreprises) et de cibler ces entreprises par le biais de destinations comme LinkedIn qui acceptent des listes d’entreprises comme entrée ou exportent vers des destinations de stockage dans le cloud pour le ciblage et la vente.

## Cas d’utilisation

Grâce à l’engagement basé sur les comptes, les marketeurs peuvent déverrouiller trois cas d’utilisation clés :

* **Remplir les trous des groupes d’achats :** Un marketeur peut faire de la publicité sur des comptes où il n’a pas encore de contacts pour les rôles CMO ou CIO. Ils peuvent d’abord créer une audience de comptes sans contact avec le titre &quot;CMO&quot; ou &quot;CIO&quot;, puis activer l’audience sur LinkedIn. Dans la destination, LinkedIn, il peut alors lancer une campagne ciblant cette audience et des personnes spécifiques avec des titres de tâche &quot;CMO&quot; ou &quot;CIO&quot; pour atteindre ces nouveaux contacts et mettre en évidence les avantages de leurs offres.
* **Mettre à niveau ou vendre de manière croisée à d’autres divisions d’une société qui est un client existant :** Un marketeur peut créer une audience de compte qui a acheté le produit X il y a entre 3 et 9 mois, mais ne possède pas encore le produit Y. Ils peuvent ensuite l’activer, mettant en évidence les avantages du produit Y pour cette audience cible.
* **Ciblez les entreprises qui utilisent des produits concurrents :** Un marketeur peut ouvrir des comptes pour remplacer les produits d’un concurrent, même sans contacts sur ces comptes. Ils peuvent créer une audience de comptes basée sur des données de partenaire indiquant la propriété ou l’utilisation du produit d’un concurrent, puis l’activer via LinkedIn pour sources de contacts sur les comptes cibles en vue de son extension.

## Applications

* Édition B2B Real-time Customer Data Platform

## Modèles d’intégration

* Sources de données B2B (Marketo, Salesforce, etc.) -> Real-time Customer Data Platform Édition B2B -> Destinations.
* Diverses sources de données B2B peuvent être utilisées pour mapper des données de compte, de prospect, d’opportunité et de personne à l’édition B2B de Real-time Customer Data Platform.

## Architecture

![Architecture de référence du plan directeur d’Audience Activation de compte B2B](assets/b2b-blueprint-account-audience-activation.png)

## Destinations d’audience de compte

* (Sociétés) Audiences mappées LinkedIn
* Destinations de stockage dans le cloud
   * Azure Data Lake
   * Zone de destination des données
   * SFTP
   * Azure Blob
   * AWS S3

## Garde-fous

* Limité à 50 segments de compte par environnement de test.
* Évaluation de la segmentation par lots.
   * Évaluation automatique toutes les 24 heures suivant la fin de l’exécution de l’audience par lots et des tâches d’exportation de profils.
   * Pas de prise en charge de l’évaluation à la périphérie, en flux continu ou ad hoc.
* Les attributs de compte peuvent être exportés.
* Événements de personnes.
   * Jusqu’à 30 jours de recherche en amont des événements, aucun ordre des prédicats d’événement.
   * ET / OU sont pris en charge (pour que vous puissiez dire &quot;A et B doivent se produire&quot;,  mais vous ne pouvez pas dire &quot;A doit arriver 3 jours avant B&quot;).
* Pour les destinations de stockage dans le cloud, le planning d’exportation prend en charge l’option &quot;Après l’évaluation des segments&quot;.
* [Barrières de sécurité du profil et de la segmentation B2B](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Étapes de mise en oeuvre de l’édition B2B de Real-time Customer Data Platform, création d’audience de compte et activation

* Pour connaître les étapes de mise en oeuvre de Real-time Customer Data Platform B2B Edition, consultez la documentation [Prise en main de Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial) .
* Pour connaître les étapes de création d’audiences de compte, consultez la documentation [Audiences du compte](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/account-audiences) .
* Pour connaître les étapes d’Audience Activation du compte, consultez la documentation [Activation des audiences de compte](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-account-audiences) .
   * Mappage requis pour la destination [(sociétés) Audiences mappées LinkedIn &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Considérations relatives à la mise en œuvre

Les audiences avec correspondance linkedIn ont quelques exigences, y compris la taille d’audience minimale de 300 membres avec correspondance. Si l’audience de compte activée pour la destination d’audience correspondante de l’entreprise ne répond pas aux exigences, la définition de l’audience doit être modifiée afin d’augmenter la taille de l’audience pour lancer une campagne LinkedIn.

## Documentation connexe

* [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [&#x200B; Tutoriel vidéo sur la création et l’activation de l’audience de compte &#x200B;](https://experienceleague.adobe.com/fr/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [Créer des audiences de compte](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/account-audiences)
* [Activer les audiences de compte](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn Destination Connector](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/social/linkedin)
