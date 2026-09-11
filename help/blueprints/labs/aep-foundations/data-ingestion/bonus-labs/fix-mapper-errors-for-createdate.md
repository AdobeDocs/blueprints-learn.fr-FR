---
title: Correction des erreurs MAPPER pour CreateDate
description: Dépanner et résoudre une erreur MAPPER causée par une valeur createDate mal formatée qui se transformait en un champ vide.
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Correction des erreurs MAPPER pour CreateDate

Dans cet exercice, vous devez comprendre comment supprimer l’erreur MAPPER que nous avons vue dans le Lab d’ingestion par lots. L’erreur doit être corrigée car, même si createDate n’est pas un champ obligatoire, les enregistrements sont toujours ingérés, car la date mal formatée est transformée en un champ vide à la place.

![ valeur createDate avec un format non valide provoquant l’erreur MAPPER ](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
