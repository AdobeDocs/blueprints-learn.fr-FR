---
title: Plan directeur Campaign v8, Campaign et Platform
description: Découvrez le plan directeur de Campaign v8.
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 16b233c7ea9077566ebf12238f0a87beec1c61ce
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 41%

---

# Plan directeur de Campaign v8

Adobe Campaign v8 est l’outil de campagne de nouvelle génération conçu pour les canaux marketing traditionnels tels que le publipostage par e-mail ou le publipostage direct. Il offre des fonctionnalités ETL et de gestion des données performantes pour concevoir et organiser une campagne parfaite. Son moteur d’orchestration fournit des programmes marketing multi-touch riches qui mettent l’accent sur les parcours pilotés par lots.

Il est également fourni avec un serveur de messagerie en temps réel adaptable qui permet aux équipes marketing d’envoyer des messages prédéfinis sur la base d’une payload globale de n’importe quel système informatique pour des tâches telles que la réinitialisation du mot de passe, la confirmation de commande, la réception électronique, etc.

## Cas d’utilisation

* Des programmes de messagerie par lots très complexes.
* Campagnes d’intégration et de remarketing.
* Campagnes de publicité, de brochures et de magazines par publipostage direct
* Messages transactionnels simples (tels que réinitialisation de mot de passe, accusés de réception d’emails, confirmations de commandes, etc.).
* Intégration des données de Campaign à Adobe Experience Platform pour l’analyse et la création de profils.
* Partage des audiences Real-time Customer Data Platform avec Campaign.

## Diagrammes d’architecture

En savoir plus sur [Modèles de déploiement de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Déploiement Campaign Entreprise (FFDA)

<img src="assets/P4-architecture.png" alt="Architecture de référence du plan directeur Campaign v8 (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Déploiement FDA Campaign v8

<img src="assets/P1-P3-architecture.png" alt="Architecture de référence du plan directeur Campaign v8 (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Modèles d’intégration

| Scénario | Description | Fonctionnalités |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform] avec Adobe [!DNL Campaign]](rtcdp-and-campaign-v8.md) | Présente comment Adobe Experience Platform et son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe. [!DNL Campaign] pour diffuser des conversations personnalisées | <ul><li>Partage de profils et d&#39;audiences depuis le [!DNL Real-Time CDP] à Adobe [!DNL Campaign] par l’utilisation de l’échange et de l’Adobe de fichiers de stockage dans le cloud [!DNL Campaign] workflows d’ingestion </li><li>Partagez facilement les données de diffusion et d’interaction des conversations des clients dans le [!DNL Real-Time CDP] de l’Adobe [!DNL Campaign] pour améliorer le profil client en temps réel et fournir des rapports cross-canal sur les campagnes de messagerie</li></ul> |
| [[!DNL Journey Optimizer] avec Adobe [!DNL Campaign]](ajo-and-campaign.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et exploiter l’Adobe natif [!DNL Campaign] système de messagerie transactionnelle pour envoyer le message | Utilisation du profil client en temps réel et de la puissance de [!DNL Journey Optimizer] orchestrer les expériences en temps réel tout en utilisant les fonctionnalités natives de messagerie en temps réel d’Adobe [!DNL Campaign] pour effectuer la communication du dernier kilomètre<br><br>Considérations :<br><ul><li>Il peut envoyer jusqu’à 1 million de messages par heure via le serveur de messagerie en temps réel.<li>Aucun ralentissement n’est effectué à partir de [!DNL Journey Optimizer] assurez-vous que la validation technique est effectuée par un architecte d’entreprise de prévente</li><li>La gestion des décisions n’est pas pris en charge dans les payloads de Campaign v8.</li></ul> |

## Conditions préalables

Les conditions préalables suivantes sont nécessaires pour ce plan directeur.

### Serveur d’applications et serveur de messagerie en temps réel

* L&#39;Adobe [!DNL Campaign] La console cliente est nécessaire pour interagir et utiliser la variable [!DNL Campaign] Logiciel v8. Il s’agit d’un client Windows qui utilise des protocoles Internet standard (SOAP, HTTP, etc.). Assurez-vous que les autorisations nécessaires sont activées dans votre organisation pour distribuer, installer et exécuter des logiciels.

* Listes autorisées des adresses IP :
   * Identifiez les plages d’adresses IP exploitées par tous les utilisateurs lors de l’accès à la console cliente.
   * Identifiez les systèmes d’entreprise autorisés à communiquer avec le serveur de messagerie en temps réel et vérifiez qu’ils disposent d’une adresse IP ou d’une plage affectée de manière statique que vous pouvez mettre sur liste autorisée.
   * Elles peuvent être configurées et contrôlées dans le Panneau de contrôle de Campaign.
* Gestion des clés sFTP :
   * Préparez les clés publiques SSH de façons à ce qu’elles soient utilisables avec le sFTP fourni par Campaign. Elles peuvent être configurées et contrôlées dans le Panneau de contrôle de Campaign.

### E-mail

* disposer d’un sous-domaine prêt à être utilisé pour l’envoi des messages ;
* Le sous-domaine peut être entièrement délégué à l’Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à l’Adobe (personnalisés).
* Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin d’assurer une bonne délivrabilité.

### Notification push mobile

* Demandez à un développeur mobile de déployer, configurer et créer l’application mobile.
* Adobe ne fournit qu’un SDK pour collecter les informations nécessaires auprès de FCM (Android) et APNS (iOS) afin d’envoyer des payloads de message à leurs serveurs. Le code, le déploiement, la gestion et le débogage de l’application mobile sont de la responsabilité du client.

### Webapps (facultatif)

* Peut déléguer un sous-domaine supplémentaire pour le désabonnement et les landing pages hébergés par Campaign.
* Le certificat SSL est vivement recommandé.

## Garde-fous

Les barrières de sécurité sont décrites ci-dessous.

### Dimensionnement du serveur d’applications

* Le stockage peut être dimensionné jusqu’à 200 millions de profils avec un potentiel de mise à l’échelle jusqu’à des profils 1B.
* Configurer et contrôler l’accès des utilisateurs via Adobe [!DNL Admin Console].
* Chargement de données vers [!DNL Campaign] doit être effectué par le biais de fichiers de lot :
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

* Campaign permet de s’intégrer à un fournisseur SMS. Le fournisseur est acheté par le client et intégré à la campagne d&#39;envoi de messages basés sur SMS.
* La prise en charge se fait via le protocole SMPP.
* Il existe trois (3) différents types de SMS, qu’Adobe peut tous prendre en charge :
   * SMS MT (Mobile Terminated) : un SMS émis par Adobe [!DNL Campaign] vers les téléphones mobiles par l&#39;intermédiaire du fournisseur SMPP.
   * SMS MO (Mobile Originated) : un SMS envoyé par un mobile pour Adobe [!DNL Campaign] par l&#39;intermédiaire du fournisseur SMPP.
   * SMS SR (Status Report) ou DR ou DLR (Delivery Receipt) : un accusé de réception envoyé par le mobile à l&#39;Adobe. [!DNL Campaign] par l&#39;intermédiaire du fournisseur SMPP indiquant que le SMS a bien été reçu. Adobe [!DNL Campaign] peut également recevoir un SR indiquant que le message n&#39;a pas pu être diffusé, souvent avec une description de l&#39;erreur.

## Étapes de mise en œuvre

Consultez le guide de prise en main pour la [Mise en œuvre d’Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=fr).

## Documentation connexe

* [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Description du produit Campaign v8](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/launch.html)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html)
