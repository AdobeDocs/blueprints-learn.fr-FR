---
title: Journey Optimizer - Plan directeur pour Adobe Experience Platform et la diffusion de messages déclenchés
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 98%

---

# Plans directeurs de Journey Optimizer

Adobe Journey Optimizer est un système conçu spécifiquement pour permettre aux équipes marketing de réagir en temps réel aux comportements des clients et de s’adapter à leurs besoins en fonction de leur localisation. Les fonctionnalités de gestion des données ont été déplacées vers Adobe Experience Platform, ce qui permet aux équipes marketing de se concentrer sur ce qu’elles font le mieux : créer un parcours client de haute qualité et des conversations personnalisées.  Ce plan directeur décrit les fonctionnalités techniques de l’application et présente en détail les différents composants architecturaux qui constituent Adobe Journey Optimizer.

<br>

## Cas d’utilisation

* Messages déclenchés
* Confirmations de bienvenue et d’enregistrement
* Abandon de panier et de formulaire de demande
* Messages déclenchés par l’emplacement
* Expériences dans un stade
* Voyage et hospitalité avant l’arrivée et pendant le séjour

<br>

## Architecture

<img src="assets/ajo-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Scénarios de plan directeur

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Messagerie tierce](3rd-party-messaging.md) | Illustre comment Adobe Journey Optimizer peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées. | Diffusez des communications personnalisées aux clients dès qu’ils interagissent avec votre marque ou votre entreprise.<br><br>Remarques :<br><ul><li>Le système tiers doit prendre en charge les jetons porteur pour l’authentification.</li><li>Les adresses IP statiques ne sont pas prises en charge en raison d’une architecture multi-locataire.</li><li>Prenez en compte les contraintes architecturales concernant le système tiers lorsqu’il s’agit d’appels API par seconde.  Le client peut avoir besoin d’acheter du volume supplémentaire auprès du fournisseur tiers pour prendre en charge le volume provenant de Journey Optimizer.</li><li>Gestion des décisions non prise en charge dans les messages ou les payloads</li></ul> |

<br>

## Modèles d’intégration

| Intégration | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Journey Optimizer avec Adobe Campaign](ajo-and-campaign.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et utiliser le système de messagerie transactionnelle Adobe Campaign natif pour envoyer le message. | Exploite les profils clients en temps réel et la puissance de Journey Optimizer pour orchestrer les expériences en temps réel tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe Campaign pour effectuer la communication du « dernier kilomètre ».<br><br>Remarques :<br><ul><li>L’application Campaign doit être soit la version v7 build >21.1, soit la v8.</li><li>Débit des messages</li><ul><li>Campaign v7 : jusqu’à 50 000 par heure</li><li>Campaign v8 : jusqu’à 1 million par heure</li><li>Campaign Standard : jusqu’à 50 000 par heure</li></ul><li>Aucune limitation n’est effectuée, de sorte que les cas d’utilisation doivent être vérifiés par un architecte d’entreprise.</li><li>Utilisation de la gestion des décisions non prise en charge dans les messages envoyés par Campaign</li></ul> |

<br>

## Conditions préalables

Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.

E-mail

* Vous devez disposer d’un sous-domaine prêt à être utilisé pour l’envoi de messages.
* Le sous-domaine peut être entièrement délégué à Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à Adobe (personnalisés).
* Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin de garantir une bonne délivrabilité.

Notification push mobile

* Le client doit disposer des services d’un développeur mobile pour créer l’application
* SDK mobile Adobe Experience Platform

<br>

## Garde-fous

[Lien de produit pour les garde-fous de Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Barrières de sécurité et conseils de latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Documentation connexe

* [Documentation pour Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
* [Documentation Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [Description du produit Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
