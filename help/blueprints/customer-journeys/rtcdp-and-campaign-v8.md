---
title: Modèle d’intégration de Real-Time CDP avec Adobe Campaign v8
description: Montre comment Adobe Experience Platform, son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign v8 pour diffuser des conversations personnalisées.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 72%

---

# [!DNL Real-Time CDP] avec Adobe [!DNL Campaign] modèle d’intégration v8

Présente comment l’Adobe [!DNL Experience Platform] et son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées.

## Applications

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architecture

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Architecture de référence du modèle d’intégration de la messagerie par lots et d’Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Conditions préalables

* Le client doit disposer d’une session Experience Cloud configurée avec une organisation IMS valide
* Adobe Experience Platform et [!DNL Campaign] sont recommandés pour être configurés dans la même organisation IMS pour une URL de connexion unique.
* Le client doit être configuré pour l’instance V8 de [!DNL Campaign].
* Le client doit être éligible et avoir accès à RTCDP, aux sources et aux destinations.
* Le contexte du produit Adobe [!DNL Campaign] doit exister
<br>

## Étapes de mise en œuvre

Reportez-vous à la documentation suivante sur la configuration du connecteur source Campaign v8 sur Adobe Experience Platform et du connecteur de destination Real-time Customer Data Platform sur Campaign v8.
[Connecteurs Campaign et AEP](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=fr)

## Garde-fous

### Adobe Campaign

* Reportez-vous à la documentation du connecteur source Campaign : [Connecteur source Campaign](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=fr)
* Ne prend en charge que les déploiements d’une seule unité organisationnelle d’Adobe Campaign.


### Partage de segments Real-time Customer Data Platform Experience Platform

* Reportez-vous au connecteur de destination RTCDP Campaign : [Connexion à RTCDP Campaign](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=fr)

* Voir les garde-fous concernant l’ingestion des données et les profils pour AEP - [Lien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
