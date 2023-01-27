---
title: Plan directeur de collecte de données de transfert d’événements multi-sandbox
description: Diffusion en continu des données collectées par les SDK Experience Platform vers plusieurs sandbox à l’aide du transfert d’événements
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 73%

---

# Plan directeur de collecte de données de transfert d’événements multi-sandbox

Le plan directeur de la collecte de données de transfert d’événements multi-sandbox indique comment les données collectées avec les SDK web et mobiles Adobe Experience Platform peuvent être configurées pour collecter un seul événement et les transférer vers plusieurs sandbox AEP. Ce plan directeur est un cas d’utilisation spécifique qui utilise la fonctionnalité de transfert d’événement des balises d’Adobe.

En plus de répliquer l’événement, grâce aux fonctionnalités de transfert d’événement vous pouvez ajouter, filtrer ou manipuler les données collectées d’origine qui répondent aux exigences d’autres sandbox. Par exemple, la sandbox A doit recevoir tous les éléments de données d’événement et la sandbox B ne doit recevoir que des données autres que les informations d’identification personnelle.

Le transfert d’événements utilise une propriété de balise distincte qui contient les éléments de données, les règles et les extensions nécessaires à vos besoins de données. Avec un événement entrant, votre propriété de transfert d’événement peut collecter les données et les gérer selon les besoins avant le transfert.

La boîte de réception de votre destination nécessite un point de sortie de diffusion en continu HTTP qui serait utilisé par l’extension HTTPS de transfert d’événement.



## Cas d’utilisation

* Création de rapports de données globales : lorsque vous utilisez plusieurs sandbox pour isoler les environnements d’exploitation et la nécessité de consolider la collecte de données sur une sandbox pour la création de rapports entre sandbox. Le transfert d’événement à une sandbox de création de rapports permet à chaque environnement de sandbox d’envoyer des données telles qu’elles sont collectées en temps réel à une sandbox de création de rapports.
* Gérez la collecte de données dans les sandbox en fonction de différentes règles de données pour chaque sandbox. Les environnements qui nécessitent le filtrage de données sensibles telles que les services de santé et financiers

## Applications

* Collecte de données dʼAdobe Experience Platform

## Architecture

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Architecture de référence pour le transfert d’événements multi-sandbox" style="width:90%; border:1px solid #4a4a4a" />

1. Les auteurs de balises définissent une propriété de balise ainsi qu’une propriété de transfert d’événement. Ici, les auteurs définissent les éléments de données, les règles et les actions qui gèrent la collecte de données. N’oubliez pas que le code de propriété de balise s’exécute sur le client et est distribué par un hôte CDN. Le code de propriété de transfert d’événement s’exécute sur le serveur Adobe Edge.

1. Les données collectées sur le client sont envoyées au réseau Edge. Les clients ont également la possibilité d’envoyer des données à leur propre serveur en premier lieu en suivant la méthode de collecte côté serveur.  Le SDK Web peut fournir une fonctionnalité de collecte serveur à serveur. Cela nécessite toutefois la mise en œuvre d’un modèle de programmation différent. Consultez la documentation de **présentation de l’API du serveur Edge Network** ci-dessous.

1. Platform Edge Network reçoit les payloads de collecte de données et orchestre le flux de données vers les systèmes requis tels que Target et Analytics.

1. Les éléments de données de propriété de transfert d’événement sont utilisés pour accéder aux données d’événement arrivant dans la payload. Les règles peuvent également être utilisées pour manipuler les données d’événement en fonction des besoins avant le transfert. Par exemple, le formatage des données dans le fichier XDM requis pour l’ingestion de données par flux

1. Le transfert d’événement fournit l’extension HTTPS qui permet de transférer les données d’événement vers un point de terminaison HTTPS.

1. L’environnement de test 2 est configuré avec un point de terminaison de diffusion en continu qui reçoit l’événement transféré.

## Documentation connexe

* [Documentation sur le transfert d’événement](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr)
* [Vidéos sur le transfert d’événement](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=fr)
* Tutoriel relatif au [cours sur le transfert d’événement](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=fr) du SDK web
* [Présentation du SDK Web Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
* [Présentation de l’API de serveur Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr)

## Publications de blog connexes

* [[!DNL Boosting Website Performance with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [[!DNL Solving Implementation Pain Points with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Adobe Experience Platform Web SDK — Adobe Target]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [[!DNL Adobe Experience Platform Web SDK Migration Scenarios for Adobe Analytics]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [[!DNL Unify Your Adobe Experience Platform Services with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [[!DNL Accelerate Your Mobile Application Development with Adobe Experience Platform Mobile SDK and Launch]](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [[!DNL Simplifying Customer Workflows with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
