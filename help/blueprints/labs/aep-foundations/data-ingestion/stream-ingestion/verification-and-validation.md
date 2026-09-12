---
title: Vérification et validation
description: Prévisualisez un jeu de données diffusé dans l’interface utilisateur et exécutez des requêtes SQL pour vérifier les enregistrements ingérés et les champs de schéma imbriqués.
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Vérification et validation

## Prévisualiser le jeu de données

1. Cliquez sur **Jeux de données**
1. **Recherchez** puis **cliquez** le nom du jeu de données que vous avez créé.

   ![Accès au jeu de données créé dans le volet Jeux de données](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "Accédez au jeu de données dans le volet Jeux de données")



1. Cliquez sur **Prévisualiser le jeu de données** dans le coin supérieur droit

   ![Le bouton Aperçu du jeu de données se trouve dans le coin supérieur droit de l’écran du jeu de données](assets/verification-and-validation-preview-dataset-button.png "L’aperçu du jeu de données se trouve dans le coin supérieur droit ")



1. **Vérifier** et **valider** les mêmes enregistrements que ceux ingérés en cliquant sur le volet de gauche affichant la hiérarchie du schéma.

![Vérification et validation des enregistrements ingérés à l&#39;aide du volet de hiérarchie des schémas](assets/verification-and-validation-verify-and-validate-the-dataset.png "Vérification et validation du jeu de données")

>[!NOTE]
>
>**Prévisualiser le jeu de données** affiche uniquement les premières lignes du jeu de données. Les objets de tableau ne sont pas visibles.



## Jeu de données de requête

1. **Fermer** l’aperçu
1. Dans l’écran Jeu de données, cliquez sur l’icône de copie sur **Nom du tableau**. Dans l’exemple d’écran ci-dessous, le nom du tableau est `customer_account_sm`

   ![Copie du nom de la table à partir de l’écran Jeu de données pour une utilisation dans une requête](assets/verification-and-validation-copy-the-table-name.png "Copiez le nom de la table")



1. Accédez à la section **Requêtes**

1. Cliquez sur **Créer une requête**

   ![Accès au requêteur à partir de la section Requêtes](assets/verification-and-validation-access-the-query-editor.png "Accès au requêteur")



1. Activez le bouton (bascule) **Éditeur de requêtes amélioré**

   ![Interface du requêteur avec le bouton (bascule) Query Editor amélioré activé](assets/verification-and-validation-enhanced-query-editor-toggle.png "Interface du requêteur")



1. Copiez et collez la requête SQL suivante dans l’**Éditeur**. N’oubliez pas de remplacer `<table_name>` par la valeur obtenue à l’étape 2.

   ```sql
   SELECT * FROM <table_name>
   ```



1. Appuyez sur le bouton **Lecture**.

1. **Prévisualiser** les résultats.

1. Exécutez également la requête SQL suivante pour récupérer le schéma XDM avec les données :

   ```sql
   SELECT to_json(shippingAddress) FROM <table_name>
   ```



1. Pour accéder aux données du `postalCode` **nœud**, vous pouvez saisir :

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Félicitations !  Vous avez correctement ingéré et créé un échantillon de profils clients en temps réel
