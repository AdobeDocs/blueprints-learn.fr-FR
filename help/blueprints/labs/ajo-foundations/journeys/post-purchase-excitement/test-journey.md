---
title: Parcours de test
description: Utilisez le simulateur de mode Test parcours pour déclencher un événement Commande envoyée et confirmer que le déclencheur et la logique d’action s’exécutent correctement avant la publication.
doc-type: article
solution: Experience Platform
exl-id: fc3dbfb9-b44b-4866-acc9-398a8b52f2b9
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---


# Parcours de test

## Objectif d’apprentissage

Utilisez les outils de test de parcours pour vérifier que le déclencheur d’événement et la logique de parcours sont correctement configurés.

## Tester le parcours

1. Cliquez sur **Parcours** sur le rail de gauche et sur l’onglet **Parcourir** si vous ne voyez pas de liste de Parcours
2. Cliquez sur votre Parcours **** pour l&#39;ouvrir
3. Cliquez sur **Alertes** et vérifiez qu’aucune erreur ne s’est produite (les avertissements sont activés).

   ![Panneau Alertes ne présentant aucune erreur après l’ouverture du parcours ](assets/test-journey-alerts-no-errors.png)

   >[!NOTE]
   >
   >**Qu’est-ce que CJMMAS - 2001-200**
   >
   >Indique que le lien d’opt-out est manquant dans une variante d’e-mail

4. Cliquez sur le bouton **Simuler** puis, sur le côté gauche, sélectionnez **Mode Test**

   ![Mode Test sélectionné sous Simuler sur le côté gauche](assets/test-journey-select-test-mode.png)



   >[!NOTE]
   >
   >Il faudra peut-être une minute pour se préparer. Pendant ce temps, le bouton Déclencher un événement n’est pas disponible.



5. Cliquez sur **Déclencher un événement** et renseignez les propriétés suivantes :
   - **Type d’événement** : `orders.shipped`
   - **E-mail personnel** : `henry.creel@emailsim.io`
   - **ID de commande** : `123`
6. Cliquez sur **Envoyer** (notez qu’il faut quelques secondes pour répondre après avoir cliqué sur Envoyer).

   ![Déclencher un formulaire d’événement rempli et Envoyer sur lequel l’utilisateur a cliqué](assets/test-journey-trigger-event-send.png)

   >[!WARNING]
   >
   >Certains étudiants ont des erreurs et doivent les envoyer plusieurs fois. Il se peut que vous deviez le faire **plusieurs** fois.
   >
   >**Parfois** le premier envoi renvoie une erreur de :
   >
   >**L’entrée n’existe pas (ID de référence : 3216a850-c40d-11f0-8fa5-73d1522cc9a2)**
   >
   >Si vous obtenez une erreur, cliquez sur **Déclencher un événement**, puis **envoyer** à nouveau.  Vous devrez peut-être le faire **plusieurs fois**.



7. Sous **Résultats** -> Cliquez sur **Afficher le journal** sur le côté gauche

![Afficher l’option Journal sous Résultats après le déclenchement de l’événement de test](assets/test-journey-show-log-results.png)

>[!NOTE]
>
>Certains élèves qui ont reçu des erreurs reçoivent parfois différents journaux affichant un tableau d’instances `{"instances": []}`. Ceci n&#39;est pas un bloqueur, allez-y et passez à l&#39;étape suivante.

Vous devriez voir un élément similaire à ceci dans le journal :

>[!NOTE]
>
>Nous recherchons les champs clés utilisés : **actionsHistory**, **transitionsHistory**, **eta**, **tracking_number**, **eventType**, **personalEmail** et **orderID**.

```json
{
  "actionsHistory": {
    "8919055f-1b00-4a43-8bd6-c8af894474b2": {
      "eta": "11/27/2025",
      "tracking_number": "091204404",
      "jo_status_code": "http_200"
    }
  },
  "transitionsHistory": {
    "orderShipped (1158856989)": {
      "eventType": "orders.shipped",
      "_id": "joTestModeEvent_5abbfdcd-561d-45a7-ba42-d0640539831a",
      "_dep": {
        "personalEmail": "henry.creel@emailsim.io"
      },
      "order": {
        "orderID": "123"
      },
      "timestamp": "2025-11-17T23:30:49.576289372Z"
    }
  }
}
```



8. **Fermer** l’onglet **du navigateur**
9. **Fermer le mode Test** en haut à droite

   ![Bouton Fermer le mode Test en haut à droite](assets/test-journey-close-test-mode.png)

10. Cliquez sur **Publier** le Parcours en haut à droite

![Bouton Publier pour le Parcours en haut à droite](assets/test-journey-publish-journey.png)

11. **Fermez** Parcours **** en cliquant sur la flèche \&lt;- en haut à gauche

![Flèche vers l’arrière en haut à gauche pour fermer le Parcours ](assets/test-journey-close-journey-back-arrow.png)

Ensuite, nous enverrons un événement réel de commande expédiée dans AEP

## Récapituler

Le parcours a réussi la validation de la configuration et est prêt à recevoir des événements
