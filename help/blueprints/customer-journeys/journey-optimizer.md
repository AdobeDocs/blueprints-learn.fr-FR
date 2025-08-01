---
title: '[!DNL Journey Optimizer] - Message déclenché et plan directeur Adobe Experience Platform'
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 50%

---

# [!DNL Journey Optimizer] des plans directeurs

Adobe [!DNL Journey Optimizer] est un système conçu spécifiquement pour que les équipes marketing puissent réagir en temps réel aux comportements des clients et les rencontrer là où elles se trouvent. Les fonctionnalités de gestion des données ont été transférées vers Adobe [!DNL Experience Platform], ce qui permet aux équipes marketing de se concentrer sur ce qu’elles font de mieux : créer des parcours clients de classe mondiale et des conversations personnalisées.

Ce plan directeur décrit les fonctionnalités techniques de l’application et offre une exploration approfondie des différents composants architecturaux qui la [!DNL Journey Optimizer].

## Cas d’utilisation

* Messages déclenchés
* Confirmations de bienvenue et d’enregistrement
* Abandon de panier et de formulaire de demande
* Messages déclenchés par l’emplacement
* Expériences dans un stade
* Voyage et hospitalité avant l’arrivée et pendant le séjour

## Architecture

<img src="assets/ajo-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Scénarios de plan directeur

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Messagerie tierce](3rd-party-messaging.md) | Montre comment Adobe [!DNL Journey Optimizer] peut être utilisé avec des systèmes de messagerie tiers pour orchestrer et envoyer des communications personnalisées | Diffusez 1:1 en même temps des communications personnalisées aux clients qui interagissent avec votre marque ou votre entreprise<br><br>Considérations :<br><ul><li>Le système tiers doit prendre en charge les jetons porteur pour l’authentification.</li><li>Les adresses IP statiques ne sont pas prises en charge en raison d’une architecture multi-locataire.</li><li>Prenez en compte les contraintes architecturales concernant le système tiers lorsqu’il s’agit d’appels API par seconde.  Le client peut avoir besoin d’acheter un volume supplémentaire auprès d’un fournisseur tiers pour prendre en charge le volume provenant de l’adresse [!DNL Journey Optimizer]</li><li>Gestion des décisions non prise en charge dans les messages ou les payloads</li></ul> |

<br>

## Modèles d’intégration

| Intégration | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] avec Adobe Campaign](ajo-and-campaign.md) | Indique comment utiliser Adobe [!DNL Journey Optimizer] pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et tirer parti du système de messagerie transactionnelle Adobe Campaign natif pour envoyer le message | Tirez parti du profil client en temps réel et de la puissance des [!DNL Journey Optimizer] pour orchestrer des expériences sur le moment, tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe Campaign pour effectuer la communication du dernier kilomètre<br><br>Considérations :<br><ul><li>L’application Campaign doit être soit la version v7 build >21.1, soit la v8.</li><li>Débit des messages</li><ul><li>Campaign v7 : jusqu’à 50 000 par heure</li><li>Campaign v8 : jusqu’à 1 million par heure</li><li>Campaign Standard : jusqu’à 50 000 par heure</li></ul><li>Aucune limitation n’est effectuée, de sorte que les cas d’utilisation doivent être vérifiés par un architecte d’entreprise.</li><li>Utilisation de la gestion des décisions non prise en charge dans les messages envoyés par Campaign</li></ul> |

<br>

## Conditions préalables

[!DNL Experience Platform] ADOBE :

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer des sources de données [!DNL Journey Optimizer]
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe de profils individuels, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec [!DNL Journey Optimizer]

E-mail :

* Vous devez disposer d’un sous-domaine prêt à être utilisé pour l’envoi de messages.
* Le sous-domaine peut être entièrement délégué à Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à Adobe (personnalisés).
* Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin de garantir une bonne délivrabilité.

Mobile Push :

* Le client doit disposer des services d’un développeur mobile pour créer l’application
* SDK mobile Adobe Experience Platform

## Garde-fous

[[!DNL Journey Optimizer] Lien du produit Mécanismes de sécurisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Documentation connexe

* [[!DNL Experience Platform] documentation ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [[!DNL Experience Platform] Documentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [[!DNL Experience Platform Mobile SDK] documentation ](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
* [[!DNL Journey Optimizer] documentation ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
* [[!DNL Journey Optimizer] description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
