---
title: Envoyer l’événement web au hub
description: Découvrez comment envoyer un événement web directement au Hub à l’aide de Postman et vérifier qu’il atteint le profil et se qualifie pour les segments en flux continu.
doc-type: article
solution: Experience Platform
exl-id: a8343499-b4d5-4540-8fe1-7497bc20e437
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Envoyer l’événement web au hub

## Ouvrir Postman

Lancez Postman sur votre ordinateur et accédez à l’appel API suivant :

1. Barre Latérale Gauche De **Postman** —> `Collections`
1. **Collection** —> `AEP Foundations Bootcamps (labs)`
1. **Dossier** —> Laboratoire de profils
1. **Requête API** —> `Create Web Event`

![Ouvrez la requête d’API Créer un événement web dans Postman](assets/send-web-event-to-hub-create-web-event-api-request.png)


## Modifier la requête API

Pour créer l’exemple de requête API, vous devez renseigner les éléments suivants dans le corps de la requête API.

Collectez d&#39;abord les valeurs suivantes :



## Rechercher le point d’entrée de diffusion en continu du compte

1. Accédez à **Sources** dans le rail de gauche, puis cliquez sur **Comptes** dans le volet de navigation supérieur
1. Recherchez **dep : API HTTP \[raw]**, mettez la ligne en surbrillance, copiez et enregistrez la valeur du point d’entrée **de diffusion en continu** à un endroit auquel vous pourrez vous référer ultérieurement

 le compte et copiez son point d’entrée de diffusion en continu&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png « dep: HTTP API \[raw] »)

## Rechercher un identifiant de flux de données web

1. Cliquez dans le compte **API HTTP \[raw]**
1. Recherchez et sélectionnez la ligne du flux de données appelée **dep : Web (flux)**
1. Dans le rail de droite, copiez et enregistrez les valeurs **ID de flux de données** à un emplacement auquel vous pourrez faire référence ultérieurement

>[!NOTE]
>
>Cliquez dans un espace vide sur la ligne.  NE CLIQUEZ PAS sur les liens bleus !

![Copiez l’ID de flux de données pour le dep : ID de flux de données web (flux] (assets/send-web-event-to-hub-web-stream-dataflow-id.png "Web)")

## Créer une requête API finale

Copiez les valeurs enregistrées lors des étapes précédentes dans les emplacements mis en surbrillance ci-dessous.

- **Rouge** —> `Streaming Endpoint URL`
- **Vert** —> `Dataflow ID`

Votre requête d’API finale doit ressembler à ceci une fois terminée

>[!CAUTION]
>
>NE PAS EXÉCUTER POUR LE MOMENT

![Requête Créer une API d’événement web terminée avec le point d’entrée de diffusion en continu et l’identifiant de flux de données renseignés](assets/send-web-event-to-hub-final-web-api-request.png)

## Exécution de l’API

1. Enregistrez votre appel API en cliquant sur le bouton **Enregistrer**
1. Exécutez votre demande en cliquant sur le bouton **Envoyer**

Un appel réussi doit entraîner la réponse suivante...

![Réponse API réussie après l’envoi de l’événement web](assets/send-web-event-to-hub-successful-api-response.png)

## Valider

1. Accédez à votre profil et recherchez votre profil pour voir que l’événement a été ingéré dans Profile.  Il devrait apparaître en secondes.
   1. Utiliser l’e-mail de votre appel pour rechercher le profil
1. Selon la durée écoulée depuis votre dernier envoi d’un événement, il se peut que vous ne soyez pas admissible pour de nouveaux segments. Sinon, vous risquez de voir ces éléments ou d’autres :
   1. Tout événement Edge (dans les 15 minutes)
      1. À retenir : toutes les audiences enregistrées avec une évaluation Edge sont également évaluées sur le Hub lorsque des données de diffusion en continu arrivent
   2. dep : diffusion en continu de tout événement (au cours de l’heure)
1. Il se peut que rien n’apparaisse dans votre webhook si vous n’avez aucun nouveau segment.
1. Le transfert d’événement n’envoie rien.
   1. Pourquoi ? Cet événement a été envoyé au hub, et non à Edge. Par conséquent, l’événement n’apparaîtra pas comme quoi que ce soit à envoyer par transfert d’événement, ni dans Assurance.
1. Après au moins 30 minutes, vous pouvez même vérifier votre jeu de données avec les éléments suivants :
   1. Remplacez le nom du tableau ci-dessous par celui de votre sandbox.  Pour le trouver, accédez à la liste de vos jeux de données et filtrez sur « `dest` », ouvrez le jeu de données et copiez le nom du tableau sur le rail de droite.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
