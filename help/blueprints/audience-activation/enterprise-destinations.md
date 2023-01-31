---
title: Plan directeur d’activation d’audience et de profil vers des destinations de diffusion en continu de fichiers et d’entreprise
description: Activation d’audiences et de profils vers des destinations d’entreprise
solution: Real-Time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 66%

---

# Plan directeur d’activation d’audience et de profil vers des destinations de diffusion en continu de fichiers et d’entreprise

Partage des modifications et événements de profil et d’audience par flux ou par lots à partir de [!UICONTROL Real-time Customer Data Platform] aux entrepôts de données et aux applications d’entreprise. Ces événements de profil et d’audience peuvent être utilisés pour lancer une action de vente ou d’assistance au client, comme le suivi d’un processus d’application abandonné ou d’un enregistrement de webinaire, ou pour mettre à jour les applications d’entreprise avec les derniers attributs du client et les informations provenant de [!UICONTROL Real-time Customer Data Platform].

## Cas d’utilisation

* Activation de profil et d’audience vers des destinations d’enregistrement en mode cloud ou des destinations de diffusion en flux continu pour le suivi, l’enregistrement, l’analyse et l’activation des données et des informations client au sein de l’entreprise.

## Applications

* Adobe Experience Platform   Activation

## Architecture

<img src="assets/enterprise_destination_activation.svg" alt="Architecture de référence pour le scénario d’activation en entreprise" style="width:90%; border:1px solid #4a4a4a" />


## Garde-fous

[Référez-vous aux garde-fous tels que décrits sur la page de présentation d’Audience et Profil Activation](overview.md)

## Étapes d’implémentation

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=fr) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Ingérez des données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) dans Experience Platform.
1. [Configuration [!UICONTROL Real-time Customer Data Platform] partage de segments](https://www.adobe.com/go/audiences) entre l’Experience Platform et l’Audience Manager pour les audiences définies dans l’Experience Platform à partager avec l’Audience Manager.
1. [Créez des segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr) dans Experience Platform. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. [Configurez les destinations](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=fr) pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.

## Documentation connexe

* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)
* [Présentation des destinations d’espace de stockage](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=fr#catalog)
* [Destination HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=fr#overview)
* [[!UICONTROL Real-time Customer Data Platform] Description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)

## Vidéos et tutoriels connexes

* [[!UICONTROL Real-time Customer Data Platform] aperçu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [Démonstration d’ [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr)
