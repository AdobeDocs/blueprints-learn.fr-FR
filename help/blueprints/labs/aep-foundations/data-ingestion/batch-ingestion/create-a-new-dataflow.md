---
title: Créer un flux de données
description: Créez un flux de données source par lot par rapport à un jeu de données existant et importez les mappages d’un flux de données précédent pour accélérer la configuration.
doc-type: article
solution: Experience Platform
exl-id: 6f26f742-27e8-445a-8005-21d4e59dc3d0
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Créer un flux de données

## Accéder aux sources

1. Dans l’interface utilisateur de Adobe Experience Platform, accédez à l’emplacement suivant :\
   **Sources** -> **Catalogue** -> **Système local**
1. Cliquez ensuite sur le bouton **Ajouter des données** pour la carte **Chargement de fichier local**

![Bouton Ajouter des données pour la carte Chargement de fichier local dans le catalogue des sources](assets/create-a-new-dataflow-local-file-upload-add-data.png "Accès à la zone d’atterrissage de données")



## Configurer le flux de données

1. Dans l’écran Détails du flux de données , choisissez **Jeu de données existant**.
1. Utilisez le jeu de données que vous avez créé précédemment avec le nom **Compte client - \&lt;Vos initiales>**
1. Assurez-vous que le bouton (bascule) **Jeu de données de profil** est activé.
(Si vous n’activez pas cette option, le magasin de profils ne pourra pas surveiller les nouvelles données qui entrent dans ce jeu de données et n’ingérera donc pas ces données dans le profil)
1. Assurez-vous que le bouton (bascule) **Activer l’ingestion partielle** est activé
(Si vous ne l’activez pas, l’ingestion entière peut échouer si un seul des enregistrements comporte une erreur)
1. Définissez le nom du flux de données sur **Lot de comptes client v2 - \&lt;Vos initiales>**
1. Activer toutes les alertes **Début/Succès/Échec du flux de données des sources**
1. Si tout semble correct, cliquez sur le bouton **Suivant** dans le coin supérieur droit de l’écran pour passer à l’étape suivante.

![Écran Détails du flux de données configuré avec le jeu de données existant pour les deuxièmes détails du flux ](assets/create-a-new-dataflow-existing-dataset-flow-details.png " données")



## Charger l’exemple de fichier

1. Faites glisser et déposez le fichier **Lab\_Customer\_Account.csv** et/ou chargez-le dans l’interface utilisateur.  Lorsque vous avez terminé, l’écran doit ressembler à ce qui suit.

![Aperçu du fichier CSV de compte client chargé pour le deuxième flux de données](assets/create-a-new-dataflow-uploaded-csv-preview.png "Accès aux fichiers de l’explorateur de stockage Azure dans Adobe Experience Platform")



## Importer les mappages

Sur l’écran de mappage, au lieu de configurer à nouveau tous vos mappages, vous pouvez importer ceux que vous avez créés précédemment.

1. Cliquez sur le bouton **Importer le mappage**
1. Sélectionnez le flux de données avec le mappage que vous avez précédemment créé



![Bouton Importer le mappage sur l’écran ](assets/create-a-new-dataflow-import-mapping-button.png " mappage")



![Boîte de dialogue permettant de sélectionner le flux de données à partir duquel importer le mappage](assets/create-a-new-dataflow-select-dataflow-to-import-mapping-from.png "Sélectionnez le flux de données à partir duquel importer le mappage")

>[!NOTE]
>
>L’importation de mappages est un moyen pratique de réutiliser des mappages d’autres flux de données et de réduire la quantité de travail de mappage que vous devez effectuer
