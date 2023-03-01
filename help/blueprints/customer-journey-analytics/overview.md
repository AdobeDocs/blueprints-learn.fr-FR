---
title: Plans directeurs de Customer Journey Analytics
description: Unification et analyse des données et des comportements du client tout au long du parcours client.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
source-git-commit: dabb5ae0bf2fc186f67d4aa93a2e9e8c5bb04498
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plans directeurs de Customer Journey Analytics

Customer Journey Analytics montre comment les entreprises peuvent unifier les données et le comportement des clients à partir de divers canaux et sources d’interaction pour créer une vue d’ensemble basée sur le parcours client de toutes les interactions client. La création de rapports et d’analyses peut être réalisée dans le service applicatif Customer Journey Analytics pour évaluer et obtenir un aperçu sur les interactions client et les modèles de comportement des clients.

Vous trouverez une liste complète des cas d’utilisation de Customer Journey Analytics dans la documentation de Customer Journey Analytics disponible ici.

## Cas d’utilisation de Customer Journey Analytics

[Cas d’utilisation courants :](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=fr)

* Création et publication d’audiences sur Real-time Customer Data Platform
* Les chemins de conversion vers le haut ou le bas
* Le niveau d’engagement et de conversion sur les différents canaux
* Les contenus les plus consultés
* Les catégories et les produits les plus populaires
* Quelles campagnes ont généré une conversion et un engagement accrus
* Analyse de l’utilisation des outils pour optimiser les expériences en libre-service

## Architecture pour Customer Journey Analytics

![Diagramme d’architecture](assets/CJA.svg){zoomable=&quot;yes&quot;}

Voici quelques principaux cas d’utilisation.
| Plan directeur | Description |  Applications Experience Cloud |
|---|---|---|
| **[Analyse de parcours cross-canal](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel.html?lang=fr)**  | <ul><li>Ayez une vue consolidée unique du comportement des clients sur différents canaux en unifiant les données de diverses propriétés web, mobiles et hors ligne.</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (facultatif)</li></ul>|
| **[Publication d’audiences sur Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=fr)** | <ul><li>Créez et publiez des audiences identifiées dans Customer Journey Analytics (CJA) vers le profil client en temps réel dans Adobe Experience Platform, pour le ciblage et la personnalisation des clients. Idéal pour créer des audiences à l’aide de données historiques ou des audiences plus affinées à partir d’un filtrage granulaire et de champs calculés dans Customer Journey Analytics.</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> |
| **[Analyse du parcours de déviation des appels](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/call-center.html?lang=fr)** | <ul><li>Déterminez les comportements les plus révélateurs pour aboutir à des appels assistés par un agent en regroupant les données du centre d’appel avec des données d’interaction web, mobiles et autres.</li><li>Ces informations peuvent ensuite être utilisées pour optimiser l’expérience client et réduire le chemin vers les interactions assistées par agent grâce à un contenu et des outils en libre-service optimisés.  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Diagramme des mécanismes de sécurisation pour les plans directeurs de Customer Journey Analytics

* Pour des garde-fous détaillés et des latences de bout en bout, consultez le [document sur les garde-fous de déploiement](../experience-platform/deployment/guardrails.md)

![Diagramme des garde-fous](../experience-platform/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Articles de blog connexes

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
