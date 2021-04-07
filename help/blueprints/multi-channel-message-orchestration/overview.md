---
title: 'Orchestration de messages à plusieurs canaux '
description: Diffusez des expériences client individuelles et ponctuelles sur plusieurs écrans.
solution: Experience Platform
kt: null
thumbnail: null
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 2%

---

# Orchestration de messages à plusieurs canaux

L’orchestration de messages à plusieurs canaux montre comment les marques peuvent interagir et communiquer de manière proactive avec leurs clients par le biais de canaux tels que les courriels, les SMS et les alertes mobiles.

Les outils d’orchestration peuvent s’intégrer à d’autres canaux d’interaction (tels que les canaux entrants) pour la personnalisation Web et mobile en partageant l’état d’audience avec les autres moteurs de décision des canaux. Divers facteurs permettent de déterminer les applications et les options de déploiement à utiliser, comme par exemple si l’interaction client est déclenchée ou planifiée, les données nécessaires au ciblage et à la personnalisation, etc. Ces facteurs donnent lieu à divers scénarios et options de déploiement possibles lors de la création de la fonctionnalité d’orchestration des messages.

## Plans directeurs


| Plan directeur | Description | Applications Experience Cloud |
|---|---|---|
| **Traitement par lots et messages transactionnels** | <ul><li>Création et exécution de campagnes sortantes planifiées et par lots</li><li>Livraison de messages transactionnels</li></ul> | <ul><li>Adobe Campaign Classic et Managed Services</li><li>Adobe Campaign Standard</li></ul> |
| **[Messagerie par lots et Adobe Experience Platform](batch-messaging.md)** | <ul><li>Exécuter des campagnes de messagerie par lots et planifiées à l’aide de Adobe Experience Platform en tant que centre central des profils clients et de la segmentation</li></ul> | <ul><li> de la plateforme de données clients en temps réel</li><li>Adobe Campaign Classic, Managed Services ou Campaign Standard</li><li>Fournisseur de messagerie tiers pris en charge</li></ul> |
| **[Messagerie et Adobe Experience Platform déclenchées](triggered-messaging.md)** | <ul><li>Exécuter des messages déclenchés et en flux continu à l’aide de Adobe Experience Platform en tant que hub central pour la diffusion en flux continu de données, de profils clients et de segmentation, avec Journey Orchestration pour l’orchestration en flux continu des parcours et la diffusion des messages</li></ul> | <ul><li>Adobe Experience Platform</li><li>Journey Orchestration</li><li>Adobe Campaign ou autre application tierce pour la diffusion de messages</li></ul> |
