---
title: Créer une identité de référence de plan
description: Utilisez l’API Schema Registry pour créer un descripteur d’identité de référence sur le schéma de recherche afin qu’il puisse être utilisé dans la segmentation par lots.
doc-type: article
solution: Experience Platform
exl-id: b3b8f480-af3b-4bf8-b74e-3842f59691b6
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Créer une identité de référence de plan

1. Cliquez sur la requête d’API `Step 3 - Reference Descriptor for Plan` dans le dossier `XDM Schema Lab -> Create Relationship Descriptors` .

   >[!CAUTION]
   >
   >Ne pas exécuter la requête... pour l’instant

   ![Étape 3 - Descripteur de référence pour la requête API de schéma de plan](assets/create-plan-reference-identity-step-3-descriptor-request.jpeg "Étape 3 - Descripteur de référence pour le schéma de plan")



2. Mettez à jour les propriétés suivantes dans le corps de l’appel API.

- Mettez à jour la valeur de la propriété `xdm:sourceSchema` sur la `$id` du schéma `Customer Account` que vous avez enregistré à partir de l’étape [Créer un schéma](../build-schema/create-schema.md)
- Mettez à jour la valeur du `xdm:sourceProperty` vers le chemin du champ `planID` à partir du schéma `Customer Account`

>[!NOTE]
>
>Utilisez la valeur de notation par points du champ `planId` du schéma `dep: Lookup Plan` et remplacez le `.` par `/`
>
>N&#39;oubliez pas non plus le `/` principal 😄

EXEMPLE UNIQUEMENT

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

>[!NOTE]
>
>Pensez à mettre à jour le nom du client ci-dessus (\_devbc) avec le vôtre



&#x200B;3. Enregistrez votre demande avant de continuer à utiliser le bouton `Save`

&#x200B;4. Exécutez l’API en cliquant sur le bouton `Send` .

Vous devriez maintenant voir une réponse `201 Created` comme ci-dessous

![201 Réponse créée après la création de dep : Plan Lookup reference identity descriptor](assets/create-plan-reference-identity-dep-plan-descriptor-result.png "dep : Plan Lookup Reference Identity descriptor")

>[!NOTE]
>
>Un descripteur d’identité de référence est toujours défini sur le schéma de recherche (à savoir sourceSchema)

>[!NOTE]
>
>Les descripteurs d’identité de référence sont créés automatiquement en arrière-plan lorsque vous créez des relations à partir de l’interface utilisateur du schéma. **Il vous suffit de les créer explicitement lors de l’utilisation des API pour créer des schémas**

>[!TIP]
>
>Génial ! Vous venez de créer tous les descripteurs requis pour mettre en relation le schéma `dep: Lookup Plan` avec le schéma `Customer Account` et vous avez permis de le référencer lors de la segmentation par lots
