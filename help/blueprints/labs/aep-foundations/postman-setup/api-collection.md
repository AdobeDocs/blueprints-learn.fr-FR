---
title: Collection d’API
description: Téléchargez et importez la collection d’API Postman de bootcamp contenant les requêtes utilisées dans les laboratoires AEP Foundations.
doc-type: article
solution: Experience Platform
exl-id: 18d820c5-56ad-46b8-a9cf-f725555d2db3
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---

# Collection d’API

## Fichier de collection de l’API Postman

Télécharger le fichier — [Bootcamp AEP Foundations (Labs).postman_collection.json](assets/aep-foundations-bootcamp-labs.postman_collection.json)



## Importer la collection d’API

1. Ouvrez le `Postman API Collection File` ci-dessus dans votre navigateur en cliquant sur le fichier .
1. Copiez l’URL du fichier dans le presse-papiers
1. Lancez Postman sur votre ordinateur local et cliquez sur le bouton `Import` dans votre espace de travail
1. Collez l’URL du `Postman API Collection File` dans la zone de texte modale d’importation. Cela déclenche une importation automatique

![Cliquez sur le bouton Importer dans l’espace de travail Postman pour importer le bouton d’importation &#x200B;](assets/api-collection-click-import-button.png " la collection d’API")



![Collage de l’URL du fichier de collection d’API dans la zone de texte modale d’importation de Postman](assets/api-collection-import-modal-paste-url.png "zone de texte modale du bouton d’importation")

Une collection s’affiche désormais sous l’onglet `Collections` de la barre latérale gauche, appelé `AEP Foundations Bootcamp`



![La collection Bootcamp d’AEP Foundations est renseignée sous l’onglet de barre latérale Collections de Postman](assets/api-collection-imported-collection-in-sidebar.png)

## Présentation de la collection Bootcamp d’AEP Foundations

La collection d’API que vous avez importée contient tous les appels d’API nécessaires pour les ateliers du camp d’amorçage.  Chaque Lab est organisé dans un dossier spécifique avec son propre ensemble d’API.  Tenez compte de cette structure de dossiers lorsque vous terminerez les exercices pratiques de cette semaine.

Vous trouverez ci-dessous des informations détaillées sur chaque dossier :

- **Authentification IMS** - contient une seule demande de génération d’un jeton access\_token requis lorsque vous utilisez l’une des API Adobe Experience Platform
- **XDM Schema Lab** : contient un ensemble de requêtes pour la création des composants XDM nécessaires à la création et la configuration d’un schéma pour le profil client en temps réel
- **Data Ingestion Lab** - contient un ensemble de demandes de diffusion de données en continu dans Experience Platform
- **Profile Lab** - contient un ensemble de requêtes pour afficher les caractéristiques et les comportements du profil client en temps réel

>[!SUCCESS]
>
>Félicitations !  Vous avez correctement importé la collection Postman du bootcamp
