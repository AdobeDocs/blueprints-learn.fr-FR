---
title: Plan directeur Campaign v8, Campaign et Platform
description: Adobe Campaign v8 est l’outil de campagne de nouvelle génération conçu pour les canaux marketing traditionnels tels que le publipostage par e-mail ou le publipostage direct. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots. Il est également fourni avec un serveur de messagerie en temps réel adaptable qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’une payload globale de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: ac6e27e88854f5a05a7ff7428cd4375b3532f632
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 95%

---

# Plan directeur de Campaign v8

Adobe Campaign v8 est l’outil de campagne de nouvelle génération conçu pour les canaux marketing traditionnels tels que le publipostage par e-mail ou le publipostage direct. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots. Il est également fourni avec un serveur de messagerie en temps réel adaptable qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’une payload globale de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.

<br>

## Cas d’utilisation

* Programmes de messagerie par lots très complexes
* Campagnes d’intégration et de remarketing
* Campagnes de publicité, de brochures et de magazines par publipostage direct
* Messages transactionnels simples (réinitialisation de mot de passe, accusés de réception d’e-mails, confirmations de commandes, etc.)
* Intégration des données de Campaign dans Adobe Experience Platform pour l’analyse et la création de profils
* Partage des audiences Real-time Customer Data Platform avec Campaign.

<br>

## Diagrammes d’architecture

En savoir plus sur les modèles de déploiement de Campaign v8 dans [cette page](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Déploiement Campaign Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Architecture de référence du plan directeur Campaign v8 (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


### Déploiement FDA Campaign v8

<img src="assets/P1-P3-architecture.png" alt="Architecture de référence du plan directeur Campaign v8 (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Modèles d’intégration

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [Real-time Customer Data Platform avec Adobe Campaign](rtcdp-and-campaign-v8.md) | Montre comment Adobe Experience Platform, son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées. | <ul><li>Partage de profils et d’audiences de Real-Time CDP vers Adobe Campaign via l’échange de fichiers dans le stockage cloud et les workflows d’ingestion d’Adobe Campaign. </li><li>Partage facile des données de diffusion et d’interaction issues des conversations de la clientèle dans Real-Time CDP d’Adobe Campaign afin d’améliorer le profil client en temps réel et de fournir des rapports cross-canal sur les campagnes de messagerie.</li></ul> |
| [Journey Optimizer avec Adobe Campaign](ajo-and-campaign.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et utiliser le système de messagerie transactionnelle Adobe Campaign natif pour envoyer le message. | Exploite les profils clients en temps réel et la puissance de Journey Optimizer pour orchestrer les expériences en temps réel tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe Campaign pour effectuer la communication du « dernier kilomètre ».<br><br>Remarques :<br><ul><li>Il peut envoyer jusqu’à 1 million de messages par heure via le serveur de messagerie en temps réel.<li>Aucune limitation n’est effectuée à partir de Journey Optimizer, de sorte que la validation technique par un architecte d’entreprise de prévente est assurée.</li><li>La gestion des décisions n’est pas pris en charge dans les payloads de Campaign v8.</li></ul> |

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

### Notification push mobile

* Préparez un développeur mobile pour pouvoir déployer, configurer et créer l’application mobile.
* Adobe ne fournit qu’un SDK pour collecter les informations nécessaires auprès de FCM (Android) et APNS (iOS) afin d’envoyer des payloads de message à leurs serveurs. Le client doit choisir la manière dont l’application mobile doit être codée, déployée, gérée et déboguée.

### Webapps (facultatif)

* Peuvent déléguer un sous-domaine supplémentaire pour le désabonnement et les pages de destination hébergés par Campaign.
* Le certificat SSL est vivement recommandé.

<br>

## Garde-fous

### Dimensionnement du serveur d’applications

* Le stockage peut être dimensionné jusqu’à 200 millions de profils, pour atteindre potentiellement 1 milliard de profils.
* Configurez et contrôlez l’accès des utilisateurs dans l’Adobe Admin Console.
* Le chargement des données vers Campaign doit être effectué par le biais de fichiers par lots.
   * La prise en charge du chargement des données d’API est principalement destinée à la gestion des profils ou des objets simples dans la base de données (c’est-à-dire la création et la mise à jour). Il n’est pas destiné à être utilisé pour le chargement de gros volumes de données ou d’opérations de type batch.
   * L’utilisation d’API pour lire des données à des fins d’application personnalisée n’est pas prise en charge.
   * Les données chargées via l’API sont mises en scène dans la base de données de l’application, puis répliquées toutes les heures dans la base de données Cloud.
* Des limites aux appels API s’appliquent. En savoir plus dans la section [Description du produit Adobe Campaign](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Dimensionnement du serveur de messagerie par lots

* Peut s’adapter pour gérer jusqu’à 20 millions de messages par heure.

### Dimensionnement du serveur de messagerie en temps réel

* Peut envoyer jusqu’à 1 million de messages par heure.
* Deux serveurs de messagerie en temps réel sont configurés par défaut. Il est possible d’étendre la configuration à jusque huit serveurs de messagerie en temps réel.

### Configuration des SMS

* Campaign permet de s’intégrer à un fournisseur SMS. Le fournisseur doit être acheté par le client et intégré à la campagne pour l’envoi de messages basés sur les SMS.
* La prise en charge s’effectue via un protocole SMPP.
* Il existe trois (3) différents types de SMS, qu’Adobe peut tous prendre en charge :
   * SMS MT (Mobile Terminated) : un SMS émis par Adobe Campaign vers les téléphones mobiles par le fournisseur SMPP.
   * SMS MO (Mobile Originated) : un SMS envoyé par un mobile à Adobe Campaign par l’intermédiaire du fournisseur SMPP.
   * SMS SR (Status Report) ou DR ou DLR (Delivery Receive) : un reçu de retour envoyé par le mobile à Adobe Campaign par l’intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe Campaign peut également recevoir un SR indiquant que le message n’a pas pu être diffusé, souvent avec une description de l’erreur.

## Étapes de mise en œuvre

Consultez le guide de prise en main pour la [Mise en œuvre d’Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=fr).


## Documentation connexe

* [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Description du produit Campaign v8](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/launch.html)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html)
