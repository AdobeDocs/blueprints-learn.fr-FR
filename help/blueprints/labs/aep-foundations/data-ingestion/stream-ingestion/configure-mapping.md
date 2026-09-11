---
hold: true
title: Configurer le mappage
description: Importez le jeu de mappages à partir du Lab d’ingestion par lots et mettez à jour les champs de date calculés pour qu’ils correspondent au format de date de la source de diffusion en continu.
doc-type: article
solution: Experience Platform
exl-id: c05792af-5eab-4e62-a26e-a54478a988a8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Configurer le mappage

&#x200B;> [!NOTE]
>
>Ne suivez cette section que si vous avez terminé avec succès l’atelier d’ingestion par lots.  Sinon, suivez les étapes [Mappage de données](../batch-ingestion/mapping-data/overview.md) qui se trouvent dans le Lab d’ingestion par lots.

## Importer le jeu de mappages

Si vous avez terminé l’atelier d’ingestion par lots, vous pouvez réutiliser le jeu de mappages que vous y avez créé 😄🎉

Effectuez les étapes suivantes :

1. Cliquez sur le bouton **Importer le mappage** sur l’écran du mappage

![Bouton Importer le mappage sur l’écran du mappage](assets/configure-mapping-import-mapping-button.png)



1. Sélectionnez le flux de données que vous avez créé dans la section Ingestion par lots et sélectionnez-le.  Son nom doit être le suivant : **Lot de comptes client v2 - \&lt;vos initiales>.**.

![Choix du flux de données d’ingestion par lots à partir duquel importer son jeu de mappages](assets/configure-mapping-choose-batch-ingestion-dataflow.png)



Après l’importation, des erreurs apparaîtront.  Cela est dû au fait que le format de date utilisé pour le champ date de naissance dans le fichier d’exemple a changé.

- Fichier d’échantillon de lot utilisé -> mm/jj/aaaa
- Fichier d’exemple de flux utilisé -> aaaa-mm-jj

Les champs calculés qui utilisent les fonctions **date** devront être mis à jour pour tenir compte du changement du format de date utilisé.

![Erreurs de mappage affichées après l’importation du jeu de mappages d’ingestion par lots](assets/configure-mapping-mapping-after-the-import.png)



## Mettre à jour les champs calculés

Mettez à jour chaque champ calculé en cliquant simplement sur l’icône de flèche en regard de chaque champ calculé, puis validez vos mappages

![Icône de flèche à cliquer pour modifier la formule d’un champ calculé](assets/configure-mapping-arrow-to-edit-calculated-field-formula.png)

| Champ cible | Nouveau champ calculé |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| person.bornYear | date\_part(« aaaa »,date(naissance\_Date,« aaaa-M-j »)) |
| person.bornDayAndMonth | concat(date\_part(« mm », date(naissance\_Date, « aaaa-M-j »)).toString(), « - », date\_part(« jj », date(naissance\_Date, « aaaa-M-j »)).toString()) |
