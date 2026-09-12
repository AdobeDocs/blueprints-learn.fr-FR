---
title: Lancement de téléphone phare
description: Obtenez une vue d’ensemble de la création d’une campagne orchestrée qui cible les titulaires de compte et les lignes individuelles avec une offre de mise à niveau des SMS suite à un lancement téléphonique phare.
doc-type: overview-page
solution: Experience Platform
exl-id: 04c509f1-aa10-4d29-aa59-5e627b79e498
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Lancement de téléphone phare

## Conditions préalables

>[!WARNING]
>
>Les exercices ci-dessous doivent avoir été terminés avant de démarrer cet exercice

- **Magasins de données — Magasin relationnel en action** **—>** [Dimension cible du profil](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Magasins de données — Configurer les canaux e-mail —>** [Configurer pour relationnel](../../data-stores/configure-email-channels/configure-for-relational.md)
  *(cette étape de configuration peut prendre jusqu’à 3 heures)*

Si vous n&#39;avez pas terminé ces laboratoires, veuillez le faire maintenant avant de continuer.

## Présentation de l’atelier

Dans cette vidéo, vous découvrirez comment le cas d’utilisation phare de lancement de téléphone mappe les campagnes orchestrées, résumant les questions et l’architecture de la pensée critique avant de créer les titulaires de compte de ciblage de campagne et les lignes individuelles.

>[!VIDEO](https://video.tv.adobe.com/v/3486217/)

## Objectifs d’apprentissage

- Créer une campagne orchestrée à l’aide de diverses activités de workflow
- Création d’une audience à l’aide d’une activité Créer une audience
- Comprendre comment configurer un canal SMS
- Enregistrer une audience sur le portail d’audiences
- Ciblez le compte client et les lignes individuelles avec des e-mails et des sms



## Description du cas d’utilisation

Immédiatement après le lancement du dernier appareil phare d&#39;un fabricant, envoyez un message ciblé aux titulaires de compte et aux utilisateurs de ligne avec des modèles plus anciens, les invitant à mettre à niveau et à découvrir l&#39;avenir du mobile.

**Légendes principales :**

- Enregistrer l’audience de toutes les lignes client sur le portail Audience
- Ciblez les lignes individuelles et les titulaires de compte avec un message (vous utiliserez les SMS).

>[!NOTE]
>
>Ce scénario simule une **campagne de mise à niveau de contrat de télécommunications**, où les lignes secondaires (dépendantes) reçoivent des messages de mise à niveau ciblés.
