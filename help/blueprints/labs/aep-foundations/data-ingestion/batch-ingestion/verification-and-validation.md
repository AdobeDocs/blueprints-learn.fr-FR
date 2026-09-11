---
hold: true
title: Vérification et validation
description: Prévisualisez un jeu de données ingéré dans l’interface utilisateur et exécutez des requêtes SQL pour vérifier les enregistrements ingérés par lots et les champs de schéma imbriqués.
doc-type: article
solution: Experience Platform
exl-id: 7e7cd43d-cc24-4a40-a175-2c651436ab79
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Vérification et validation

## Prévisualiser le jeu de données

1. Cliquez sur **Jeux de données**
1. **Recherchez** puis **cliquez** le nom du jeu de données que vous avez créé.

![Recherche et clic sur le nom du jeu de données dans le volet Jeux de données](assets/verification-and-validation-access-dataset-in-datasets-pane.png "Accès au jeu de données dans le volet Jeux de données")



1. Cliquez sur **Prévisualiser le jeu de données** dans le coin supérieur droit

![Emplacement du bouton Aperçu du jeu de données dans le coin supérieur droit de l’écran du jeu de données](assets/verification-and-validation-preview-dataset-button-location.png "L’aperçu du jeu de données se trouve dans le coin supérieur droit")



1. **Vérifier** et **valider** les mêmes enregistrements que ceux ingérés en cliquant sur le volet de gauche affichant la hiérarchie du schéma.

![Aperçu du jeu de données avec le volet de hiérarchie du schéma affichant les enregistrements ingérés](assets/verification-and-validation-verify-and-validate-the-dataset.png)

>[!NOTE]
>
>**Prévisualiser le jeu de données** affiche le lot réussi le plus récent de ce jeu de données. Vous ne pouvez pas voir les lots précédents. En outre, les données complexes telles que les tableaux et les mappages ne sont pas visibles aujourd’hui et apparaissent sous la forme de colonnes vides. Ne paniquez pas ! Pour obtenir une vue plus complète, vous devez utiliser SQL pour explorer le jeu de données, comme expliqué ci-dessous.



## Jeu de données de requête

1. **Fermer** l’aperçu
1. Dans l’écran Jeu de données, cliquez sur l’icône de copie sur **Nom du tableau**. Dans l’exemple d’écran ci-dessous, le nom du tableau est `customer_account_sm`

![Icône Copier en regard du nom du tableau dans l’écran Jeu de données](assets/verification-and-validation-copy-table-name.png "Copiez le nom du tableau")



1. Accédez à la section **Requêtes**

1. Cliquez sur **Créer une requête**

![Bouton Créer une requête dans la section Requêtes](assets/verification-and-validation-access-the-query-editor.png)



1. Copiez et collez la requête SQL suivante dans l’**Éditeur**. N’oubliez pas de remplacer `<table_name>` par la valeur obtenue à l’étape 6.

```sql
SELECT * FROM <table_name>
```



1. Appuyez sur le bouton **Lecture**.

![Interface du requêteur avec requête SQL et bouton Lire](assets/verification-and-validation-query-editor-interface.png "Interface du requêteur")



1. **Prévisualiser** les résultats

1. Exécutez également la requête SQL suivante pour récupérer le schéma XDM avec les données :

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```

Pour accéder aux données du `postalCode` **nœud**, vous pouvez saisir :

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Félicitations !  Vous avez correctement ingéré et créé un échantillon de profils clients en temps réel
