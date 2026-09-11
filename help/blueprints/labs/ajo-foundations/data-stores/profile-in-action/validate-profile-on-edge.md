---
hold: true
title: Valider le profil sur Edge
description: Découvrez comment vérifier le magasin de profils Edge et l’onglet Appartenance à une audience pour confirmer le statut d’un profil sur le réseau Edge.
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Valider le profil sur Edge

## Objectif d’apprentissage

Vérifiez que le profil n’existe pas sur le magasin de profils réseau Edge.

## Vérifier le profil Edge

1. Cliquez sur l’onglet **Attributs** et sur le bouton radio **Edge** pour afficher le profil Edge

![Profil Edge affiché dans l’onglet Attributs](assets/validate-profile-on-edge-attributes-tab.png)

>[!NOTE]
>
>Il est possible que vous voyiez une version « supprimée » du profil qui ne comprend que les identités en fonction du temps écoulé.



&#x200B;2. Cliquez sur l’onglet Abonnement de l’audience .  Ce sera **vide**.

![Onglet Abonnement d’une audience vide dans le profil Edge](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**Pourquoi n’êtes-vous pas membre d’Edge ?**
>
>N’aurions-nous pas dû voir **dep : Any Event Edge (dans l’heure)** qualifier ?
>
>Même si nous avons une audience qui dispose d’une évaluation Edge, cette audience n’existe pas sur Edge, car nous n’avons aucune raison de l’utiliser... pour l’instant.
>
>Si nous utilisions cette audience (par exemple, Prise de décision ou Destinations), les règles d’audience seront transmises à Edge et la prochaine fois qu’un événement sera diffusé en continu dans Edge, cette audience sera évaluée.
>
>En outre, nous n’avons pas activé Edge Segmentation Services.



## Récapituler

Le profil n’existe pas (encore) sur Edge
