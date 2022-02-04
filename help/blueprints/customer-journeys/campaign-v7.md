---
title: Plan directeur de Campaign v7
description: Adobe Campaign v7 est un outil de campagne conçu pour les canaux marketing traditionnels tels que le courrier électronique et le courrier. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots.  Il est également fourni avec un serveur de messagerie en temps réel qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’une payload globale de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.
solution: Campaign Classic v7
hidefromtoc: true
exl-id: d8cae05f-cf29-45f6-8ee0-1d670a31bdcc
source-git-commit: 13f750c0ff820ab01ed4fc615aba864bc2dc7b75
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 3%

---

# Plan directeur de Campaign v7

Adobe Campaign v7 est un outil de campagne conçu pour les canaux marketing traditionnels tels que le courrier électronique et le courrier. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots.  Il est également fourni avec un serveur de messagerie en temps réel qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’une payload globale de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.

<br>

## Cas d’utilisation

* Programmes de messagerie par lots
* Campagnes d’intégration et de remarketing
* Campagnes de publicité, de brochures et de magazines par courrier
* Messages transactionnels simples à faible volume (réinitialisation du mot de passe, accusés de réception d’emails, confirmations de commandes, etc.)

<br>

## Architecture

<img src="assets/campaign-v7-architecture.svg" alt="Architecture de référence du plan directeur de Campaign v7" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Scénarios de plan directeur

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Journey Optimizer avec Adobe Campaign](ajo-and-campaign.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et utiliser le système de messagerie transactionnelle Adobe Campaign natif pour envoyer le message. | Tirer parti du profil client en temps réel et de la puissance de Journey Optimizer pour orchestrer les expériences en temps réel tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe Campaign pour effectuer la communication du dernier kilomètre<br><br>Considérations :<br><ul><li>Peut envoyer jusqu’à 50 000 messages par heure via le serveur de messagerie en temps réel<li>Aucun ralentissement n’est effectué à partir de Journey Optimizer, de sorte que la validation technique par un architecte d’entreprise de prévente soit assurée.</li><li>Offer Decisioning n’est pas pris en charge dans les payloads du serveur de messagerie en temps réel de Campaign v7</li></ul> |
| [Real-Time CDP avec Adobe Campaign](rtcdp-and-campaign.md) | Présente comment Adobe Experience Platform Real-Time CDP et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées | <ul><li>Partage natif d&#39;audiences de l&#39;Experience Platform avec Adobe Campaign v8 via une destination productisée</li><li>Prise en charge native de l’ingestion des données de diffusion et d’interaction des conversations des clients dans l’Experience Platform afin d’améliorer le profil client en temps réel et de fournir des rapports cross-canal sur les campagnes de messagerie.</li></ul> |

<br>

## Conditions préalables

### Serveur d’applications et serveur de messagerie en temps réel

* La console cliente Adobe Campaign est nécessaire pour interagir et utiliser le logiciel Campaign v8. Il s’agit d’un client Windows qui utilise des protocoles Internet standard (SOAP, HTTP, etc.). Assurez-vous que les autorisations nécessaires sont activées dans votre organisation pour distribuer, installer et exécuter des logiciels.

* Listes autorisées des adresses IP
   * Identifier les plages d’adresses IP que tous les utilisateurs exploiteront lors de l’accès à la console cliente
   * Identifiez les systèmes d’entreprise qui seront autorisés à communiquer avec le serveur de messagerie en temps réel et vérifiez qu’ils disposent d’une adresse IP ou d’une plage affectée de manière statique que vous pouvez liste autorisée.
   * Il peut être configuré et contrôlé via le Panneau de Contrôle Campaign
* Gestion des clés sFTP
   * Disposer de clés publiques SSH utilisables avec le sFTP fourni par Campaign. Il peut être configuré et contrôlé via le Panneau de Contrôle Campaign.

### E-mail

* disposer d’un sous-domaine prêt à être utilisé pour l’envoi des messages ;
* Le sous-domaine peut être entièrement délégué à l’Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à l’Adobe (personnalisés).
* Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin de garantir une bonne délivrabilité

### Push mobile

* Disposer d’un développeur mobile pour déployer, configurer et créer l’application mobile
* Adobe ne fournit qu’un SDK pour collecter les informations nécessaires auprès de FCM (Android) et APNS (iOS) afin d’envoyer des payloads de message à leurs serveurs. La responsabilité du client est de savoir comment l’application mobile doit être codée, déployée, gérée et déboguée.

### Webapps (facultatif)

* Peut déléguer un sous-domaine supplémentaire pour le désabonnement et les landing pages hébergés par Campaign
* Le certificat SSL est vivement recommandé.

<br>

## Garde-fous

### Dimensionnement du serveur d’applications

* Le stockage peut être dimensionné jusqu’à 100 millions de profils
* Configuration et contrôle de l’accès des utilisateurs via Adobe Admin Console (recommandé) ou localement dans l’application elle-même
* Le chargement des données vers Campaign doit être effectué par le biais de fichiers de lots.
   * La prise en charge du chargement des données d’API est principalement destinée à la gestion des profils ou des objets simples dans la base de données (c’est-à-dire la création et la mise à jour). Il n’est pas destiné à être utilisé pour le chargement de gros volumes de données ou d’opérations de type batch.
   * L’utilisation d’API pour lire des données à des fins d’application personnalisée n’est pas prise en charge
* Les appels API sont limités à 15 par seconde ou 150 000 par jour à l’échelle

### Dimensionnement du serveur de messagerie par lots

* peut être mis à l’échelle pour gérer jusqu’à 2,5 millions de messages par heure ;

### Dimensionnement du serveur de messagerie en temps réel

* Peut envoyer jusqu’à 50 000 messages par heure
* Par défaut, un seul (1) serveur de messagerie en temps réel est configuré. Cela permet de s’assurer que toute communication avec le serveur est effectuée via un jeton de session qui expire dans 24 heures.
* Vous pouvez éventuellement déployer jusqu’à huit (8) serveurs de messagerie en temps réel, mais l’authentification ne prend en charge que l’utilisateur/la transmission.
* L’approche recommandée consiste toujours à utiliser un serveur de messagerie en temps réel pour tirer parti, si possible, de l’authentification par jeton de session.

### Configuration des SMS

* Campaign permet de s&#39;intégrer à un fournisseur SMS. Le fournisseur est acheté par le client et intégré à la campagne pour l&#39;envoi de messages basés sur les SMS.
* La prise en charge s’effectue via le protocole SMPP.
* Il existe trois (3) différents types de SMS que l&#39;Adobe peut tous prendre en charge :
   * SMS MT (Mobile Terminated) : un SMS émis par Adobe Campaign vers les téléphones mobiles par le fournisseur SMPP.
   * SMS MO (Mobile Originated) : un SMS envoyé par un mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP.
   * SMS SR (Status Report) ou DR ou DLR (Delivery Receive) : un reçu de retour envoyé par le mobile à Adobe Campaign par l&#39;intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe Campaign peut également recevoir un SR indiquant que le message n&#39;a pas pu être diffusé, souvent avec une description de l&#39;erreur.

### Configuration push mobile

* Deux approches prises en charge pour l’intégration aux appareils mobiles pour les notifications push :
   * SDK Mobile Experience Platform (recommandé)
   * SDK Campaign Mobile
* Itinéraire du SDK Mobile Experience Platform :
   * Tirez parti des balises Adobe et de l’extension Campaign Classic pour configurer votre intégration avec le SDK Mobile Experience Platform
   * Besoin d’une connaissance pratique des balises d’Adobe et de la collecte de données
   * Besoin d’une expérience de développement mobile avec les notifications push dans Android et iOS pour déployer le SDK, intégrer avec FCM (Android) et APNS (iOS) pour obtenir un jeton push, configurer votre application pour recevoir des notifications push et gérer les interactions push
* SDK Campaign Mobile
   * Contactez l’assistance clientèle d’Adobe pour accéder à
   * Veuillez suivre le [Documentation du SDK Campaign](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) pour savoir comment installer et configurer le SDK

   >[!IMPORTANT]
   >Si vous déployez le SDK Campaign et que vous travaillez avec d’autres applications Experience Cloud, vous devrez utiliser le SDK Mobile Experience Platform pour la collecte de données. Il s’agit d’un autre SDK qui devra être installé avec le SDK Campaign.

<br>

## Étapes d’implémentation

Voir [Guide de prise en main](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=en) pour la mise en oeuvre d’Adobe Campaign v7


## Documentation connexe

* [Documentation de Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Description du produit Campaign v7](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
