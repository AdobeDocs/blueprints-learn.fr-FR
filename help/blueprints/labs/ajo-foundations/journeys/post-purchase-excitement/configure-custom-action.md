---
title: Configuration d’une action personnalisée
description: Configurez une action personnalisée réutilisable dans Adobe Journey Optimizer qui appelle un point d’entrée tiers pour récupérer l’ETA d’expédition et les détails de suivi.
doc-type: article
solution: Experience Platform
exl-id: f81cc8be-bc2a-43cb-a2d4-89834aa94dcb
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%
---

# Configuration d’une action personnalisée

## Objectif d’apprentissage

Créez une action personnalisée qui définit la manière dont le parcours communique avec un point d’entrée ou un service externe afin d’obtenir une ETA pour le moment où le package arrive.

## Accéder aux actions

Dans le rail de gauche, sous le menu Administration, cliquez sur **Configurations** puis, sur la mosaïque Actions, cliquez sur le bouton **Gérer**

![Bouton Gérer sur la mosaïque Actions sous Configurations](assets/configure-custom-action-open-actions-manage.png)



## Configuration de l’action

### Nom et détails de l’action

1. Dans le coin supérieur droit, cliquez sur le bouton **Créer une action**

   ![Bouton Créer une action en haut à droite](assets/configure-custom-action-click-create-action-button.png)

2. Dans le panneau de configuration qui s’affiche, mettez à jour les valeurs de base suivantes, comme illustré ci-dessous :
   - **Nom** : `GetShippingDetails`
   - **Description** : `Call third party to get Shipping ETA and Tracking Number`
   - **Type d’action** : `Custom`
   - **Canal** : `Email`
   - **Action marketing requise** : `Email Targeting`

![Valeurs de base configurées pour l’action personnalisée GetShippingDetails](assets/configure-custom-action-set-basic-values.png)


### Détails du point d’entrée

Dans la zone Configuration du point d’entrée , fournissez les détails suivants :

- **URL du point d’entrée** : `https://api.mockaroo.com/api/67077bb0?count=1&key=a0dbce20`
- **Méthode** : `GET`
- **En-têtes :** *laisser en l’état*
- **Paramètres de requête:**
  - **Nom** : `orderid`
  - **Type** : `variable`

>[!NOTE]
>
>Une variable vous permet de transmettre une valeur au cours d’un parcours au lieu d’utiliser une valeur statique pour tous les parcours

- **Type d’authentification** : `No Authentication`

![URL du point d’entrée, méthode et paramètre de requête configuré pour l’action personnalisée](assets/configure-custom-action-endpoint-details-configured.png)

![Type d’authentification défini sur Aucune authentification pour le point d’entrée](assets/configure-custom-action-endpoint-details-configured--2.png)



### Détails de la payload de réponse

Vous devez maintenant fournir un exemple de payload afin que l’action sache à quoi ressemble la payload de réponse.

1. Dans la zone Payloads, cliquez sur l’icône **Crayon** pour ouvrir l’écran Configuration du champ .

   ![Icône en forme de crayon pour ouvrir l’écran Configuration du champ dans la zone Payloads](assets/configure-custom-action-open-field-configuration.png)

   ![Écran de configuration du champ pour le payload de réponse](assets/configure-custom-action-open-field-configuration--2.png)



2. **Copiez et collez** la payload ci-dessous dans la zone Payload .

   ```json
   {
    "eta": "11/19/2025",
    "tracking_number": "072000326"
   }
   ```

   >[!NOTE]
   >
   >Il s’agit de la même structure JSON que le point d’entrée Mockaroo ci-dessus doit renvoyer :


3. La payload de réponse s’affiche. Cliquez sur le bouton **Enregistrer**.

![ Payload de réponse affichée avec le bouton Enregistrer ](assets/configure-custom-action-save-response-payload.png)

>[!NOTE]
>
>Vous pouvez tout laisser sous forme de chaîne, mais dans la vie réelle, vous souhaiterez probablement le mettre à jour pour qu’il corresponde au type de données



### Tester l’action

1. Cliquez sur le bouton **Envoyer une requête de test** dans le rail inférieur droit pour confirmer que votre configuration fonctionne correctement

   ![Bouton Envoyer la demande de test dans le rail inférieur droit](assets/configure-custom-action-click-send-test-request.png)



2. Cliquez sur l’onglet **Paramètres de requête** et mettez à jour la valeur de `orderId` sur **123**

   ![Onglet Paramètres de requête avec la valeur orderId définie sur 123](assets/configure-custom-action-set-orderid-query-parameter.png)



3. Cliquez sur le bouton **Envoyer** et si tout fonctionne bien, vous devriez voir un code de réponse de 200 et un aperçu de la payload comme illustré ci-dessous...

   ![Code de réponse 200 et aperçu de la payload après l’envoi de la requête de test](assets/configure-custom-action-response-200-preview.png)

   Prévisualiser

   ```json
   {
     "eta": "12/26/2025",
     "tracking_number": "063112249"
   }
   ```

   >[!WARNING]
   >
   >Si vous ne voyez pas de réponse 200 ou d’aperçu, ne continuez pas. Demandez de l&#39;aide à votre animateur.



4. Cliquez sur le bouton **Annuler** pour revenir à l’écran Action, puis faites défiler l’écran vers le haut dans le rail supérieur droit et cliquez sur le bouton **Enregistrer**

>[!SUCCESS]
>
>Félicitations ! Votre action personnalisée est en ligne, grâce à vos compétences de niveau expert Ctrl+C, Ctrl+V.

## Récapituler

Action personnalisée réutilisable configurée dans Adobe Journey Optimizer qui prend un ID de commande et renvoie l’ETA et le numéro de suivi.
