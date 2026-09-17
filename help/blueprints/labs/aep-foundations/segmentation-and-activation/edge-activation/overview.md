---
title: Activation d’Edge
description: Découvrez en quoi les vitesses d’activation d’Edge, de streaming et par lots diffèrent et prévisualisez les étapes du Lab pour créer un segment Edge et configurer le transfert d’événement.
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%
---

# Activation d’Edge

## Récapitulatif de la vitesse d’activation

Adobe propose trois vitesses d’activation destinées à répondre à des besoins différents :

1. Edge
1. Diffusion en continu
1. Lot

Nous allons passer en revue la procédure d’activation à l’aide d’Adobe Edge avec le transfert d’événement, les audiences Edge et Edge Personalization. Nous montrerons ensuite comment utiliser les destinations de diffusion en continu du hub vers Edge et vers une destination externe.

>[!IMPORTANT]
>
>Terminez la configuration de [&#128279;](../../setup.md) avant de commencer cet atelier. Vous devez également accéder à [webhook.site](https://webhook.site/) pour capturer l’événement envoyé à la destination externe.

>[!NOTE]
>
>L’activation par lots ne sera pas couverte dans cet atelier. L’activation par lots peut être planifiée à différents intervalles, ce qui complique la présentation dans un environnement de laboratoire sans disposer d’au moins 3 à 24 heures.



## Ce que couvrira le laboratoire

- Créer un segment Edge
- Configurer le transfert d’événement
- Envoyer dans un événement Edge
- Cela se déclenche
  - Segment Edge à qualifier
  - Transfert d’événement sur Edge à envoyer à webhook
