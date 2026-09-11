---
hold: true
title: Vérification du profil ingéré
description: Recherchez un profil diffusé dans l’explorateur de profils à l’aide de son espace de noms d’identité principal pour confirmer la réussite de l’ingestion.
doc-type: article
solution: Experience Platform
exl-id: d45d6baf-9597-4419-b838-03156ce8cc83
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Vérification du profil ingéré

## Validation du streaming

La validation des données de diffusion en continu dans le Adobe Experience Platform nécessite quelques étapes différentes.  N’oubliez pas que les données de diffusion en continu peuvent écrire dans plusieurs bases de données en fonction de la configuration du jeu de données.

| Stockage | Latence | Description |
| -------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Lac De Données | \~jusqu&#39;à 60 minutes | Lieu d’essai final pour toutes les données en flux continu |
| Magasin de profils | \~1 min en moyenne mais jusqu&#39;à \~15min | Ne traite les données que lorsque le jeu de données sous-jacent est activé pour le profil |
| Magasin d’identités | \~1 min moy. \~10 min micro-lots pour les nouvelles relations d’identité nettes | Ne traite les données que lorsque le jeu de données sous-jacent est activé pour le profil |

Selon ce que vous essayez de valider, vous devrez peut-être accéder à différents emplacements, comme vous pouvez le voir ci-dessus.  Dans ce scénario, vous avez écrit les données dans le profil (comme vous avez activé le jeu de données pour le profil). Vérifiez donc que le magasin de profils ne contient pas le profil.



## Recherche de votre profil

1. Dans l’interface utilisateur, accédez à **Profils -> Parcourir**
1. Saisissez les valeurs suivantes dans les zones de saisie Espace de noms d’identité et Valeur d’identité :
   - **Espace de noms d’identité** -> `customerID`
   - **Valeur de l’identité** -> `202208240125`
1. Cliquez sur le bouton **Afficher** pour rechercher votre profil
1. Cliquez sur le lien **Identifiant du profil** dans la ligne renvoyée pour afficher votre profil

![Écran Parcourir le profil affichant la ligne de profil renvoyée après une recherche par customerID](assets/verify-ingested-profile-browse-profile-screen.png "écran Parcourir le profil")

Jetez un coup d’œil à votre profil et vérifiez qu’il correspond à ce que vous avez diffusé en streaming. Plutôt cool, hein !

![Vue détaillée du profil correspondant à l’enregistrement du compte client diffusé](assets/verify-ingested-profile-profile-detail-view.png)

>[!NOTE]
>
>Compte tenu de la latence de \~10 min sur l’assemblage des nouvelles relations d’identité, si vous aviez essayé de rechercher votre profil à l’aide de l’espace de noms d’e-mail, vous n’auriez pas vu de réponse.
>
>En utilisant plutôt l’espace de noms customerID (qui est l’identité principale), vous pouviez rechercher le profil immédiatement.
>
>N’oubliez pas que le profil ne connaît que les identités principales 😄
