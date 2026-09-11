---
hold: true
title: Diffusion d’un événement de commande
description: Entraînez-vous à créer un flux de données de diffusion en continu d’API HTTP pour envoyer un exemple d’événement de commande et le lier à un profil client existant.
doc-type: article
solution: Experience Platform
exl-id: 558c21d1-f9b7-489b-9153-5f10d0b8448a
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Diffusion d’un événement de commande

## Conditions préalables

1. Vous avez téléchargé le fichier [Exemples de fichiers](../sample-files.md) et consultez le fichier nommé —> **Lab\_Single\_Order\_sample.json**
1. Vous avez terminé l’atelier [Utilisation de Data Landing Zone](./using-data-landing-zone/overview.md) et disposez d’un jeu de mappages valide à importer

## Défi

Effectuez les tâches suivantes comme vous l&#39;avez fait dans l&#39;atelier précédent.

1. Créer un compte à l’aide du connecteur source d’API HTTP
1. Configurez un flux de données à l’aide du nouveau compte pour diffuser des données dans votre propre jeu de données Commandes client
1. Réutilisez le jeu de mappages de l’atelier [Utilisation de la zone d’atterrissage de données](./using-data-landing-zone/overview.md).
1. Dans Postman, renseignez l’**Événement de commande à créer** avec les informations nécessaires pour diffuser avec succès les données et joignez-les à l’enregistrement de compte client créé précédemment
1. Vérifiez que la commande est liée à votre profil

> [!TIP]
>
>Bonne chance et que les dieux du Adobe Experience Platform soient avec vous !
