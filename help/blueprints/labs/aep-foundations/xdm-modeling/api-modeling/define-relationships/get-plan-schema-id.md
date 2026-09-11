---
title: Obtenir l’ID du schéma de plan
description: Exécutez une requête dans l’API de registre des schémas client pour rechercher et enregistrer le $id du schéma de recherche de plan à utiliser dans un descripteur de relation.
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Obtenir l’ID du schéma de plan

## Liste de tous les schémas client

1. Cliquez sur la requête d’API `Step 1 - Get Lookup Schemas` dans le dossier `XDM Schema Lab -> Create Relationship Descriptors` .
1. Exécutez l’API en cliquant sur le bouton `Send` .

![Étape 1 - Obtenir la requête de l’API des schémas de recherche](assets/get-plan-schema-id-step-1-get-lookup-schemas.jpeg "Étape 1 - Obtenir les schémas de recherche")

>[!NOTE]
>
>Cet appel GET récupère tous les schémas qui existent dans la partie « tenant » du registre des schémas (c’est-à-dire les schémas créés sur mesure). Il suffit de rechercher le schéma **Plan** pour pouvoir l’associer au schéma Compte client.



## Identification du schéma du plan

1. Recherche du schéma `dep: Plan [Lookup] ` dans la réponse des appels
1. Copiez le `$id` du schéma et enregistrez-le quelque part pour référence ultérieure

![Dep : Schéma de recherche de plan $id situé dans la réponse de l’API](assets/get-plan-schema-id-dep-lookup-plan-schema-sid.png "dep : Schéma de plan de recherche $id")

>[!NOTE]
>
>Ce schéma doit déjà être prédéployé dans votre sandbox

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré `$id` du schéma quelque part.  Il sera nécessaire ultérieurement pour créer le descripteur de relation
