---
hold: true
title: Créer des groupes de champs personnalisés
description: Utilisez l’API Schema Registry pour créer un groupe de champs personnalisé Détails du compte client et enregistrer son $id en vue de l’utiliser dans un schéma ultérieur.
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Créer des groupes de champs personnalisés

## Structure du groupe de champs

Un groupe de champs est toujours composé des champs suivants. Cela apparaîtra dans la requête à l’étape suivante.

| Valeurs requises | Description |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| titre | Nom du groupe de champs que vous souhaitez créer dans le registre des schémas. Notez que le nom DOIT ÊTRE UNIQUE. |
| description | Brève description de l’objectif du groupe de champs |
| type | Toujours un objet |
| meta\:intendedToExtend | Définit les classes avec lesquelles le groupe de champs peut être utilisé. Les classes sont toujours référencées par leur valeur `$id` |
| allOf | Décrit les ressources qui peuvent être incluses dans le groupe de champs. Pour les champs définis personnalisés, le chemin est toujours `#/definitions/customFields` |
| define.customFields... | Il s’agit de la structure de schéma JSON par défaut requise pour créer des groupes de champs personnalisés. Il doit correspondre au `allOf` d&#39;en haut |
| \&lt;TENANT\_NAME> | Le nom du client (c’est-à-dire un nom unique) est créé pendant le processus d’approvisionnement. Cela permet de s’assurer que les personnalisations effectuées n’entrent pas en conflit avec les modifications existantes ou futures du registre des schémas d’Adobe |



## Créer un groupe de champs Détails du compte client

1. Cliquez sur l’appel API request `Step 2 - Create Customer Account Details Field Group` dans le dossier `XDM Schema Lab -> Create Schema` .



![Étape 2 - Demande d’API du groupe de champs Créer des détails de compte client](assets/create-custom-field-groups-step-2-field-group-request.png "Étape 2 - Groupe de champs Créer des détails de compte client")



Vérifiez le corps de la requête avant de l’exécuter. Notez que les champs obligatoires mentionnés dans la section Structure de groupe de champs se présentent comme suit :

![Champs obligatoires d’un groupe de champs personnalisé, comme indiqué dans le corps de la demande](assets/create-custom-field-groups-field-group-structure.png "Structure de groupe de champs")



![La propriété allOf faisant référence aux définitions de champ personnalisées path](assets/create-custom-field-groups-field-group-structure-allof.png "Field Group Structure allOf")

>[!NOTE]
>
>Notez que dans l’image située à droite au-dessus de la `allOf`, le chemin d’accès est « /définitions/customFields ».  Doit correspondre à la structure définie dans le schéma (image à gauche), car il indique au système XDM où localiser les objets créés personnalisés.
>
>![Comparaison mettant en surbrillance la manière dont le chemin allOf doit correspondre au chemin des définitions de champ personnalisé](assets/create-custom-field-groups-allof-path-highlighted.png)



Notez également comment chaque champ spécifique de la feuille de mappage est justifié dans la structure JSON XDM.



![Mappage de la notation par points de plan de feuille de calcul convertie en structure JSON XDM](assets/create-custom-field-groups-plan-dot-notation-to-xdm-json.png "la notation par points de plan au format JSON XDM")



![Mappage de la notation de point de compte de feuille et d’ID client converti en XDM](assets/create-custom-field-groups-account-customer-id-dot-notation-to-xdm.png "Account et de la notation de point d’ID client converti en XDM")



&#x200B;2. Mettez à jour les `title` et `description` du groupe de champs à l’aide du format suivant : `Customer Account Details - Sandbox <your number here>`



![Exemple de titre et de description renseigné pour le groupe de champs personnalisés](assets/create-custom-field-groups-field-group-title-description-example.png "Groupe de champs Titre et description Exemple")



&#x200B;3. Exécutez en cliquant sur le bouton `Send` .  Vous devriez voir une réponse similaire à la capture d’écran ci-dessous.

&#x200B;4. Copiez la valeur `$id` de votre groupe de champs Détails du compte client nouvellement créé.

![Réponse API réussie après la création du groupe de champs personnalisés](assets/create-custom-field-groups-step-2-create-custom-field-group-success.png "Étape 2 - Création réussie du groupe de champs personnalisés")

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré le `$id` quelque part.  Elle sera nécessaire ultérieurement pour créer le schéma Compte client
>
>
