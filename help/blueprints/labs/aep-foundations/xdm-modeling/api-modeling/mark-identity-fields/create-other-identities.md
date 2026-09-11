---
hold: true
title: Créer d’autres identités
description: Utilisez l’API Schema Registry pour créer un descripteur d’identité d’adresse e-mail non principale pour le schéma Compte client.
doc-type: article
solution: Experience Platform
exl-id: 22c40299-fb93-4d41-a23b-f8629df3e7b9
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Créer d’autres identités

1. Cliquez sur l’appel API `Step 2 - Create Email Address Identity for Customer Account Schema` dans le dossier `XDM Schema Lab -> Create Identity Descriptors` .

>[!CAUTION]
>
>Ne pas exécuter la requête... pour l’instant

![Étape 2 - Créer une identité d’adresse e-mail pour la requête Postman de schéma de compte client](assets/create-other-identities-step-2-postman-request.jpeg "Étape 2 - Créer un descripteur d’identité d’adresse e-mail")



1. Mettez à jour la valeur `xdm:sourceSchema` dans le corps de la requête à l’aide de la `$id` que vous avez enregistrée à partir de l’étape [Créer un schéma](../build-schema/create-schema.md) du Lab

1. Mettez à jour la valeur `xdm:isPrimary` dans le corps de la requête vers `false`

EXEMPLE UNIQUEMENT

```json
{
  "@type": "xdm:descriptorIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/personalEmail/address",
  "xdm:namespace": "Email",
  "xdm:property": "xdm:code",
  "xdm:isPrimary": false
}
```

>[!NOTE]
>
>Pensez à mettre à jour le nom du client ci-dessus (\_devbc) avec le vôtre



1. Enregistrez votre demande avant de continuer à utiliser le bouton `Save`

1. Exécutez l’API en cliquant sur le bouton `Send` . Vous devriez maintenant voir une réponse `201 Created` comme ci-dessous

![201 Réponse créée après la création réussie du descripteur d’identité d’adresse e-mail](assets/create-other-identities-201-created-response.png "descripteur d’identité réussi pour l’adresse e-mail")
