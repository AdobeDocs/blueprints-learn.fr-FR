---
hold: true
title: Définir les relations
description: Découvrez comment les descripteurs de relation lient un schéma client à un schéma de recherche dans le registre des schémas XDM via l’API.
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Définir les relations

## Descripteurs de relation

Pour créer une relation d’un schéma à un autre, vous devez créer un descripteur de relation dans le registre des schémas. Un exemple de corps de descripteur de schéma se présente comme suit :

Descripteur Un-à-un

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

Descripteur d’identité de référence

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## Votre objectif

Créez des identités de relation pour le schéma de compte client. Après avoir suivi les étapes de la section suivante, votre schéma doit se présenter comme suit.

![Schéma de compte client présentant les descripteurs d’identité de relation et de référence](assets/overview-schema-with-relationship-identities.png)
