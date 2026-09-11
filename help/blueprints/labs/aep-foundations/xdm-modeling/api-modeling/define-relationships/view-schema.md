---
hold: true
title: Afficher le schéma
description: Affichez la relation de recherche du schéma de compte client avec le schéma de plan au moyen de l’interface utilisateur du schéma et de l’API Get Schema.
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Afficher le schéma

## Affichage via l’interface utilisateur

1. Ouvrez votre navigateur et revenez à la section `Schema -> Browse` .
1. Rechercher le `Sample Customer Schema - <your sandbox number>` de schéma
1. Notez que la relation avec la `dep: Plan [Lookup]` est définie

![Exemple de schéma client dans l’interface utilisateur d’Experience Platform montrant la relation dep: Plan Lookup](assets/view-schema-relationship-to-plan-lookup-schema.png)


## Affichage via l’API

1. Sélectionnez l’API `Step 4 - Get Customer Account Schema and its descriptors` en cliquant dessus.

![Étape 4 - Obtenir le schéma du compte client et son appel API de descripteurs](assets/view-schema-step-4-get-schema-and-descriptors.png "Étape 4 - Obtenir le schéma du compte client et ses descripteurs")



2. Dans l’URL de la requête, remplacez la `<replace me>` par la `$meta:altId` que vous avez enregistrée dans la section précédente [Créer un schéma](../build-schema/create-schema.md) comme illustré ci-dessous

![Requête de l’étape 4 avec le méta:altId ajoutée à la requête URL](assets/view-schema-final-step-4-request.png "Étape finale 4")



3. Enregistrez la demande à l’aide du bouton `Save` .

4. Exécutez la requête en cliquant sur le bouton `Send` .

Vous devriez maintenant voir une réponse `200 OK` et vous devriez être en mesure de naviguer jusqu’à la fin du schéma que vous avez créé pour voir l’identité à travers le prisme de la structure JSON XDM



![Descripteur de relation visible dans le schéma de compte client JSON](assets/view-schema-relationship-descriptor.png "Relationship Descriptor")



![Descripteur d’identité de référence visible dans le schéma de compte client JSON](assets/view-schema-reference-identity-descriptor.png "Descripteur d’identité de référence")
