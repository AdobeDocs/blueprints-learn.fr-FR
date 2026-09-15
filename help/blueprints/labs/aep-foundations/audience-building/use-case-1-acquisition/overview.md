---
title: Cas d’utilisation #1 - Acquisition
description: Définissez un cas d’utilisation d’acquisition qui cible les visiteurs d’iPhone 14 pages qui n’ont pas commandé l’appareil ou qui ne sont pas propriétaires de l’appareil, et planifiez l’approche de création d’audience.
doc-type: overview-page
solution: Experience Platform
exl-id: a85b1eb1-88f4-41b2-acce-2e34dbe6aff8
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---

# Cas pratique #1 - Acquisition

## Présentation

Dans cette vidéo, vous apprendrez à créer l’audience pour le cas d’utilisation d’acquisition d’iPhone 14.

>[!VIDEO](https://video.tv.adobe.com/v/3459402/?quality=12&learn=on)



**Définition de cas d’utilisation**

Activez tous les profils qui ont visité une page de produit iPhone 14 et qu’il n’existe aucune commande pour un iPhone 14 ou qui n’ont pas de produit iPhone 14 actif.

>[!IMPORTANT]
>
>Terminez la configuration de [](../../setup.md) avant de commencer cet atelier. Vous devez également accéder à [webhook.site](https://webhook.site/) pour capturer les données d’audience activées.



## Tâches d&#39;analyse

Analysez ce qui précède et notez ce qui suit :

1. Quels champs pensez-vous nécessaires pour résoudre ce cas d’utilisation ?
1. La méthode d’évaluation doit-elle être Diffusion en continu ?
1. Quelles sont les ramifications de la diffusion en continu lorsque les événements utilisés dans l’audience arrivent à différents moments ?
1. Comment savons-nous ce que signifie « actif »?
1. Quelles autres informations souhaitez-vous connaître ?

**À retenir** : lorsque nous obtenons des exigences des parties prenantes de l’entreprise, elles ont tendance à être incomplètes, à utiliser une autre terminologie et à émettre des hypothèses sans les connaître. C&#39;est votre travail de faire ressortir le plus de choses possible et de les guider vers quelque chose qui peut être fait.



## Approche

Pour ce cas d’utilisation, nous allons le diviser en plusieurs audiences :

1. Il n’existe aucune commande iPhone/Pixel.
1. Pas d’iPhone/pixel actif
1. IPhone/Pixel visité et aucune commande n’existe iPhone/Pixel et aucune iPhone/pixel actif
