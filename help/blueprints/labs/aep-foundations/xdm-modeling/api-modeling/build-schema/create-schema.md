---
title: Créer Un Schéma
description: Utilisez l’API Schema Registry pour assembler un schéma client à partir d’une classe de profil et de références de groupes de champs standard et personnalisés.
doc-type: article
solution: Experience Platform
exl-id: 78ebc5b8-d088-48e9-857f-87085a87a280
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Créer Un Schéma

## Modifier le corps de l’API

>[!CAUTION]
>
>**Ne pas exécuter l’appel...pour l’instant**

1. Cliquez sur l’appel API `Step 4 - Create Customer Account Schema` dans le dossier `XDM Schema Lab -> Create Schema` .

   ![Étape 4 - Créer un appel API de schéma de compte client dans la collection Postman](assets/create-schema-click-on-the-step-4-create-customer-account-schema.png)



2. Ouvrez le corps de l’appel et affichez la structure de la définition d’un schéma. N’oubliez pas qu’un schéma est toujours composé d’une seule (1) classe et d’un ou plusieurs groupes de champs.

3. Renseignez les champs `title` et `description` dans le corps du schéma avec les éléments suivants :

   - Titre -> `Sample Customer Schema - <your sandbox number>`
   - Description -> `Sample Customer Schema - <your sandbox number>`

4. Renseignez les champs de `$ref` avec les `$ids` que vous avez enregistrées à partir des sections de l’atelier précédentes que vous avez terminées : [Créer des groupes de champs personnalisés](./create-custom-field-groups.md) et [Obtenir la classe de profil](./get-profile-class.md). Vous devez disposer de $ids pour chacun des éléments suivants :

   - Classe -> XDM Individual Profile
   - Groupe de champs -> Détails démographiques
   - Groupe de champs -> Coordonnées personnelles
   - Groupe de champs -> Détails du consentement et des préférences
   - Groupe de champs (personnalisé) -> Détails du compte client

   ![Corps de requête de schéma vide avant d’ajouter des références de classe et de groupe de champs](assets/create-schema-empty-schema-api-body.png "Corps d’API de schéma vide")



5. Vérifiez que le corps final ressemble à ceci

![Le corps de la requête de schéma terminé avec le titre, la description et toutes les valeurs $ref renseignées](assets/create-schema-example-of-final-body-payload.png "Exemple de payload de corps finale")

>[!NOTE]
>
>L’ordre des `$refs` n’a pas d’importance, pas plus que l’emplacement des `title` et des `description` dans le corps.



## Exécution de l’API

1. Enregistrez les modifications apportées à la requête API avant de continuer.
1. Exécutez l’API en cliquant sur le bouton `Send` .

Une réponse réussie pour la création du schéma doit entraîner un statut `201 Created` et doit ressembler à l’image ci-dessous

>[!WARNING]
>
>N’exécutez pas à nouveau la requête en cas de réussite

![201 Réponse créée après la création réussie du schéma via l&#39;API Step 4](assets/create-schema-sample-response-from-executing-the-step-4-api.png "Exemple de réponse provenant de l&#39;exécution de l&#39;API Step 4")


## Recherchez et enregistrez le schéma $id

1. Après avoir exécuté la requête d’API, copiez les `$id` et `$meta:altId` de la réponse
1. Enregistrez les valeurs quelque part pour pouvoir les réutiliser ultérieurement

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré le `$id` et `$meta:altId` quelque part.  Ils seront nécessaires lors des prochaines étapes du laboratoire

>[!TIP]
>
>**Félicitations ! Vous venez de créer un schéma en utilisant uniquement les API**
