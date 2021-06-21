---
title: Journey Optimizer - Messagerie déclenchée et plan directeur Adobe Experience Platform
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: dc13a1fe9a32f70497c5c73485618e6989b7a644
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 49%

---

# Journey Optimizer

Adobe Journey Optimizer est un système conçu spécifiquement pour permettre aux équipes marketing de réagir en temps réel aux comportements des clients et de les satisfaire là où ils se trouvent. Les fonctionnalités de gestion des données ont été déplacées vers Adobe Experience Platform, ce qui permet aux équipes marketing de se concentrer sur ce qu’elles font le mieux : qui crée un parcours client de classe mondiale et des conversations personnalisées.  Ce plan directeur décrit les fonctionnalités techniques de l’application et présente en détail les différents composants architecturaux qui constituent Adobe Journey Optimizer.

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

1. Le client doit être configuré pour un Experience Cloud avec une organisation IMS valide
1. Mobile Push

* Un développeur mobile doit être disponible pour créer l’application.
* SDK Adobe Experience Platform Mobile
* Adobe Launch
   * Propriété mobile
      * Extensions :
         * Extension Adobe Journey Optimizer
         * Adobe Experience Platform Edge Network
         * Identité
         * Mobile Core
         * Profil
   * Configurations d’applications
   * Datastreams
      * Activé pour Experience Platform
      * Jeu de données d’événement - utilisé pour la collecte du comportement mobile général
      * Jeu de données de profil - Jeu de données de profil push AJO (ne peut pas être différent)

## Garde-fous

* Voir le lien pour plus de détails sur les limitations
* Segments par lot : vous devez vous assurer de comprendre le volume quotidien des utilisateurs qualifiés et de vous assurer que le système de destination peut gérer le débit par parcours et sur tous les parcours.
* Segments de diffusion en continu : devez vous assurer que l’explosion initiale des qualifications de profil peut être gérée avec le volume de qualification de diffusion en continu quotidien par parcours et sur tous les parcours.
* Activité Mise à jour de profil : le profil client en temps réel peut être mis à jour en mode natif dans un parcours.  Le traitement de la mise à jour dans la banque de profils peut prendre jusqu’à 1 min.
* Événements commerciaux : un parcours basé sur les segments lus peut être déclenché pour démarrer en fonction d’un appel externe dans le système JO.
* Prend uniquement en charge l’Offer decisioning en mode natif dans les messages. Prise en charge future par l’action native
* Canaux pris en charge :
   * Email
   * Push (FCM/APNS)
   * Points de terminaison de l’API REST
* Traite 5 000 événements par seconde avec mise à l’échelle horizontale (la limitation du portefeuille)
* Les tests A/B sont effectués en utilisant deux diffusions et en déterminant les résultats à l’aide de QS ou CJA.
* Intégration Litmus : doit disposer d’un compte avec Litmus pour tirer parti de l’intégration

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=fr) dans Experience Platform, en fonction des données fournies par le client.
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

1. Les données de diffusion en continu utilisées pour lancer un parcours client doivent d’abord être configurées dans Journey Optimizer pour obtenir un identifiant d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configurez des actions personnalisées.

## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
