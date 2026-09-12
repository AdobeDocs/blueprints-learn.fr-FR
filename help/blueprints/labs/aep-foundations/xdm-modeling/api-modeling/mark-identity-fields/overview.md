---
title: Marquer les champs d’identité
description: Découvrez comment les descripteurs d’identité marquent les champs de schéma comme identités principales ou non principales à l’aide de l’API XDM Schema Registry.
doc-type: overview-page
solution: Experience Platform
exl-id: f6498584-0f4d-4baf-86b5-b00cc78e2ba7
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Marquer les champs d’identité

## Descripteurs d’identité

Pour marquer un champ en tant qu’identité, vous devez créer un descripteur d’identité dans le registre des schémas. Un exemple de corps de descripteur de schéma se présente comme suit :

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

- **&#x200B;**&#x200B;-> toujours défini sur `xdm:descriptorIdentity`
- **xdm\:sourceSchema** -> `$id` du schéma où se trouve le champ
- **xdm\:sourceVersion** -> toujours 1
- **xdm\:sourceProperty** -> chemin d’accès du champ dans le schéma
- **xdm\:namespace** -> code d’espace de noms d’identité dans lequel le champ doit être stocké
- **xdm\:property** -> toujours `xdm:code`
- **xdm\:isPrimary** -> si une identité principale est `true`, elle est `false`


## Votre objectif

Créez des identités principales et secondaires pour le schéma de compte client. Après avoir suivi les étapes de la section suivante, votre schéma doit se présenter comme suit.

![Schéma de compte client après la création des descripteurs d’identité principaux et non principaux](assets/overview-schema-with-primary-and-non-primary-identities.png)
