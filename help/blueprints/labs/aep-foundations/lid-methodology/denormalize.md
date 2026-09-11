---
hold: true
title: Dénormaliser
description: Appliquez les règles de dénormalisation de la méthodologie LID pour replier les tables bridge et dépendantes d’un ERD dans leurs tables parent de profil, d’événement et de recherche.
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---


# Dénormaliser

## Conférence

Dans cette vidéo, vous découvrirez les trois règles de dénormalisation pour replier les tables de recherche et de pontage dans leurs tables parents, ainsi que la manière dont les exigences de personnalisation et de segmentation en flux continu affectent ces décisions.

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## Détails de l’atelier

>[!NOTE]
>
>Ce Lab se concentre uniquement sur l&#39;entrepôt de connexion 5G ERD

## Règles de dénormalisation :

1. Toute table du modèle relationnel étiquetée comme « **D** » avec une cardinalité 1\:M ou étiquetée comme « **B** » est définie comme un tableau d&#39;objets ou un mappage sur la table parent
1. Déclenché par le #1 de règles, avant de dénormaliser les tables « **D** » ou « **B** » qui agissent comme des tableaux ou des mappages, interrogez-les pour déterminer la meilleure façon de les dénormaliser à nouveau dans leur table parent
1. Toute table du modèle relationnel étiquetée comme « **D** » avec une cardinalité de M:1 agit comme un objet ou comme une liste de champs sur sa table parent

## Dénormalisation pour les règles de personnalisation :

N’oubliez jamais de consulter les cas d’utilisation client lors de la création du modèle de données.  Gardez à l’esprit les points suivants :

- La segmentation en flux continu n’a pas accès aux tables de recherche au moment de l’évaluation
- Seules les caractéristiques et l’appartenance à un segment d’un profil sont accessibles pour personnaliser le contenu

![Cas d’utilisation de connexion 5G pris en compte lors de l’application de la dénormalisation pour les cas d’utilisation de personnalisation](assets/denormalize-connection-5g-use-cases.png "connexion 5G")

>[!NOTE]
>
>N’oubliez pas de vous référer au scénario de formation Connection 5G.pdf au cours de ce Lab.



## Etape 1 - Remplir le tableau de profil individuel

1. Écrivez dans les champs qui doivent être dénormalisés dans le tableau des comptes clients à partir de tout schéma « **B** » ou « **D** » associé
1. En examinant les cas d’utilisation ci-dessus, quels champs supplémentaires sont nécessaires pour prendre en charge la segmentation et/ou la personnalisation en flux continu ? Ajouter ces champs au tableau



## Étape 2 : renseigner les tableaux Événement d’expérience

1. Écrivez dans les champs qui doivent être dénormalisés dans les tables Facturation et Commandes à partir de toutes les tables « **B** » ou « **D** » associées
1. En examinant les cas d’utilisation ci-dessus, quels champs supplémentaires sont nécessaires pour prendre en charge la segmentation et/ou la personnalisation en flux continu ? Ajouter ces champs au tableau



## Etape 3 - Renseigner les tables Lookup

1. Écrivez dans les champs qui doivent être dénormalisés dans la table de recherche de produit à partir de toutes les tables « **B** » ou « **D** » associées
1. En examinant les cas d’utilisation ci-dessus, quels champs supplémentaires sont nécessaires pour prendre en charge la segmentation et/ou la personnalisation en flux continu ? Ajouter ces champs au tableau




## Révision

La vidéo ci-dessous montre comment les tableaux de connexion 5G ont été dénormalisés en tableaux et objets, et comment les cas d’utilisation d’acquisition et de montée en gamme ont nécessité de ramener des champs supplémentaires sur les tableaux de profils et d’événements principaux.

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
