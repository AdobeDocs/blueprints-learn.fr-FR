---
title: Collecte de données pour le transfert d’événement multi-sandbox
description: Découvrez comment les données collectées avec les SDK web et mobiles Experience Platform peuvent être configurées pour collecter un seul événement et transférées vers plusieurs sandbox Experience Platform.
solution: Data Collection
kt: 7202
exl-id: 3d9d312a-50b6-435f-b277-076e0c442a5f
source-git-commit: cb36f47232261d6ddc6659949272c9832baec0da
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 100%

---

# Collecte de données pour le transfert d’événement multi-sandbox

Ce plan directeur indique comment les données collectées avec les SDK web et mobiles Experience Platform peuvent être configurées pour collecter un seul événement et les transférer vers plusieurs sandbox AEP. Ce plan directeur est spécifique à la collecte de données multi-sandbox qui utilise le [!UICONTROL transfert d’événement] pour atteindre cet objectif.

En plus de répliquer l’événement avec les fonctionnalités de [!UICONTROL transfert d’événement], vous pouvez ajouter, filtrer ou manipuler les données collectées d’origine qui répondent aux exigences d’autres sandbox.

Le [!UICONTROL transfert d’événement] utilise une propriété distincte qui contient les [!UICONTROL éléments de données], les [!UICONTROL règles] et les [!UICONTROL extensions] nécessaires à vos besoins en termes de données. Avec un événement entrant, votre propriété [!UICONTROL Transfert d’événement] peut collecter les données et les gérer selon les besoins avant le transfert.

Votre sandbox de destination nécessite la configuration d’un point d’entrée de streaming HTTP utilisé par l’extension [!UICONTROL Cloud Connector].

## Cas d’utilisation

* Reporting de données globales : lorsque vous utilisez plusieurs sandbox pour isoler les environnements d’exploitation et la nécessité de consolider la collecte de données sur un sandbox pour le reporting entre sandbox. Le routage d’un événement Experience Edge vers un sandbox de reporting via le [!UICONTROL transfert d’événement] permet à chaque environnement de sandbox d’envoyer des données telles qu’elles sont collectées en temps réel à un sandbox de reporting.

* Gérez la collecte de données dans les sandbox en fonction de différentes règles de données pour chaque sandbox.

## Applications

* [!DNL Experience Platform] sur la collecte de données
* [!UICONTROL Transfert d’événement]
* [!UICONTROL Extension] AEP
* [!UICONTROL Extension Cloud Connector]

## Considérations

Le [!UICONTROL transfert d’événement] étant la méthode d’envoi de données vers plusieurs sandbox, certains éléments doivent être pris en compte avec votre architecture de solution.

### Aucune donnée HIPAA

[!UICONTROL Le transfert d’événement n’est pas considéré comme prêt pour HIPAA et ne doit pas être utilisé dans les cas d’utilisation HIPAA où des données HIPAA sont collectées.] Cependant, l’infrastructure utilisée pour le [!UICONTROL transfert d’événement]  est considérée comme prête pour HIPAA et est uniquement à la discrétion du client ou de la cliente. Bien que la propriété de balise [!UICONTROL Transfert d’événement] se trouve dans le système de [!UICONTROL transfert d’événement], la payload de données collectée est intégralement envoyée au système de [!UICONTROL transfert d’événement] pour traitement. C’est ce processus qui rend le [!UICONTROL transfert d’événement] impropre aux cas d’utilisation HIPAA. Avec la payload expédiée intégralement au système de [!UICONTROL transfert d’événement], toutes les valeurs HIPAA seraient incluses. Bien que les règles de [!UICONTROL transfert d’événement] filtrent ces données avant de les envoyer à destination, ces données HIPAA sont toujours envoyées vers une infrastructure non compatible avec la loi HIPAA. Toutefois, les données de payload ne sont jamais stockées et ne sont qu’un passthrough.

### Trains de données et points d’entrée de streaming différents

Comme les données transitent par les flux de données de [!UICONTROL Platform Edge Network], lors de l’utilisation du [!UICONTROL transfert d’événement] vers un autre sandbox AEP, une exigence consiste à ne jamais utiliser le même train de données ou point d’entrée de streaming que le train de données qui effectue la collecte initiale. Cela peut être préjudiciable à l’instance AEP et potentiellement déclencher une situation de déni de service.

### Volumes de trafic estimés

Les volumes de trafic doivent être examinés dans chaque cas d’utilisation. Il s’agit d’un facteur important, dans la mesure où des volumes élevés peuvent entraîner une situation de ralentissement. Une notification est alors envoyée aux clientes et clients.

## Architecture

![[!UICONTROL Transfert d’événement]](assets/multi-sandbox-data-collection.png) multi-sandbox 

1. La collecte et l’envoi de données d’événement à [!UICONTROL Platform Edge Network] sont nécessaires pour utiliser le [!UICONTROL transfert d’événement]. Les clientes et clients peuvent utiliser les balises Adobe pour l’API côté client ou l’[!UICONTROL API du serveur Platform Edge Network] pour la collecte de données de serveur à serveur. L’[!UICONTROL API Platform Edge Network] peut fournir une fonctionnalité de collecte de serveur à serveur. Cela nécessite toutefois la mise en œuvre d’un modèle de programmation différent. Voir [Vue d’ensemble de l’API Platform Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr).

1. Les payloads collectées sont envoyées de l’implémentation des balises au service [!UICONTROL Transfert d’événement] en passant par [!UICONTROL Platform Edge Network], et traitées par des [!UICONTROL éléments de données], [!UICONTROL règles] et [!UICONTROL actions] spécifiques. Pour en savoir plus sur les différences entre les balises et le [!UICONTROL transfert d’événement], cliquez [ici](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr#differences-from-tags).

1. Une propriété de [!UICONTROL transfert d’événement] est également requise pour recevoir les données d’événement collectées à partir de [!UICONTROL Platform Edge Network], que ces données aient été envoyées à Platform Edge Network par une implémentation de balises déployée ou une collecte de serveur à serveur. Les auteurs définissent les éléments de données, les règles et les actions utilisés pour enrichir les données d’événement avant le transfert vers le second sandbox. Pensez à utiliser l’élément de données [!DNL JavaScript] Custom Code pour faciliter la structuration de vos données pour l’ingestion des sandbox. Avec les fonctionnalités de préparation de données Platform, vous disposez de plusieurs options pour gérer votre structure de données.

1. Actuellement, l’utilisation de l’[!UICONTROL extension Adobe Cloud Connector] est requise dans la propriété de [!UICONTROL transfert d’événement]. Une fois que les règles traitent ou enrichissent les données d’événement, l’extension Cloud Connector est utilisée dans un appel de récupération configuré pour une méthode POST qui envoie la payload au deuxième sandbox.

1. Un point d’entrée de streaming pour l’ingestion des données est requis pour le deuxième sandbox. Vous pouvez également tenir compte des fonctionnalités de préparation des données dans AEP pour faciliter l’ingestion et le mappage des payloads de [!UICONTROL transfert d’événement] vers XDM. Reportez-vous à la documentation AEP Création d’une [connexion en continu via l’API HTTP à l’aide de l’interface utilisateur](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=fr)
