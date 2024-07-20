---
title: Collecte de données pour le transfert d’événement multi-sandbox
description: Découvrez comment les données collectées avec les SDK web et mobiles Experience Platform peuvent être configurées pour collecter un seul événement et transférées vers plusieurs sandbox Experience Platform.
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 55%

---

# Collecte de données pour le transfert d’événement multi-sandbox

Ce plan directeur montre comment les données collectées avec les [!DNL Experience Platform] SDK Web et mobiles peuvent être configurées pour collecter un seul événement et les transférer vers plusieurs environnements de test AEP. Ce plan directeur est spécifique à la collecte de données multi-sandbox qui utilise le [!UICONTROL transfert d’événement] pour atteindre cet objectif.

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

[!UICONTROL Le transfert d’événement] n’est pas considéré comme prêt pour HIPAA et ne doit pas être utilisé dans les cas pratiques HIPAA où des données HIPAA sont collectées.

Cependant, l’infrastructure utilisée pour le [!UICONTROL transfert d’événement] est considérée comme prête pour le HIPAA et est uniquement à la discrétion du client. Bien que la propriété de balise [!UICONTROL Transfert d’événement] se trouve dans le système de [!UICONTROL transfert d’événement], la payload de données collectée est intégralement envoyée au système de [!UICONTROL transfert d’événement] pour traitement. Ce processus définit le [!UICONTROL transfert d’événement] concernant les cas pratiques HIPAA. Avec la charge utile entière fournie au système de [!UICONTROL transfert d’événement], ce processus inclut toutes les valeurs HIPAA. Même si les règles de [!UICONTROL transfert d’événement] filtrent ces données avant de les envoyer à sa destination, ces données HIPAA sont toujours envoyées vers une infrastructure non compatible avec HIPAA. Toutefois, les données de payload ne sont jamais stockées et ne sont qu’un passage à l’étape suivante.

### Trains de données et points d’entrée de streaming différents

Lorsque les données transitent par les flux de données de [!DNL Platform Edge Network], lors de l’utilisation du [!UICONTROL transfert d’événement] vers un autre environnement de test AEP, il est nécessaire de ne jamais utiliser le même flux de données ou point de terminaison de diffusion en continu que le flux de données qui crée la collection d’origine. Cela peut être préjudiciable à l’instance AEP et potentiellement déclencher une situation de déni de service.

### Volumes de trafic estimés

Les volumes de trafic doivent être examinés dans chaque cas d’utilisation. Il s’agit d’un facteur important, dans la mesure où des volumes élevés peuvent entraîner une situation de ralentissement. Une notification est alors envoyée aux clientes et clients.

## Architecture

![[!UICONTROL Transfert d’événement]](assets/multi-sandbox-data-collection.png) multi-sandbox 

1. La collecte et l&#39;envoi de données d&#39;événement à [!DNL Platform Edge Network] sont nécessaires pour utiliser le [!UICONTROL transfert d&#39;événement]. Vous pouvez utiliser des balises d’Adobe pour la collecte de données côté client ou [!DNL Platform Edge Network Server API] pour la collecte de données serveur à serveur.

   [!DNL Platform Edge Network API] peut fournir une fonctionnalité de collecte serveur à serveur. Toutefois, cela nécessite un modèle de programmation différent à mettre en oeuvre. Voir [Vue d’ensemble de l’API Platform Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr).

1. Les payloads collectées sont envoyées de l’implémentation des balises vers le service [!DNL Platform Edge Network] vers le [!UICONTROL transfert d’événement] et traitées par ses propres [!UICONTROL éléments de données], [!UICONTROL règles] et [!UICONTROL actions]. Pour en savoir plus sur les différences, voir [Balises et [!UICONTROL Transfert d’événement]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr#differences-from-tags).

1. Une propriété [!UICONTROL Event Forwarding] est également nécessaire pour recevoir les données d’événement collectées de [!DNL Platform Edge Network], que ces données d’événement aient été envoyées à [!DNL Platform Edge Network] par une implémentation de balises déployée ou une collection serveur à serveur.

   Les auteurs définissent les éléments de données, les règles et les actions utilisés pour enrichir les données d’événement avant le transfert vers le second sandbox. Pensez à utiliser l’élément de données [!DNL JavaScript] Custom Code pour faciliter la structuration de vos données pour l’ingestion des sandbox. Avec les fonctionnalités de préparation de données Platform, vous disposez de plusieurs options pour gérer votre structure de données.

1. Actuellement, l’utilisation de l’[!UICONTROL extension Adobe Cloud Connector] est requise dans la propriété de [!UICONTROL transfert d’événement]. Après le traitement des règles ou l’enrichissement des données d’événement, [!UICONTROL Cloud Connector] est utilisé dans un appel de récupération configuré pour un POST, envoyant la charge utile au second environnement de test.

1. Un point de terminaison de diffusion en continu pour l’ingestion des données est requis pour le second environnement de test. Vous pouvez également envisager des fonctionnalités [!UICONTROL Data Prep] dans AEP pour faciliter l’ingestion et le mappage des charges utiles [!UICONTROL Event Forwarding] vers XDM. Reportez-vous à la documentation AEP Création d’une [connexion en continu via l’API HTTP à l’aide de l’interface utilisateur](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=fr)
