---
title: Journey Optimizer - Plan directeur pour Adobe Experience Platform et la diffusion de messages déclenchés
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: d19f42a181b51135c3cf672eeb957709279fe49a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 98%

---

# Journey Optimizer

Adobe Journey Optimizer est un système conçu spécifiquement pour permettre aux équipes marketing de réagir en temps réel aux comportements des clients et de s’adapter à leurs besoins en fonction de leur localisation. Les fonctionnalités de gestion des données ont été déplacées vers Adobe Experience Platform, ce qui permet aux équipes marketing de se concentrer sur ce qu’elles font le mieux : créer un parcours client de haute qualité et des conversations personnalisées.  Ce plan directeur décrit les fonctionnalités techniques de l’application et présente en détail les différents composants architecturaux qui constituent Adobe Journey Optimizer.

## Cas d’utilisation

* Messages déclenchés
* Confirmations d’enregistrement
* Abandon de panier et de formulaire de demande
* Messages déclenchés par l’emplacement

## Architecture

<img src="assets/journey-optimizer.png" alt="Architecture de référence pour les messages déclenchés et le plan directeur d’Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Modèles d’intégration

* Adobe Experience Platform -> Journey Optimizer

## Conditions préalables

1. Le client doit disposer d’une session Experience Cloud configurée avec une organisation IMS valide
1. Push mobile

* Le client doit disposer des services d’un développeur mobile pour créer l’application
* SDK mobile Adobe Experience Platform
* sur la collecte de données
   * Propriété des balises mobiles
      * Extensions :
         * extension Adobe Journey Optimizer
         * Adobe Experience Platform Edge Network
         * Identité
         * Mobile Core
         * Profil
   * Configurations d’applications
   * Flux de données
      * Activé pour Experience Platform
      * Jeu de données d’événement : utilisé pour la collecte du comportement mobile en général
      * Jeu de données de profil : jeu de données du profil push AJO (ne peut pas être différent)

## Garde-fous

* Pour plus d’informations sur les garde-fous pour Journey Optimizer, consultez le lien [LINK](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)
* Segments par lot : veillez à connaître le volume quotidien des utilisateurs qualifiés et à garantir que le système de destination peut gérer les pics de débit par parcours et sur tous les parcours.
* Segments en diffusion en continu : veillez à ce que le pic initial des qualifications de profil puisse être traité en même temps que le volume de qualification des diffusion en continu quotidien par parcours et sur tous les parcours
* Activité de mise à jour des profils : le profil client en temps réel peut être mis à jour en mode natif dans un parcours.  Le traitement de la mise à jour dans la banque de profils peut prendre jusqu’à 1 min.
* Événements commerciaux : un parcours basé sur les segments lus peut être déclenché pour démarrer en fonction d’un appel externe dans le système JO.
* Prend en charge de façon native uniquement l’Offer decisioning dans les messages. Prise en charge par action native prévue dans le futur
* Canaux pris en charge :
   * E-mail
   * Push (FCM/APNS)
   * Points d’entrée de l’API REST
* Traite 5 000 événements par seconde avec mise à l’échelle horizontale (la limitation est celle du portefeuille)
* Les tests A/B sont effectués en utilisant deux diffusions et en déterminant les résultats à l’aide de QS ou CJA.
* Intégration Litmus : doit disposer d’un compte Litmus pour tirer parti de l’intégration

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas Adobe Campaign pour les éléments broadLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour utilisation dans une campagne.

#### Sources / destinations

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide d’API de diffusion en continu et de connecteurs sources.1. Configurez [!DNL Azure] la destination de stockage d’objets blob à utiliser avec Adobe Campaign.

#### Déploiement d’applications mobiles

1. Utilisez le SDK Adobe Campaign pour Adobe Campaign Classic ou le SDK Experience Platform pour Adobe Campaign Standard. Si vous disposez d’Experience Platform Launch, il est recommandé d’utiliser l’extension Adobe Campaign Classic ou Adobe Campaign Standard avec le SDK Experience Platform.


### Adobe Journey Orchestration

1. Les données de diffusion en continu utilisées pour lancer un parcours client doivent d’abord être configurées dans Journey Optimizer pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configurez des actions personnalisées.

## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
