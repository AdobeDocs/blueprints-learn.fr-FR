---
title: Modèle d'Activation des Audiences et des Profils aux destinations d'entreprise
description: Audience et Activation Profil vers les destinations d’entreprise
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: da21d1796eb9a2c9c0f087d82606874ca55bd4ea
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 39%

---

# Modèle d&#39;Activation des Audiences et des Profils aux destinations d&#39;entreprise

Partagez les modifications et les événements d’profil et d’audience en flux continu ou par lot de [!UICONTROL Plate-forme de données client en temps réel] vers les entrepôts de données et les applications d’entreprise. Ces événements d&#39;profil et d&#39;audience peuvent être utilisés pour lancer une action de vente ou d&#39;assistance au client, telle que le suivi d&#39;un processus de demande abandonné ou d&#39;un enregistrement de webinaire, ou pour mettre à jour les applications d&#39;entreprise avec les derniers attributs du client et les dernières informations de [!UICONTROL plate-forme de données client en temps réel].

## Cas d’utilisation

* Activation de profil et d’audience vers les destinations d’enregistrement en mode cloud ou les destinations de diffusion en flux continu pour le suivi d’entreprise, l’enregistrement, l’analyse et l’activation des données et des statistiques client.

## Applications

* Adobe Experience Platform Activation

## Architecture

<img src="assets/enterprise_destination_activation.svg" alt="Architecture de référence pour le scénario d'Activation d'entreprise" style="border:1px solid #4a4a4a" />


## Garde-fous

Reportez-vous aux garde-fous comme indiqué sur la page Aperçu de l&#39;Activation des Audiences et des Profils - [LIEN](overview.md)

## Étapes d’implémentation

1. Créez des schémas pour que les données soient assimilées.
1. Créez des jeux de données pour les données à ingérer.
1. Configurez les identités et les espaces de noms d’identité corrects sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. Activez les schémas et les jeux de données pour le traitement des profils.
1. Configurez toutes les sources pour l&#39;assimilation des données.
1. Segments d’auteur dans l’Experience Platform, à évaluer par lot ou en flux continu. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. Configurez les destinations pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.

## Documentation connexe

* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)
* [Présentation des destinations d’enregistrement dans le cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destination HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Description de Real-time Customer Data Platform](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Directives sur le profil et la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)

## Vidéos et tutoriels connexes

* [Présentation de Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [[!UICONTROL Vidéo de démonstration de Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr)
