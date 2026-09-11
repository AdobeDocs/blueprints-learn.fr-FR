---
hold: true
title: Créer une identité principale
description: Utilisez l’API Schema Registry pour créer un descripteur d’identité customerID principal pour le schéma Compte client.
doc-type: article
solution: Experience Platform
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Créer une identité principale

1. Cliquez sur la requête d’API `Step 1 - Create Primary Identity for Customer Account Schema` dans le dossier `XDM Schema Lab -> Create Identity Descriptors` .

![Étape 1 - Création d’une identité de Principal pour la requête Postman du schéma de compte client](assets/create-primary-identity-step-1-postman-request.jpeg "Étape 1 - Création d’une identité de Principal pour le schéma de compte client")

>[!CAUTION]
>
>Ne pas exécuter la requête pour le moment



1. Mettez à jour la valeur `xdm:sourceSchema` dans le corps de la requête à l’aide de la `$id` que vous avez enregistrée à partir de l’étape [Créer un schéma](../build-schema/create-schema.md) du Lab

1. Mettez à jour la valeur `xdm:isPrimary` dans le corps de la requête vers `true`

EXEMPLE UNIQUEMENT

```json
{
  "@type": "xdm:descriptorIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/customerID",
  "xdm:namespace": "customerID",
  "xdm:property": "xdm:code",
  "xdm:isPrimary": true
}
```

>[!NOTE]
>
>Pensez à mettre à jour le nom du client ci-dessus (\_devbc) avec le vôtre



1. Enregistrez votre demande avant de continuer à utiliser le bouton `Save`

1. Exécutez l’API en cliquant sur le bouton `Send` . Vous devriez maintenant voir une réponse `201 Created` comme ci-dessous

![201 Création d’une réponse après la création réussie du descripteur d’identité primaire](assets/create-primary-identity-201-created-response.png "Descripteur d’identité primaire créé avec succès")

> [!TIP]
>
>Félicitations !  Vous venez de créer un descripteur d’identité principale dans votre schéma
