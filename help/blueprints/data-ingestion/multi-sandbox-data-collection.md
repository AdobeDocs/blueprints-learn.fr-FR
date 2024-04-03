---
title: Plan directeur de la collecte de données pour le transfert d’événement multi-sandbox
description: Diffusez les données collectées en [!DNL Experience Platform] SDK (AEP) vers plusieurs environnements de test à l’aide du transfert d’événements
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 60%

---

# Plan directeur de collecte de données de transfert d’événement multi-environnements de test

Le plan directeur de la collecte de données de transfert d’événement multi-environnement indique comment les données sont collectées avec Adobe. [!DNL Experience Platform] Les SDK web et mobiles peuvent être configurés pour collecter un seul événement et le transférer vers plusieurs [!DNL Experience Platform] (AEP) environnements de test. Ce plan directeur est un cas d’utilisation spécifique qui utilise la fonctionnalité de transfert d’événement des balises d’Adobe.

En plus de répliquer l’événement, grâce aux fonctionnalités de transfert d’événement vous pouvez ajouter, filtrer ou manipuler les données collectées d’origine qui répondent aux exigences d’autres sandbox. Par exemple, la sandbox A doit recevoir tous les éléments de données d’événement et la sandbox B ne doit recevoir que des données autres que les informations d’identification personnelle.

Le transfert d’événements utilise une propriété Tag distincte qui contient les éléments de données, les règles et les extensions nécessaires pour répondre à vos besoins en données. Avec un événement entrant, votre propriété de transfert d’événement peut collecter les données et les gérer selon les besoins avant le transfert.

Votre environnement de test de destination doit avoir un point de terminaison HTTP Streaming qui sera utilisé par l’extension HTTPS de transfert d’événement.

## Cas d’utilisation

* Création de rapports de données globales : lorsque vous utilisez plusieurs sandbox pour isoler les environnements d’exploitation et la nécessité de consolider la collecte de données sur un sandbox pour la création de rapports entre sandbox. Le transfert d’événement à une sandbox de création de rapports permet à chaque environnement de sandbox d’envoyer des données telles qu’elles sont collectées en temps réel à une sandbox de création de rapports.
* Gérez la collecte de données dans les sandbox en fonction de différentes règles de données pour chaque sandbox. Les environnements qui nécessitent le filtrage de données sensibles telles que les services de santé et financiers

## Applications

* Adobe [!DNL Experience Platform] Collecte de données

## Architecture

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Architecture de référence pour le transfert d’événements multi-sandbox" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

1. Les auteurs de balises définissent une propriété de balise ainsi qu’une propriété de transfert d’événement. Ici, les auteurs définissent les éléments de données, les règles et les actions qui gèrent la collecte de données. Pour rappel, le code de propriété de balise s’exécute sur le client et est distribué par un hôte CDN. La variable [!UICONTROL Propriété de transfert d’événement] s’exécute sur l’Adobe. [!DNL Edge Server].

1. Les données collectées sur le client sont envoyées au [!DNL Edge Network]. Les clients ont également la possibilité d’envoyer des données à leur propre serveur en premier lieu en tant que méthode de collecte côté serveur. Le SDK web peut fournir une fonctionnalité de collecte entre les serveurs. Cela nécessite toutefois la mise en œuvre d’un modèle de programmation différent. Consultez la documentation **[!DNL Edge Network]Présentation de l’API de serveur** below

1. Plateforme [!DNL Edge Network] reçoit les payloads de collecte de données et orchestre le flux de données vers les systèmes requis tels que Target et Analytics.

1. Les éléments de données de propriété du transfert d’événement sont utilisés pour accéder aux données d’événement qui arrivent dans le payload. Les règles peuvent également être utilisées pour manipuler les données d’événement en fonction des besoins avant le transfert. Par exemple, le formatage des données dans le fichier XDM requis pour l’ingestion de données par flux

1. Le transfert d’événement fournit l’extension HTTPS qui permet de transférer vos données d’événement vers un point d’entrée HTTPS.

1. Le sandbox 2 est configuré avec un point d’entrée de streaming qui reçoit l’événement transféré.

## Documentation connexe

* [Documentation sur le transfert d’événement](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr)
* [Vidéos sur le transfert d’événement](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=fr)
* Tutoriel relatif au [cours sur le transfert d’événement](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=fr) du SDK web
* [[!DNL Experience Platform] Présentation du SDK Web](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
* [[!DNL Edge Network] Présentation de l’API de serveur](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr)

## Articles de blog connexes

* [Amélioration des performances du site web avec Adobe [!DNL Experience Platform] SDK Web et [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Résoudre les problèmes de mise en oeuvre avec Adobe [!DNL Experience Platform] SDK Web et [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe [!DNL Experience Platform] SDK Web pour la gestion de l’audience](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] SDK Web - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe [!DNL Experience Platform] Scénarios de migration du SDK Web pour Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Unifier votre Adobe [!DNL Experience Platform] Services avec Adobe [!DNL Experience Platform] SDK Web](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Accélérer le développement de vos applications mobiles avec Adobe [!DNL Experience Platform] SDK Mobile et Launch](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Simplifiez les workflows client avec le SDK web d’Adobe Experience Platform](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
