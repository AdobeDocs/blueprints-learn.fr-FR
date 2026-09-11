---
title: Envoi d’un événement Edge
description: Envoyez un événement web non authentifié à Edge via Postman et vérifiez qu’il passe par le transfert d’événement, l’ingestion de profil et la qualification d’audience Edge.
doc-type: article
solution: Experience Platform
exl-id: 8d6e9552-1fa0-4f12-928c-03f836c1652e
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Envoi d’un événement Edge

Maintenant que tout est configuré, envoyez un événement à Edge pour voir si tout fonctionne.

Pour ce faire, utilisez Postman pour envoyer un événement web au flux de données que vous avez créé.

Cette opération envoie un événement **sans jeton OAuth** pour simuler une page vue entrant du web vers Edge.  Vérifiez que Postman est ouvert sur votre ordinateur pour effectuer cet exercice pratique.

>[!NOTE]
>
>Comme vous ne transmettez pas de jeton authentifié, vous ne récupérez aucun attribut.

## Attentes du Lab

1. Événement d’expérience sur Edge
1. Configuration du flux de données pour utiliser le service de transfert d’événement
1. Transfert d’événement pour envoyer l’événement au webhook
1. Configuration du flux de données pour utiliser le service AEP
   1. Audience Edge à exécuter
   1. Envoyer l’événement au hub
1. Réponse de Postman pour inclure l’audience Edge (mais pas d’attributs)
1. Magasin de profils pour recevoir l’événement et ajouter un fragment de profil d’événement
1. Magasin d’identités pour ajouter une relation
1. Jeu de données pour recevoir des données et les stocker dans le lac de données



## Accéder à l’appel

1. Barre Latérale Gauche De **Postman** -> Collections
1. **Collection** -> AEP Foundations Bootcamps (Labs)
1. **Dossier** -> Laboratoire de profils
1. **Requête API** -> Créer une Edge d’événement web (aucune authentification)

Navigation dans la barre latérale ![Postman vers la requête de l’API Create Web Event Edge (Aucune authentification) dans le dossier Profile Lab](assets/send-an-edge-event-navigate-to-the-postman-call.png)

## Modifier la requête API

Avant de pouvoir exécuter la requête API, vous devez ajouter des informations supplémentaires à la requête. Collectez d&#39;abord les valeurs suivantes :

## Collecter l’identifiant du flux de données

1. Dans le rail de gauche, cliquez sur **Flux de données** (sous l’en-tête Collecte de données)
1. Sélectionnez votre flux de données et copiez la valeur **Identifiant du flux de données**

![Liste Flux de données avec la valeur d’identifiant de flux de données mise en surbrillance pour la copie](assets/send-an-edge-event-gather-datastream-id.png)

## Mettre à jour le paramètre de requête Postman

1. Dans la requête elle-même, cliquez sur **Params**
1. Mettez à jour la **Valeur** avec l’identifiant du flux de données de l’étape précédente
1. Cliquez sur le bouton **Enregistrer** pour enregistrer votre mise à jour

![Onglet Paramètres Postman avec la valeur de l’ID du flux de données collée dans le champ Valeur](assets/send-an-edge-event-update-datastream-id-param.png "Mettre à jour dataStreamId")



Remplacer l’e-mail par votre e-mail

![Corps de la requête Postman affichant la valeur d’e-mail mise à jour vers l’adresse e-mail du testeur](assets/send-an-edge-event-change-email-param.png "Remplacez l’e-mail par votre adresse e-mail")

## Exécution de l’API

Exécutez votre demande en cliquant sur le bouton **Envoyer**.

![Bouton Envoyer Postman sur lequel l’utilisateur clique pour exécuter la requête Edge Créer un événement web](assets/send-an-edge-event-execute-request.png)

Ce que vous devriez voir revenir dans la réponse est cette chose essentielle :

- Une réponse 200 OK signifie que les données ont été envoyées et acceptées par Edge Network

>[!NOTE]
>
>Les segments en flux continu et par lots ne s’affichent pas tant qu’ils n’ont pas été évalués au niveau du hub en premier

## Validation du transfert d’événement

Sur webhook.site, le corps de la payload que vous avez envoyé via votre requête Postman doit immédiatement apparaître.

![Webhook.site affichant la payload d’événement transférée reçue du transfert d’événement](assets/send-an-edge-event-webhook-payload.png)

>[!NOTE]
>
>Notez que la payload a ajouté les informations de recherche géographique que vous avez demandées lors de la configuration du flux de données utilisé dans votre configuration Edge

## Recherche du profil

Dans Adobe Experience Platform, recherchez le profil que vous venez d’envoyer à partir de l’événement que vous venez d’envoyer dans Edge Network. Accédez à Profils -> Parcourir pour effectuer la recherche à l’aide des informations suivantes :

- Politique de fusion -> Basée sur l’heure par défaut
- Espace de noms d’identité -> E-mail
- Valeur d’identité -> edge-email\@dep.com
  - Remarque : modifiez ce paramètre pour qu’il corresponde à l’e-mail que vous avez utilisé à l’étape *Mettre à jour le paramètre de requête Postman* ci-dessus

1. Cliquez sur **Afficher** pour rechercher le profil
1. Cliquez sur le **Identifiant du profil** pour ouvrir le profil

   ![Profil Parcourez les résultats de la recherche avec le lien Afficher pour ouvrir le profil ](assets/send-an-edge-event-lookup-profile.png " recherche correspondant")

1. Cliquez sur **Événements** dans le volet de navigation supérieur pour afficher l’événement que vous venez d’envoyer

   ![Onglet Événements de profil affichant l’événement d’expérience qui vient d’être envoyé à Edge](assets/send-an-edge-event-view-profile-event.png "Affichez l’événement de profil")

1. Vérifiez que le profil est qualifié pour les audiences en consultant l’onglet Appartenance à l’audience dans le volet de navigation supérieur. Vous devriez voir les éléments suivants :

- Tout événement Edge (dans les 15 minutes)
- dep : diffusion en continu de tout événement (au cours de l’heure)

![Onglet Appartenance à une audience montrant la qualification pour N’importe quel événement Edge et dep : N’importe quelle audience de diffusion en continu d’événement](assets/send-an-edge-event-any-event-streaming-within-the-last-hour.png)

## Interprétation des contrôles

1. Vérifier la réponse 200 dans Postman (payload correctement formatée)
1. Vérifiez si le webhook contient l’événement (transfert d’événement correctement configuré)
1. Vérifiez si le profil contient les événements (service AEP correctement configuré, événement reçu et traité sur le Hub)
1. Vérifiez si le profil possède deux identités (le graphique d’identités est lié sur le Hub) au bout de quelques minutes
1. Vérifiez si le profil est qualifié pour les audiences (audience correctement définie)
1. Vérifiez si le lac de données contient l’événement .
