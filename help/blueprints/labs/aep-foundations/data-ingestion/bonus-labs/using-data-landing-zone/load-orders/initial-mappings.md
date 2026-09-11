---
hold: true
title: Mappages initiaux
description: Mappez manuellement les champs _id et timestamp requis pour un jeu de données d’événement d’expérience à l’aide des expressions de champ calculées.
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Mappages initiaux

Comme dans l’exercice précédent, vous devrez vérifier le mappage et, dans certains cas, le modifier.

## Vérifier les recommandations ML

1. À l’étape Mappage , les recommandations ML mappent automatiquement la plupart des attributs. Cependant, plusieurs erreurs s’affichent également. L’écran initial peut ressembler à ce qui suit.

![Écran de mappage affichant _id et l’horodatage comme champs non mappés non recommandés par ML](assets/initial-mappings-id-timestamp-unmapped-fields.png "_id. L’horodatage est deux champs pour lesquels ML Recommender ne générera pas le mappage")

>[!NOTE]
>
>Puisque nous mappons un jeu de données d’événement d’expérience pour la première fois, notez que **\_id** et **timestamp** ne sont jamais recommandés ou mappés par défaut pour les événements d’expérience. Vous devez vous assurer manuellement que ces éléments sont correctement mappés.

## Mapper les champs \_id, timestamp et order.\_devbc.acqSource

1. Pour mapper **\_id,** écrivez l’expression de champ calculé suivante, puis cliquez sur Aperçu

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![Le champ calculé pour le mappage _id, prêt à être enregistré](assets/initial-mappings-calculated-field-for-id-mapping.png "Le champ calculé pour le mappage _id ressemblera à ceci. Cliquez sur Enregistrer pour enregistrer le champ calculé")

![Mapper le champ calculé à l’attribut _id](assets/initial-mappings-map-calculated-field-to-id.png "Mapper le champ calculé à _id")

1. Assurez-vous que le champ **horodatage** du schéma cible est mappé au champ calculé suivant :

```none
lastOrderStatusUpdate
```

![Aperçu de l’expression du champ calculé pour le mappage d’horodatage](assets/initial-mappings-expression-preview.png "Écrivez l’expression suivante et cliquez sur Aperçu. NOTEZ que cette valeur est sensible à la casse et doit être écrite exactement comme suit ")

![Mappage de l’expression de champ calculée « inStore » à order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. Mappez l’expression de champ calculée **« inStore »** sur **order.\_devbc.acqSource**

![Écriture de l’expression du champ calculé « inStore » et clic sur Aperçu](assets/initial-mappings-write-instore-expression-preview.png "Écrivez l’expression suivante, puis cliquez sur Aperçu. NOTEZ que cette valeur est sensible à la casse et doit être écrite exactement comme suit ")

## Gestion des mappages en double

Si l’écran de mappage se plaint désormais qu’il existe un mappage en double, tel que **orderStatus** mappé à **order.\_devbc.acqSource,** cliquez sur l’icône « - » pour supprimer le mappage.

> [!NOTE]
>
>N’oubliez pas que plusieurs champs d’entrée ne peuvent pas être mappés au même champ de sortie, car cela rend le mappage ambigu. Cependant, un seul champ d’entrée peut être mappé à plusieurs champs de sortie dans le schéma XDM.

![Avertissement de mappage en double pour orderStatus mappé à order._devbc.acqSource](assets/initial-mappings-duplicate-mapping-warning.png "Mappage en double pour orderStatus mappé à order._devbc.acqSource")



![Avertissement de mappage en double pour la commande._devbc.acqSource après la création du champ calculé](assets/initial-mappings-duplicate-mapping-for-acqsource.png "Mappage en double pour la commande._devbc.acqSource depuis que nous avons créé un champ calculé et que nous lui avons déjà associé. ")
