---
title: Journey Optimizer - Blueprint de messagerie tierce
description: Illustre comment Adobe Journey Optimizer peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées.
solution: Experience Platform, Journey Optimizer
hidefromtoc: true
exl-id: 57e4d90a-61c9-444d-9bc5-40c7e58b4d21
source-git-commit: 13f750c0ff820ab01ed4fc615aba864bc2dc7b75
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 35%

---

# Messagerie tierce

Illustre comment Adobe Journey Optimizer peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées.

<br>

## Architecture

<img src="assets/3rd-party-messaging-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Conditions préalables

Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Experience Event, ajoutez le groupe de champs &quot;Orchestration eventID&quot; lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Individual Profile, ajoutez le groupe de champs &quot;Détails du test de profil&quot; pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.

Application de messagerie tierce

* Doit prendre en charge les appels d’API REST pour envoyer des payloads transactionnels

<br>

## Garde-fous

[Lien de produit de la protection Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)

Barrières de sécurité Journey Optimizer supplémentaires :

* La limitation est disponible aujourd’hui via l’API pour s’assurer que le système de destination n’est pas saturé au point d’échec. Cela signifie que les messages qui dépassent la limite seront complètement ignorés et ne seront jamais envoyés. Le ralentissement n’est pas pris en charge.
   * Nombre maximum de connexions : nombre maximum de connexions http/s qu’une destination peut gérer
   * Nombre d’appels max. : nombre maximal d’appels à effectuer dans le paramètre periodInMs
   * periodInMs - durée en millisecondes
* Les parcours initiés d’appartenance à un segment peuvent fonctionner suivant deux modes :
   * Segments par lot (actualisés toutes les 24 heures)
   * Segments de diffusion en continu (&lt;qualification de 5 minutes)
* Segments par lot : veillez à connaître le volume quotidien des utilisateurs qualifiés et à garantir que le système de destination peut gérer les pics de débit par parcours et sur tous les parcours.
* Segments en diffusion en continu : veillez à ce que le pic initial des qualifications de profil puisse être traité en même temps que le volume de qualification des diffusion en continu quotidien par parcours et sur tous les parcours
* offer decisioning non pris en charge
* Intégrations sortantes vers des systèmes tiers
   * Pas de prise en charge d’une seule adresse IP statique, car notre infrastructure comporte plusieurs clients (doit mettre en liste autorisée toutes les adresses IP du centre de données).
   * Seules les méthodes de POST et de PUT sont prises en charge pour les actions personnalisées.
   * Prise en charge de l’authentification : token | password | OAuth2
* Impossible de regrouper et de déplacer des composants individuels de Adobe Experience Platform ou de Journey Optimizer entre différents environnements de test. Doit être réimplémenté dans les nouveaux environnements

<br>

Système de messagerie tiers

* Comprendre la charge que le système peut prendre pour les appels d’API transactionnels
   * Nombre d&#39;appels autorisés par seconde
   * Nombre de connexions
* Comprendre l’authentification requise pour effectuer des appels API
   * Type d’authentification :  token | password | OAuth2 est pris en charge via Journey Optimizer
   * Durée du cache d’authentification :  combien de temps le jeton est-il valide ? 
* Si l’ingestion par lots n’est prise en charge que, elle doit être diffusée en continu vers un moteur de stockage dans le cloud tel qu’Amazon Kinesis ou Azure Event Grid 1er.
   * Les données peuvent être mises en lots de ces moteurs de stockage dans le cloud et canalisées vers des solutions tierces.
   * Tout middleware requis serait la responsabilité du client ou de tiers de fournir

<br>

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) dans Experience Platform, en fonction des données fournies par le client.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour une utilisation par Parcours.

#### Sources / destinations

1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide d’API de diffusion en continu et de connecteurs sources.

### Journey Optimizer

1. Configurez votre source de données Experience Platform et déterminez les champs à mettre en cache dans le cadre des données profileStreaming utilisées pour lancer un parcours client. Vous devez d’abord configurer Journey Optimizer pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion
1. Configurez des sources de données externes
1. Configuration d’actions personnalisées pour une application tierce

### Configuration push mobile (facultative, car des jetons tiers peuvent être collectés)

1. Mise en oeuvre du SDK Mobile Experience Platform pour collecter des jetons push et des informations de connexion afin de lier à des profils clients connus
1. Tirez parti des balises Adobe et créez une propriété mobile avec l’extension suivante :
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identité pour Edge Network
   * Mobile Core
1. Assurez-vous que vous disposez d’un flux de données dédié pour les déploiements d’applications mobiles par rapport aux déploiements web.
1. Pour plus d’informations, reportez-vous à la section [Guide de Adobe Journey Optimizer Mobile](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

<br>

## Documentation connexe

* [Documentation Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
