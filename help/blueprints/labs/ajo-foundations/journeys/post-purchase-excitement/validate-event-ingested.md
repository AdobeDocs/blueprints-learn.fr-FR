---
title: Valider l’événement ingéré
description: Confirmez qu’un événement Commande envoyée a été ingéré dans un profil et le qualifie pour les audiences attendues.
doc-type: article
solution: Experience Platform
exl-id: c04397dd-8b5c-48a8-82b5-78188b8374f1
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Valider l’événement ingéré

## Objectif d’apprentissage

Vérifiez que l’événement a bien été ingéré dans Adobe Experience Platform.

## Valider l’événement dans le profil

1. Accédez à vos **Profils** et recherchez votre profil pour voir que l’événement a été ingéré dans le profil.  Il s’affiche en secondes.
   - **Espace de noms d’identité** -> `email`
   - **Valeur de l’identité** -> `henry.creel@emailsim.io`
2. Cliquez sur l’onglet **Événements**. Recherchez `orders.shipped` événement .

   ![événement orders.shipping affiché dans l&#39;onglet Événements du profil](assets/validate-event-ingested-orders-shipped-event.png)

   >[!WARNING]
   >
   >Avez-vous reçu des événements **message.feedback** ?  Elles proviennent de Parcours et indiquent généralement un échec ou une exclusion.  Cliquez dessus et regardez le `reason`.
   >
   >Voici quelques exemples que vous pouvez rencontrer en production :
   >
   >- EmailNoAddressFoundInProfile (vous avez tenté d&#39;envoyer un e-mail à un profil qui n&#39;en avait pas)
   >- EmailNoConsent (vous avez essayé d&#39;envoyer un e-mail à un profil pour lequel le consentement a été défini sur non.



3. Vérifiez que le profil est qualifié pour le **audiences** (cela peut prendre quelques minutes).
   - Tout événement Edge (dans les 15 minutes)
   - Diffusion en continu de tout événement (dans les 15 minutes)

![Profil qualifié pour toutes les audiences d’Edge d’événement et de streaming d’événement](assets/validate-event-ingested-profile-qualified-audiences.png)



## Essayer avec votre propre e-mail

Maintenant que vous avez validé l’entrée du profil, envoyez certains événements de commande expédiée à l’aide de votre propre e-mail.

1. Revenez à Postman et recherchez l’**événement de commande d’expédition**.
2. cliquez sur le **Corps** et remplacez le **adresse e-mail** par le vôtre.

   ![Modification de l’adresse e-mail dans le corps de la requête Postman](assets/validate-event-ingested-change-email-in-postman-body.png)

3. **Enregistrer** et appuyez sur **Envoyer**.
4. Revenez aux étapes 1 à 3 et validez à l’aide de votre adresse e-mail.

## Récapituler

L’événement apparaît dans la banque de profils et le profil fait désormais partie des audiences qui recherchaient l’événement.
