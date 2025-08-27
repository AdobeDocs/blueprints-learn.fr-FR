---
title: Plan directeur de Campaign v8, Campaign et Platform
description: Découvrez le plan directeur de Campaign v8.
solution: Campaign,Campaign v8
version: Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 31%

---

# Plan directeur de Campaign v8

Adobe Campaign v8 est une plateforme de gestion de campagnes de nouvelle génération conçue pour les canaux marketing traditionnels tels que les e-mails et le publipostage direct. Il offre des fonctionnalités ETL et de gestion des données performantes pour prendre en charge une segmentation et un ciblage d’audience complexes, ainsi qu’un puissant moteur d’orchestration pour créer des programmes marketing multipoint pilotés par lots.

Il comprend également un serveur de messagerie en temps réel évolutif qui permet des communications transactionnelles (réinitialisations de mot de passe, confirmations de commande et accusés de réception électroniques) en acceptant des payloads complets de systèmes externes pour une diffusion immédiate.

## Cas d’utilisation

>[!BEGINTABS]

>[!TAB Exécution de campagnes par lots]

- Concevez et diffusez des campagnes marketing planifiées à grande échelle par e-mail, SMS et courrier.
- Idéal pour les bulletins promotionnels, les newsletters et les offres saisonnières avec une segmentation et un ciblage complexes.

>[!TAB Multi-Touch Orchestration]

- Créez des programmes à plusieurs étapes et multicanaux qui guident les clients à travers un parcours marketing prédéfini.
- Prend en charge la reprise d’audience, la logique conditionnelle et les transitions temporelles.

>[!TAB Data Management et ETL]

- Ingérez, transformez et gérez les données clients provenant de diverses sources pour prendre en charge un ciblage précis.
- Permet la création de schémas personnalisés, de champs calculés et de définitions d’audience.

>[!TAB Messages transactionnels]

- Envoyez des messages prédéfinis en temps réel déclenchés par des systèmes externes (par exemple, réinitialisations de mot de passe, confirmations de commande, accusés de réception électroniques).
- Utilise un serveur de messagerie évolutif qui accepte les payloads complètes des systèmes informatiques pour une diffusion immédiate.

>[!ENDTABS]

<br>

## Diagrammes d’architecture

En savoir plus sur les [modèles de déploiement de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Déploiement Campaign Grands comptes (FFDA)

<img src="images/campaign-v8-ffda.svg" alt="Architecture de référence pour le plan directeur de déploiement de Campaign v8 (FFDA)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Déploiement FDA Campaign v8

<img src="images/campaign-v8-fda.svg" alt="Architecture de référence pour le plan directeur de Campaign v8 (FDA)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Modèles d’intégration

| Scénario | Description | Considérations techniques |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform] avec Adobe [!DNL Campaign]](rtcdp-and-campaign-v8.md) | Montre comment Adobe Experience Platform, ainsi que son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe [!DNL Campaign] pour proposer des conversations personnalisées | <ul><li>Partage des profils et des audiences du [!DNL Real-Time CDP] vers Adobe [!DNL Campaign] à l&#39;aide de l&#39;échange de fichiers dans le cloud et des workflows d&#39;ingestion de [!DNL Campaign] Adobe </li><li>Partagez facilement les données de diffusion et d’interaction des conversations client dans le [!DNL Real-Time CDP] à partir d’Adobe [!DNL Campaign] pour améliorer le profil client en temps réel et fournir des rapports cross-canal sur les campagnes de messagerie</li></ul> |
| [[!DNL Journey Optimizer] avec Adobe [!DNL Campaign]](ajo-and-campaign-v8.md) | Indique comment utiliser Adobe Journey Optimizer pour orchestrer des expériences 1:1 à l’aide du profil client en temps réel et tirer parti du système de messagerie transactionnelle Adobe [!DNL Campaign] natif pour envoyer le message | <ul><li>Il peut envoyer jusqu’à 1 million de messages par heure via le serveur de messagerie en temps réel.<li>Aucune limitation n’est effectuée à partir de [!DNL Journey Optimizer]. Assurez-vous donc que l’architecte d’entreprise avant-vente procède à une vérification technique.</li><li>La gestion des décisions n’est pas pris en charge dans les payloads de Campaign v8.</li></ul> |

<br>

## Conditions préalables

Les conditions préalables suivantes sont requises pour ce plan directeur.

### Serveur d’applications et serveur de messagerie en temps réel

- La console cliente Adobe [!DNL Campaign] est nécessaire pour interagir et utiliser le logiciel [!DNL Campaign] v8. Il s’agit d’un client Windows qui utilise des protocoles Internet standard (SOAP, HTTP, etc.). Assurez-vous que les autorisations nécessaires sont activées dans votre organisation pour distribuer, installer et exécuter des logiciels.

- Listes autorisées des adresses IP :
   - Identifiez les plages d’adresses IP que tous les utilisateurs utilisent lors de l’accès à la console cliente.
   - Identifiez les systèmes d’entreprise autorisés à communiquer avec le serveur de messagerie en temps réel et assurez-vous qu’ils disposent d’une adresse IP ou d’une plage d’adresses IP attribuée de manière statique que vous pouvez inscrire sur la liste autorisée.
   - Elles peuvent être configurées et contrôlées dans le Panneau de contrôle de Campaign.
- Gestion des clés sFTP :
   - Préparez les clés publiques SSH de façons à ce qu’elles soient utilisables avec le sFTP fourni par Campaign. Elles peuvent être configurées et contrôlées dans le Panneau de contrôle de Campaign.

### E-mail

- disposer d’un sous-domaine prêt à être utilisé pour l’envoi de messages ;
- Le sous-domaine peut soit être entièrement délégué à Adobe (recommandé), soit être utilisé pour pointer vers des serveurs DNS spécifiques à Adobe (personnalisés).
- L’enregistrement TXT Google est nécessaire pour chaque sous-domaine afin d’assurer une bonne délivrabilité.

### Notification push mobile

- Demandez à un développeur ou une développeuse mobile de déployer, configurer et créer l’application mobile.
- Adobe ne fournit qu’un SDK pour collecter les informations nécessaires auprès de FCM (Android) et APNS (iOS) afin d’envoyer des payloads de message à leurs serveurs. La manière dont l’application mobile doit être codée, déployée, gérée et déboguée relève de la responsabilité du client.

### Webapps (facultatif)

- Peut déléguer un sous-domaine supplémentaire pour le désabonnement et les landing pages hébergés par Campaign.
- Le certificat SSL est vivement recommandé.

<br>

## Garde-fous

### Dimensionnement du serveur d’applications

- Le stockage peut être étendu jusqu&#39;à 200 millions de profils avec la possibilité d&#39;étendre jusqu&#39;à 1 milliard de profils.
- Configurez et contrôlez l’accès des utilisateurs et utilisatrices via Adobe [!DNL Admin Console].
- Le chargement des données dans [!DNL Campaign] doit s’effectuer par le biais de fichiers de lots :
   - La prise en charge du chargement des données d’API est principalement destinée à la gestion des profils ou des objets simples dans la base de données (c’est-à-dire la création et la mise à jour). Il n’est pas destiné à être utilisé pour le chargement de gros volumes de données ou d’opérations de type batch.
   - L’utilisation d’API pour lire des données à des fins d’application personnalisée n’est pas prise en charge.
   - Les données chargées via l’API sont mises en scène dans la base de données de l’application, puis répliquées toutes les heures dans la base de données Cloud.
- Des limites aux appels API s’appliquent. En savoir plus dans la Description du produit [Adobe Campaign](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Dimensionnement du serveur de messagerie par lots

- Peut s’adapter pour gérer jusqu’à 20 millions de messages par heure.

### Dimensionnement du serveur de messagerie en temps réel

- Peut envoyer jusqu’à 1 million de messages par heure.
- Deux serveurs de messagerie en temps réel sont configurés par défaut. Il est possible d’étendre la configuration à jusque huit serveurs de messagerie en temps réel.

### Configuration des SMS

- Campaign permet de s’intégrer à un fournisseur SMS. Le fournisseur est fourni par le client et intégré à Campaign pour l&#39;envoi de messages SMS.
- La prise en charge s’effectue via le protocole SMPP.
- Il existe trois (3) différents types de SMS, qu’Adobe peut tous prendre en charge :
   - SMS MT (Mobile Terminated) : un SMS émis par Adobe [!DNL Campaign] vers les téléphones portables par l&#39;intermédiaire du fournisseur SMPP.
   - SMS MO (Mobile Originated) : un SMS envoyé par un téléphone mobile à Adobe [!DNL Campaign] par l&#39;intermédiaire du fournisseur SMPP.
   - SMS SR (Status Report) ou DR ou DLR (Delivery Receipt) : un accusé de réception envoyé par le téléphone mobile à Adobe [!DNL Campaign] par l&#39;intermédiaire du fournisseur SMPP indiquant que le SMS a été reçu avec succès. Adobe [!DNL Campaign] peut également recevoir des SR indiquant que le message n’a pas pu être remis, souvent avec une description de l’erreur.

<br>

## Étapes de mise en œuvre

Consultez le guide de prise en main pour la [Mise en œuvre d’Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html).

## Documentation connexe

- [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html)
- [Description du produit Campaign v8](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
- [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/launch.html)
- [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html)