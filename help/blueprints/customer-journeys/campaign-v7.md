---
title: Plan directeur de Campaign v7
description: Adobe Campaign v7 est un outil de campagne conçu pour les canaux marketing traditionnels tels que le courrier électronique et le publipostage direct et par e-mail. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots.  Il est également fourni avec un serveur de messagerie en temps réel qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’un payload global de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: a74ef566bf468c5508263f4070beaf6d0cd73a0e
workflow-type: ht
source-wordcount: '1195'
ht-degree: 100%

---

# Plan directeur de Campaign v7

Adobe Campaign v7 est un outil de campagne conçu pour les canaux marketing traditionnels tels que le courrier électronique et le publipostage direct et par e-mail. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots.  Il est également fourni avec un serveur de messagerie en temps réel qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’un payload global de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.

<br>

## Cas d’utilisation

* Programmes de messagerie par lots
* Campagnes d’intégration et de remarketing
* Campagnes de publicité, de brochures et de magazines par publipostage direct
* Messages transactionnels simples à faible volume (réinitialisation du mot de passe, accusés de réception d’e-mails, confirmations de commandes, etc.)

<br>

## Architecture

<img src="assets/campaign-v7-architecture.svg" alt="Architecture de référence du plan directeur de Campaign v7" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Modèles d’intégration

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Real-Time CDP avec Adobe Campaign](rtcdp-and-campaign.md) | Présente comment le Real-Time CDP d’Adobe Experience Platform et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées. | <ul><li>Partage de profils et d’audiences de Real-Time CDP vers Adobe Campaign via l’échange de fichiers dans le stockage cloud et les workflows d’ingestion d’Adobe Campaign. </li><li>Partage facile des données de diffusion et d’interaction issues des conversations de la clientèle dans Real-Time CDP d’Adobe Campaign afin d’améliorer le profil client en temps réel et de fournir des rapports cross-canal sur les campagnes de messagerie.</li></ul> |
| [Journey Optimizer avec Adobe Campaign](ajo-and-campaign.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et utiliser le système de messagerie transactionnelle Adobe Campaign natif pour envoyer le message. | Exploite les profils clients en temps réel et la puissance de Journey Optimizer pour orchestrer les expériences en temps réel tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe Campaign pour effectuer la communication du « dernier kilomètre ».<br><br>Remarques :<br><ul><li>Peut envoyer jusqu’à 50 000 messages par heure via le serveur de messagerie en temps réel.<li>Aucune limitation n’est effectuée à partir de Journey Optimizer, de sorte que la validation technique par un architecte d’entreprise de prévente est assurée.</li><li>La gestion des décisions n’est pas prise en charge dans les payloads du serveur de messagerie en temps réel de Campaign v7.</li></ul> |

<br>

## Conditions préalables

### Serveur d’applications et serveur de messagerie en temps réel

* La console cliente Adobe Campaign est nécessaire pour interagir et utiliser le logiciel Campaign v8. Il s’agit d’un client Windows qui utilise des protocoles Internet standard (SOAP, HTTP, etc.). Assurez-vous que les autorisations nécessaires sont activées dans votre organisation pour distribuer, installer et exécuter des logiciels.

* Listes autorisées des adresses IP
   * Identifiez les plages d’adresses IP que tous les utilisateurs exploiteront en accédant à la console cliente.
   * Identifiez les systèmes d’entreprise qui seront autorisés à communiquer avec le serveur de messagerie en temps réel et vérifiez qu’ils disposent d’une adresse IP ou d’une plage affectée de manière statique que vous pouvez ajouter à la liste autorisée.
   * Elle peut être configurée et contrôlée dans le Panneau de contrôle de Campaign.
* Gestion des clés sFTP
   * Préparez les clés publiques SSH de façons à ce qu’elles soient utilisables avec le sFTP fourni par Campaign. Elles peuvent être configurées et contrôlées dans le Panneau de contrôle de Campaign.

### E-mail

* Préparez un sous-domaine de façon à ce qu’il puisse être utilisé pour l’envoi des messages.
* Le sous-domaine peut être entièrement délégué à Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à Adobe (personnalisés).
* Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin de garantir une bonne délivrabilité.

### Push mobile

* Préparez un développeur mobile pour pouvoir déployer, configurer et créer l’application mobile.
* Adobe ne fournit qu’un SDK pour collecter les informations nécessaires auprès de FCM (Android) et APNS (iOS) afin d’envoyer des payloads de message à leurs serveurs. Le client doit choisir la manière dont l’application mobile doit être codée, déployée, gérée et déboguée.

### Webapps (facultatif)

* Peuvent déléguer un sous-domaine supplémentaire pour le désabonnement et les pages de destination hébergés par Campaign.
* Le certificat SSL est vivement recommandé.

<br>

## Garde-fous

### Dimensionnement du serveur d’applications

* Le stockage peut être dimensionné jusqu’à 100 millions de profils.
* Configurez et contrôlez l’accès des utilisateurs dans l’Adobe Admin Console (recommandé) ou localement dans l’application elle-même.
* Le chargement des données vers Campaign doit être effectué par le biais de fichiers par lots.
   * La prise en charge du chargement des données d’API est principalement destinée à la gestion des profils ou des objets simples dans la base de données (c’est-à-dire la création et la mise à jour). Il n’est pas destiné à être utilisé pour le chargement de gros volumes de données ou d’opérations de type batch.
   * L’utilisation d’API pour lire des données à des fins d’application personnalisée n’est pas prise en charge.
* Les appels API sont limités à 15 par seconde ou à 150 000 par jour, selon l’échelle.

### Dimensionnement du serveur de messagerie par lots

* Peut être mis à l’échelle pour gérer jusqu’à 2,5 millions de messages par heure.

### Dimensionnement du serveur de messagerie en temps réel

* Peut envoyer jusqu’à 50 000 messages par heure.
* Deux serveurs de messagerie en temps réel sont configurés par défaut. Il est possible d’étendre la configuration à jusque huit serveurs de messagerie en temps réel.

### Configuration des SMS

* Campaign permet de s’intégrer à un fournisseur SMS. Le fournisseur doit être acheté par le client et intégré à la campagne pour l’envoi de messages basés sur les SMS.
* La prise en charge s’effectue via un protocole SMPP.
* Il existe trois (3) différents types de SMS, qu’Adobe peut tous prendre en charge :
   * SMS MT (Mobile Terminated) : un SMS émis par Adobe Campaign vers les téléphones mobiles par le fournisseur SMPP.
   * SMS MO (Mobile Originated) : un SMS envoyé par un mobile à Adobe Campaign par l’intermédiaire du fournisseur SMPP.
   * SMS SR (Status Report) ou DR ou DLR (Delivery Receive) : un reçu de retour envoyé par le mobile à Adobe Campaign par l’intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe Campaign peut également recevoir un SR indiquant que le message n’a pas pu être diffusé, souvent avec une description de l’erreur.

### Configuration push mobile

* Deux approches sont prises en charge pour l’intégration aux appareils mobiles pour les notifications push :
   * Le SDK mobile Experience Platform (recommandé)
   * SDK Campaign Mobile
* Chemin du SDK mobile Experience Platform :
   * Tirez parti des balises Adobe et de l’extension Campaign Classic pour configurer votre intégration avec le SDK Mobile Experience Platform.
   * Vous avez besoin d’une connaissance pratique des balises d’Adobe et de la collecte de données.
   * Vous avez besoin d’une expérience du développement mobile avec les notifications push dans Android et iOS pour le déploiement du SDK, l’intégration avec FCM (Android) et APNS (iOS) pour obtenir un jeton push, la configuration de votre application pour recevoir des notifications push et gérer les interactions push.
* SDK Campaign Mobile
   * Contactez l’assistance clientèle d’Adobe pour obtenir un accès.
   * Veuillez suivre les recommandations de la [documentation du SDK Campaign](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=fr) pour savoir comment installer et configurer le SDK.

   >[!IMPORTANT]
   >Si vous déployez le SDK Campaign et que vous travaillez avec d’autres applications Experience Cloud, vous devrez utiliser le SDK Mobile Experience Platform pour la collecte de données. Il s’agit d’un autre SDK qui devra être installé avec le SDK Campaign.

<br>

## Étapes d’implémentation

Consultez le [Guide de prise en main](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=fr) pour savoir comment mettre en œuvre Adobe Campaign v7.


## Documentation connexe

* [Documentation de Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Description du produit Campaign v7](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
