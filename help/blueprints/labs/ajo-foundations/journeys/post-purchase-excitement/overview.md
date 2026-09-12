---
title: Excitation post-achat
description: Découvrez comment créer un parcours post-achat piloté par les événements qui déclenche un e-mail de notification d’expédition avec des détails de suivi dynamique provenant d’une API tierce.
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Excitation post-achat

## Conditions préalables

>[!WARNING]
>
>Les exercices ci-dessous doivent avoir été terminés avant de démarrer cet exercice

Ces ateliers doivent avoir été terminés avant de démarrer cet atelier :

- **Magasins de données — Magasin relationnel en action** **—>** [Dimension cible du profil](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **Magasins de données — Configuration des canaux e-mail —>** [Configuration pour le profil](../../data-stores/configure-email-channels/configure-for-profile.md)
  *(cette opération peut prendre jusqu&#39;à 3 heures)*

Si vous ne l’avez pas encore fait, veuillez les compléter maintenant

## Présentation de l’atelier

Dans cette vidéo, vous découvrirez comment le cas d’utilisation d’excitation post-achat correspond à un parcours, en parcourant les questions de réflexion critique et l’architecture pour envoyer une notification d’expédition personnalisée une fois une commande envoyée.

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## Objectifs d’apprentissage

- Créez un Parcours qui commence par un événement unitaire
- Configurer une action personnalisée à appeler à un système tiers pour renvoyer des informations utilisées dans un Parcours
- Exécution d&#39;un parcours en flux continu dans une payload d&#39;événement
- Tester et déboguer des profils et des Parcours
- Valider l’expérience prévue par le biais de rapports et de journaux
- Configurez la personnalisation dans un e-mail simple et voyez-la en action



## Description du cas d’utilisation

Lorsqu’un client passe une commande, vous souhaitez envoyer un message de confirmation contenant les détails de la commande.  Une fois la commande expédiée, vous souhaitez déclencher un second message avec des informations de tracking récupérées dynamiquement à partir d’une API tierce.

**Légendes principales :**

- La commande initiale passée est généralement mise en œuvre sous la forme d’un message transactionnel, car les clients ne souhaitent pas attendre une confirmation de commande.
- La notification de commande envoyée peut également être implémentée à l’aide de la messagerie transactionnelle, mais elle peut être créée dans un parcours, ce qui permet une action personnalisée pour récupérer les informations d’expédition et améliorer la communication avec le client.

>[!NOTE]
>
>Dans cet atelier, vous allez uniquement créer le message Commande expédiée et ignorer le message Confirmation de commande.
