---
title: Composer le SMS
description: Découvrez comment composer et personnaliser un SMS dans des campagnes orchestrées à l’aide des attributs de marque de téléphone et de modèle du magasin relationnel.
doc-type: article
solution: Experience Platform
exl-id: 3deb822b-8374-4537-a260-f4f6f4d67569
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Composer le SMS

## Objectif

Dans les étapes suivantes, vous allez composer un SMS TRÈS simple.  Vous découvrirez comment ajouter facilement du contenu à un niveau EXTRÊMEMENT basique et personnaliser le message en fonction des données de la boutique relationnelle.



## Accès au contenu

Cliquez sur le bouton **Modifier le contenu** ou accédez directement à l’onglet **Contenu**

![Bouton Modifier le contenu et navigation dans l’onglet Contenu « Modifier le contenu »](assets/compose-the-sms-navigate-to-content-tab.png "Modifier le contenu")



## Création du message

1. Cliquez sur le bouton **&#x200B;**&#x200B;pour créer votre message.

   Bouton ![Personalization pour créer le SMS](assets/compose-the-sms-click-personalization-button.png)

   >[!NOTE]
   >
   >L’option « baguette magique » utilise l’IA pour vous aider à écrire un message. Regarde si tu veux, mais on ne le couvrira pas dans ce labo.



2. Copiez et collez le texte ci-dessous dans le corps du SMS.

   ```none
   Hi from Connection 5G! Your phone_make phone_model is eligible for a free upgrade to one of the new iPhone 17 models. Shop online or come into a store today to take advantage of this offer.
   ```

   >[!NOTE]
   >
   >Veillez à activer l’option Retour à la ligne Word **activé** dans l’éditeur de messages.  Vous pouvez trouver dans le volet inférieur droit de la fenêtre.



3. Mettez à jour les deux champs du message appelés **phone\_make** et **phone\_model** ci-dessous à l’aide de l’option **Attributs de cible** dans le rail de gauche.  Une fois cette opération terminée, votre message doit correspondre à la capture d’écran.

   ![Message SMS final avec marque et modèle de téléphone personnalisés](assets/compose-the-sms-final-message-text.png)

   >[!NOTE]
   >
   >Pourquoi fais-tu ça ?  Vous souhaitez personnaliser le message avec la marque et le modèle du téléphone des clients et ces informations se trouvent dans la table Ligne client de la boutique relationnelle.  Cela explique comment utiliser les données de campagnes orchestrées pour personnaliser les messages.



4. Cliquez sur le bouton **Valider** de l’éditeur et vérifiez qu’il n’y a aucune erreur de validation. Si nécessaire, cliquez sur le bouton **Enregistrer**

   ![Boutons Valider et Enregistrer dans l’éditeur de messages](assets/compose-the-sms-validate-and-save.png)



5. Cliquez sur la **flèche retour (\&lt;-)** lorsque vous avez terminé pour revenir à la zone de travail du workflow

![Flèche vers l’arrière pour revenir à la zone de travail du workflow](assets/compose-the-sms-return-to-canvas.png)



## Récapituler

Vous venez de créer un message et j’espère que vous connaissez maintenant un peu mieux le fonctionnement de l’éditeur de messages.  N’oubliez pas que vous pouvez effectuer une personnalisation à l’aide des données du magasin relationnel, mais vous pouvez également effectuer une personnalisation à l’aide des données du profil client en temps réel.

>[!NOTE]
>
>Si vous utilisez les attributs du profil client en temps réel pour personnaliser les messages dans les campagnes orchestrées, n’oubliez pas qu’ils sont extraits du jeu de données d’instantanés de profil dans le lac de données afin que les attributs puissent dater de 24 heures au maximum. L’instantané du profil n’est mis à jour qu’une seule fois par jour après la tâche de segmentation par lots quotidienne.
