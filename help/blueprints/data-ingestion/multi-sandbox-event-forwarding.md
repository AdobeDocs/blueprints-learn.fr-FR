---
title: Collecte de données de transfert d’événement multi-environnements de test
description: Découvrez comment les données collectées avec les SDK web et mobiles Experience Platform peuvent être configurées pour collecter un seul événement et les transférer vers plusieurs environnements de test Experience Platform.
solution: Data Collection
kt: 7202
source-git-commit: e9a9abeaa722bb2f9a232f4e861b1b5eae86edd1
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 4%

---


# Collecte de données de transfert d’événement multi-environnements de test

Ce plan directeur montre comment les données collectées avec les SDK web et mobiles Experience Platform peuvent être configurées pour collecter un seul événement et les transférer vers plusieurs environnements de test AEP. Ce plan directeur est spécifique à la collecte de données multi-environnement de test qui utilise [!UICONTROL Transfert d’événement] pour atteindre cet objectif.

En plus de répliquer l’événement avec [!UICONTROL Transfert d’événement] fonctionnalités, vous pouvez ajouter, filtrer ou manipuler les données collectées d’origine qui répondent aux exigences d’autres environnements de test.

[!UICONTROL Transfert d’événement] utilise une propriété distincte qui contient la propriété [!UICONTROL Éléments de données], [!UICONTROL Règles], et [!UICONTROL Extensions] nécessaire pour répondre à vos besoins en données. Avec un événement entrant, votre [!UICONTROL Transfert d’événement] peut collecter les données et les gérer selon les besoins avant le transfert.

Votre environnement de test de destination nécessite un point de terminaison de diffusion HTTP en continu configuré utilisé par l’Adobe. [!UICONTROL Connecteur cloud] extension .

## Cas d’utilisation

* Création de rapports de données globales : lors de l’utilisation de plusieurs environnements de test pour isoler les environnements d’exploitation et de la nécessité de consolider la collecte de données sur un environnement de test pour la création de rapports entre environnements de test. Routage d’un événement Experience Edge par [!UICONTROL Transfert d’événement] à un environnement de test de création de rapports permet à chaque environnement de test d’envoyer des données telles qu’elles sont collectées en temps réel à un environnement de test de création de rapports.

* Gérez la collecte de données dans les sandbox en fonction de différentes règles de données pour chaque sandbox.

## Applications

* [!DNL Experience Platform] sur la collecte de données
* [!UICONTROL Transfert d’événement]
* AEP [!UICONTROL Extension]
* [!UICONTROL Extension Cloud Connector]

## Considérations

Avec [!UICONTROL Transfert d’événement] pour envoyer des données à plusieurs environnements de test, vous devez tenir compte des points à prendre en compte dans l’architecture de votre solution.

### Aucune donnée HIPAA

[!UICONTROL Transfert d’événement] n’est pas considéré comme prêt pour HIPAA et ne doit pas être utilisé dans les cas d’utilisation HIPAA où des données HIPAA sont collectées. Toutefois, l’infrastructure utilisée pour [!UICONTROL Transfert d’événement] est considéré comme prêt par le HIPAA et est seul à la discrétion du client. Lors de votre [!UICONTROL Transfert d’événement] La propriété de balise réside dans le [!UICONTROL Transfert d’événement] système, l’intégralité de la payload de données collectée est envoyée à la variable [!UICONTROL Transfert d’événement] système pour le traitement. C&#39;est ce processus qui fait [!UICONTROL Transfert d’événement] pour les cas d’utilisation HIPAA. Avec la charge utile entière fournie à la variable [!UICONTROL Transfert d’événement] système, cela inclut toutes les valeurs HIPAA. Même si la variable [!UICONTROL Transfert d’événement] Les règles filtrent ces données avant de les envoyer à sa destination, car les données HIPAA sont toujours envoyées vers une infrastructure non compatible avec le HIPAA. Toutefois, les données de payload ne sont jamais stockées et ne sont qu’un passage à l’autre.

### Différents flux de données et points de terminaison de diffusion en continu

Lorsque les données transitent par les flux de données à partir de la variable [!UICONTROL Plateforme Edge Network], lors de l’utilisation de [!UICONTROL Transfert d’événement] dans un autre environnement de test AEP, vous devez ne jamais utiliser le même flux de données ou point de terminaison de diffusion en continu que celui qui crée la collection d’origine. Cela peut être préjudiciable à l’instance AEP et potentiellement déclencher une situation de déni de service.

### Volume estimé de trafic

Les volumes de trafic doivent être examinés dans chaque cas d’utilisation. Ceci est important, car des volumes élevés peuvent entraîner une situation de ralentissement et les clients sont avertis si cela se produit.

## Architecture

![Environnement de test multiple [!UICONTROL Transfert d’événement]](assets/multi-sandbox-data-collection.png)

1. Collecte et envoi de données d’événement à la variable [!UICONTROL Plateforme Edge Network] est requis pour utiliser [!UICONTROL Transfert d’événement]. Les clients peuvent utiliser des balises d’Adobe pour le côté client ou le [!UICONTROL API du serveur réseau Edge Platform] pour la collecte de données serveur à serveur. Le [!UICONTROL API réseau Edge Platform] peut fournir une fonctionnalité de collecte serveur à serveur. Toutefois, cela nécessite un modèle de programmation différent à mettre en oeuvre. Voir [Présentation de l’API du serveur réseau Edge](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. Les payloads collectées sont envoyées de l’implémentation des balises à l’ [!UICONTROL Plateforme Edge Network] au [!UICONTROL Transfert d’événement] service et traité par lui-même [!UICONTROL Éléments de données], [!UICONTROL Règles] et [!UICONTROL Actions]. Vous pouvez en savoir plus sur les différences entre les [Balises et [!UICONTROL Transfert d’événement]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. Un [!UICONTROL Transfert d’événement] est également requise pour recevoir les données d’événement collectées de la propriété [!UICONTROL Plateforme Edge Network]. Si ces données d’événement ont été envoyées à Platform Edge Network par une implémentation de balises déployée ou une collection serveur à serveur. Les auteurs définissent les éléments de données, les règles et les actions utilisés pour enrichir les données d’événement avant le transfert vers le second environnement de test. Envisager d’utiliser le code personnalisé [!DNL JavaScript] élément de données pour faciliter la structure de vos données pour l’ingestion des environnements de test. Combinées aux fonctionnalités de préparation de données Platform, vous disposez de plusieurs options pour gérer votre structure de données.

1. Actuellement, l’utilisation de l’Adobe [!UICONTROL Extension Cloud Connector] est requis dans la variable [!UICONTROL Transfert d’événement] Propriété. Une fois que les règles traitent ou enrichissent les données d’événement, Cloud Connector est utilisé dans un appel de récupération configuré pour un POST qui envoie la charge utile au second environnement de test.

1. Un point de terminaison de diffusion en continu pour l’ingestion des données est requis pour le second environnement de test. Vous pouvez également tenir compte des fonctionnalités de préparation de données dans AEP pour faciliter l’ingestion et le mappage des [!UICONTROL Transfert d’événement] payloads vers XDM. Reportez-vous à la documentation AEP Création d’un [Connexion en continu via l’API HTTP à l’aide de l’interface utilisateur](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=fr)
