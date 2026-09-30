---
title: Correction des erreurs MAPPER pour CreateDate
description: Dépanner et résoudre une erreur MAPPER causée par une valeur createDate mal formatée qui se transformait en un champ vide.
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%
---

# Correction des erreurs MAPPER pour CreateDate

Dans cet exercice, vous devez comprendre comment supprimer l’erreur MAPPER que nous avons vue dans le Lab d’ingestion par lots. L’erreur doit être corrigée car, même si createDate n’est pas un champ obligatoire, les enregistrements sont toujours ingérés, car la date mal formatée est transformée en un champ vide à la place.

![&#x200B; valeur createDate avec un format non valide provoquant l’erreur MAPPER &#x200B;](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
