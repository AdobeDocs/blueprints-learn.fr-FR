---
title: Afficher le schéma
description: Affichez un schéma client nouvellement créé dans l’interface utilisateur d’Experience Platform et via un appel de l’API Get Schema.
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Afficher le schéma

## Affichage via l’interface utilisateur

1. Ouvrez votre navigateur et revenez à la section `Schema -> Browse` .

   >[!NOTE]
   >
   >Actualisez l’interface utilisateur pour la voir, car vous venez de la créer et vous devez interroger à nouveau le registre des schémas

2. Rechercher le `Sample Customer Schema - <your sandbox number>` de schéma

3. Notez que la classe requise et les groupes de champs associés sont ajoutés au schéma

![Exemple de schéma client affiché dans l’interface utilisateur d’Experience Platform avec sa vue de classe et de groupes de champs](assets/view-schema-ui-view-of-sample-customer-schema.png "IU de l’exemple de schéma client")


## Affichage via l’API

1. Sélectionnez l’API `Step 5 - Get Customer Account Schema` en cliquant dessus.
1. Dans l’URL de la requête, remplacez la `<replace me>` par la `$meta:altId` que vous avez enregistrée de la section précédente (Créer votre schéma) à la fin de l’appel, comme illustré ci-dessous
1. Enregistrez les modifications apportées à la requête
1. Exécutez la requête en cliquant sur le bouton `Send` .

![Étape 5 - Appel API Get Customer Account Schema](assets/view-schema-step-5-get-customer-account-schema.jpeg "Étape 5 - Get Customer Account Schema")



Exemple de votre requête finale après l’ajout de la `$meta:altId`

![Requête de l’étape 5 avec le méta:altId ajoutée à la requête URL](assets/view-schema-final-step-5-request.png "Étape finale 5")



Si vous avez reçu une réponse `200 OK`, vous devriez être en mesure de parcourir le schéma que vous avez créé à travers l’objectif de la structure XDM JSON

Réponse OK ![200 affichant l’exemple complet de schéma de compte client JSON](assets/view-schema-sample-customer-account-schema.png "Exemple de schéma de compte client")
