---
title: Accès aux sandbox
description: Vérifiez que votre environnement Postman peut récupérer le sandbox Experience Platform qui vous a été attribué avant de démarrer les ateliers.
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Accès aux sandbox

Avant de continuer, vérifiez que votre accès est autorisé. Effectuez les étapes suivantes :

1. Ouvrez le dossier intitulé `Check Sandbox Access` et cliquez sur l’appel intitulé `Retrieve Your Sandbox`
1. Un menu déroulant Environnement s’affiche ensuite dans le coin supérieur droit de Postman.  Veillez à sélectionner l’environnement `AEP Bootcamp`
1. Exécutez l’appel en cliquant sur le bouton `Send` .

![Volet de requêtes Postman pour l’appel Récupérer votre sandbox avant l’envoi](assets/sandbox-access-check-sandbox-request.png "Récupérer votre appel API sandbox")



Une réponse réussie se présente comme suit :

Réponse OK ![200 confirmant la récupération réussie de la sandbox affectée](assets/sandbox-access-successful-response.png "200 OK Demande de sandbox réussie")

>[!NOTE]
>
>La valeur **name** doit correspondre à la variable sandbox\_name dans votre environnement Postman

>[!TIP]
>
>Félicitations !  Vous êtes prêt à commencer à utiliser les API Experience Platform
