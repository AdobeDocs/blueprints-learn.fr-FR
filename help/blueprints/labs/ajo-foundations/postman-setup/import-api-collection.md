---
hold: true
title: Importer la collection d’API
description: Importez la collection d’API Postman du bootcamp et vérifiez que ses variables d’environnement se résolvent correctement sur votre sandbox.
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# Importer la collection d’API

## Objectif

Au cours de cette étape, vous allez importer la collection d’API qui contient toutes les différentes requêtes que vous devrez effectuer tout au long du bootcamp.  Ces requêtes d’API dépendent du fichier d’environnement que vous venez d’importer.



## Importer la collection de demandes

1. Téléchargez le fichier **AJO Bootcamp (Labs).postman\_collection.json** :

Télécharger le fichier — [Bootcamp AJO (Labs).postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

2. Comme auparavant, cliquez sur le bouton **Importer**.
3. Collez l’URL locale du fichier **AJO Bootcamp (Labs).postman\_collection.json** dans la zone de texte modale de l’importation ou déposez-la dans la boîte de dialogue d’importation.  Cela déclenche une importation automatique.
4. Une fois le processus d’importation terminé, cliquez sur **Collections** dans la barre de navigation de gauche, développez le dossier **Bootcamp (Labs)** d’AJO, et la collection nouvellement importée s’affiche

![vérifier l’importation de la collection postman](assets/import-api-collection-verify-collection-imported.png)

>[!TIP]
>
>Félicitations !  Vous avez correctement importé la collection Postman du bootcamp



## Validation des variables d’environnement

La collection que vous avez importée contient tous les appels d’API nécessaires pour les exercices pratiques dans le camp d’amorçage.  Chaque Lab est organisé dans un dossier spécifique avec son propre ensemble de requêtes.

Vous trouverez ci-dessous des informations détaillées sur chaque dossier :

- **Profile &amp; Parcours Labs** : contient un ensemble de demandes d’envoi d’un événement web et d’un événement qui simule une confirmation d’expédition.
- **Decisioning Labs** : contient des requêtes pour 3 visiteurs qui imitent les appels des pages supérieure et inférieure qui se trouvent généralement sur un site AEP balisé avec SDK Web.

Pour vous assurer que l’environnement et la collection fonctionnent correctement ensemble, procédez comme suit.

1. Si nécessaire, cliquez sur **Collections** dans le rail de gauche, puis développez le dossier **Profile &amp; Parcours Labs**.
2. Cliquez sur la requête **Créer un événement web** et vous constatez que les variables d’environnement sont **rouges**

![Requête Postman affichant les variables d’environnement surlignées en rouge car aucun environnement n’est sélectionné](assets/import-api-collection-environment-variables-shown-red.png "Vérifiez que les variables d’environnement Postman sont rouges")

3. Cliquez sur le **menu déroulant Environnement** dans le coin supérieur droit et sélectionnez l’environnement **Bootcamp AJO**.

![Sélectionnez l’environnement Postman approprié](assets/import-api-collection-select-postman-environment.png)

4. Lorsque l’environnement approprié est sélectionné, la variable EDGE\_REGION prend désormais une couleur bleu clair. Cela indique que la variable possède désormais une valeur pour l’environnement sélectionné. La variable DATASTREAM\_CONFIG reste rouge, car vous n’avez pas encore créé le flux de données. Vous ne disposez donc pas encore d’une valeur pour cette variable d’environnement. Pointez sur EDGE\_REGION pour afficher la valeur de la valeur de l’environnement.

![La variable Postman EDGE_REGION est maintenant renseignée et n’est plus affichée en rouge. Vérifiez ](assets/import-api-collection-environment-works-with-collection.png " l’environnement Postman fonctionne avec la collection")

## Récapituler

Les fichiers d’environnement et de collection sont maintenant importés et vous savez comment les utiliser.
