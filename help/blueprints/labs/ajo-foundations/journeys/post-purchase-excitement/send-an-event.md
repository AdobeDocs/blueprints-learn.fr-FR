---
hold: true
title: Envoi d’un événement
description: Utilisez Postman pour diffuser directement un événement de commande expédiée simulé vers le Hub afin de déclencher le parcours, plutôt que de l’envoyer à Edge.
doc-type: article
solution: Experience Platform
exl-id: a0f75f5a-e3b3-42a2-8547-f075a7661a22
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---


# Envoi d’un événement

## Objectif d’apprentissage

Envoyez un événement simulé Commande envoyée pour déclencher le parcours à l’aide de Postman

## Diffusion en continu vers Hub ou Edge

Plus tôt, nous avons envoyé un événement à Edge.  Il existe certains cas d’utilisation où nous pouvons avoir un système principal qui souhaite diffuser un événement, mais qui n’a pas besoin de l’envoyer à Edge.  Cet atelier explique comment procéder en **diffusion en continu dans un événement de commande expédiée au hub** (ou serveur à serveur, par exemple de serveur Commerce à AEP signalant qu’une commande a été expédiée).

## L’événement de validation ne figure pas dans le profil

1. Accédez à vos **Profils** et recherchez le profil.
   - **Espace de noms d’identité** -> `email`
   - **Valeur de l’identité** -> `henry.creel@emailsim.io`
1. Cliquez sur l’onglet **Événements**.
   - Il ne doit y avoir **aucun** événement `orders.shipped`.

## Modifier la requête API

Pour créer la requête API, vous devez renseigner les éléments suivants dans le corps de la requête API.

Collectez d&#39;abord les valeurs suivantes :

### Rechercher le point d’entrée de diffusion en continu du compte

1. Accédez à **Sources** dans le rail de gauche, puis cliquez sur **Comptes** dans le volet de navigation supérieur
1. Recherchez **dep : API HTTP \[raw]**, mettez la ligne en surbrillance, copiez et enregistrez la valeur du point d’entrée **de diffusion en continu** à un endroit auquel vous pourrez vous référer ultérieurement

![dep : ligne de compte de l’API HTTP [raw] mise en surbrillance avec la valeur du point d’entrée de diffusion ](assets/send-an-event-streaming-endpoint-account-row.png "dep : API HTTP \[raw]")


### Rechercher un ID de flux de données

1. Cliquez sur **dep : API HTTP \[raw]**
1. Recherchez l’enregistrement de **dep: Orders (flux)** puis cliquez sur le lien flux de données .
1. Dans le rail de droite, copiez et enregistrez les valeurs **ID de flux de données** à un emplacement auquel vous pourrez faire référence ultérieurement

> [!WARNING]
>
>Cliquez dans un espace vide sur la ligne.  NE CLIQUEZ PAS sur les liens bleus !

![Valeurs d’ID de flux de données affichées dans le rail de droite](assets/send-an-event-dataflow-id-in-right-rail.png "ID de flux de données web et de jeu de données")



### Ouvrir Postman

Lancez Postman sur votre ordinateur et accédez à l’appel API suivant :

- Barre Latérale Gauche De **Postman** —> `Collections`
- **Collection** —> `AJO Bootcamp (Labs)`
- **Dossier** —> `Profile & Journey Labs`
- **Requête API** —> `Ship Order Event`

![Requête d’événement de commande d’expédition située dans la collection Postman](assets/send-an-event-open-ship-order-event-postman.png)



### Créer une requête API finale

1. Copiez les valeurs enregistrées lors des étapes précédentes dans les emplacements mis en surbrillance ci-dessous.
1. Cliquez sur **En-têtes** et collez ces valeurs (supprimez les espaces de fin) :
   - **Rouge** —> `Streaming Endpoint URL`
   - **Vert** —> `Dataflow ID`
     - La valeur ressemble à un GUID (ne commence pas par http)

> [!CAUTION]
>
>NE PAS EXÉCUTER POUR LE MOMENT

![URL de point d’entrée en flux continu et ID de flux de données collé dans les en-têtes Postman](assets/send-an-event-paste-headers-in-postman.png)

## Exécution de l’API

1. Enregistrez votre appel API en cliquant sur le bouton **Enregistrer**
1. Exécutez votre demande en cliquant sur le bouton **Envoyer**

Un appel réussi doit entraîner la réponse suivante...

![Réponse réussie après l’envoi de l’événement web](assets/send-an-event-successful-web-event-send.png)

## Récapituler

Un événement de commande d’expédition est envoyé avec succès à la plateforme
