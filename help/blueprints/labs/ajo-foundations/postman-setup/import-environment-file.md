---
hold: true
title: Importer le fichier d’environnement
description: Importez le fichier d’environnement Postman et définissez les variables globales comme EDGE_REGION nécessaires aux appels API dans le bootcamp.
doc-type: article
solution: Experience Platform
exl-id: a5d45656-e3f5-4207-823c-ad33d4ef26a4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Importer le fichier d’environnement

## Objectif

Sur cette page, vous allez importer le fichier d’environnement Postman.  Ce fichier contient un certain nombre de variables globales qui seront utilisées dans divers appels API que vous effectuerez dans d’autres ateliers du camp d’amorçage.

## Importer le fichier d’environnement

1. Téléchargez le fichier **Bootcamp.postman\_environment.json** d’AJO :

Télécharger le fichier — [AJO Bootcamp.postman_environment.json](assets/ajo-bootcamp.postman_environment.json)

2. Lancez Postman sur votre ordinateur local.
3. Si nécessaire, passez au Workspace que vous utilisez pour ces laboratoires (si vous utilisez un Workspace) et cliquez sur le bouton **Importer**.

![Postman commence l&#39;import](assets/import-environment-file-click-import-button.png)

4. Collez l’URL locale du fichier **Bootcamp.postman\_environment.json** d’AJO dans la zone de texte modale de l’importation ou déposez-la dans la boîte de dialogue d’importation.  Cela devrait déclencher une importation automatique

Boîte de dialogue d’importation de ![Postman affichant l’option permettant de coller une URL de fichier](assets/import-environment-file-import-button-overlay.png "Import Postman via URL")

Boîte de dialogue d’importation de ![Postman acceptant un fichier déposé par glisser-déposer](assets/import-environment-file-drag-and-drop-import.png "importation de Postman par glisser-déposer")

5. Une fois l’importation effectuée, vérifiez que l’environnement existe en cliquant sur l’onglet **Environnements** dans la barre latérale gauche. Vous voyez que l’environnement AJO Bootcamp est désormais disponible.

![Valider l’importation de l’environnement](assets/import-environment-file-validate-environment-imported.png)

## Définition des variables d’environnement

Postman a été conçu pour tester et interagir avec les API. Cependant, nous l’utilisons pour simuler les accès à AEP Web SDK à partir d’un navigateur ou pour les appels de collecte de données en temps réel côté serveur. Bien qu’il s’agisse toujours d’appels API au sens le plus strict du terme, il ne s’agit pas d’appels API standard qui nécessitent des éléments tels que des jetons d’autorisation dans l’en-tête . Les variables d’environnement de ces ateliers sont principalement utilisées pour les variables dans les chemins d’URL (une étant utilisée dans un en-tête).

1. Si nécessaire, cliquez sur l’onglet **Environnements** dans la barre latérale gauche de Postman
2. Cliquez sur le fichier d’environnement **Bootcamp**. Vous voyez certaines valeurs à renseigner

![Variables d’environnement Postman avec des valeurs vides qui doivent être renseignées](assets/import-environment-file-values-need-filling-in.png "Vérifiez les variables Postman dans les environnements")

3. Ignorez la valeur DATASTREAM\_CONFIG pour l’instant. Vous allez créer une configuration de train de données dans un atelier ultérieur.
4. Mettez à jour le champ **EDGE\_REGION** avec le code de région le plus proche de l’endroit où vous vous trouvez physiquement pour ce bootcamp, en utilisant le tableau ci-dessous comme recherche.

| **Région** | **Code de région** |
| ---------- | --------------- |
| Ouest des États-Unis | or2 |
| Est des États-Unis | va6 |
| Europe | irl1 |
| Australie | aus3 |
| Japon | jpn3 |
| Asie | spg3 |

Une fois cette opération terminée, votre fichier d’environnement doit ressembler à ceci :



![Vérifier la variable de région Postman](assets/import-environment-file-region-variable-set.png)

5. Vous devez maintenant enregistrer vos variables d’environnement, mais il n’existe pas de bouton Enregistrer dans l’interface utilisateur de Postman. Utilisez les touches de raccourci Windows ou Mac pour enregistrer (ctrl+s sous Windows, par exemple). Vous savez que vos modifications ont été enregistrées lorsque vous voyez un message **Modifications enregistrées** dans le coin inférieur droit de l’interface utilisateur de Postman :

![Vérifier les modifications enregistrées](assets/import-environment-file-changes-saved-confirmation.png)

>[!TIP]
>
>Félicitations ! Vous avez terminé votre fichier d’environnement Postman
