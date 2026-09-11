---
title: Configurer la source
description: Chargez un fichier JSON d’historiques de commandes dans la zone d’atterrissage de données et configurez un nouveau flux de données ciblant le schéma Commandes .
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Configurer la source

## Charger l’exemple de fichier

Vous devez charger un exemple de fichier de données dans votre zone d’atterrissage de données via l’explorateur de stockage Azure afin de pouvoir l’utiliser pendant le Lab.  Pour ce faire, procédez comme suit :

1. Téléchargez l’[exemple de fichiers](../../../sample-files.md)
1. Faites glisser et déposez le fichier **Lab\_Historical\_Orders.json** et/ou chargez-le dans la zone d’atterrissage de données que vous avez enregistrée ci-dessus.



Une fois votre écran chargé, il doit ressembler à la capture d’écran ci-dessous.

Fichier ![Lab_Historical_Orders.json chargé dans Data Landing Zone](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "Lab_Historical_Orders.json chargé dans DLZ")

## Accéder aux sources

1. Accédez à Adobe Experience Platform et à : **Sources** -> **Catalogue** -> **Espace de stockage**
1. Cliquez sur **Configuration** / **Ajouter des données** pour la zone d’atterrissage de données

![Accédez à Sources > Catalogue > Espace de stockage pour configurer la zone d’atterrissage de données](assets/setup-source-navigate-to-data-landing-zone-source.png "Sources - Zone d’atterrissage de données")

>[!NOTE]
>
>L’action **Ajouter des données** s’affiche par défaut si vous avez déjà configuré une connexion à partir de l’atelier d’ingestion par lots précédent



## Prévisualiser le fichier

1. Sélectionnez le fichier **Lab\_Historical\_Orders.json** et prévisualisez son contenu
1. Cliquez sur **Suivant** dans le coin supérieur droit de l’écran pour passer à l’étape suivante

![Sélection et prévisualisation du contenu du fichier Lab_Historical_Orders.json](assets/setup-source-select-and-preview-lab-historical-orders.png "Sélection et prévisualisation du fichier Lab_Historical_Orders.json")

## Configurer le flux de données

1. Dans l’écran Détails du flux de données , choisissez **Nouveau jeu de données**
1. Nommez le jeu de données de sortie **Commandes - VotreNomIci**
1. Sélectionnez le nom du schéma **dep : Commandes**
1. Activez la case à cocher **Jeu de données de profil**
(Si vous ne l’activez pas, la banque de profils ne pourra pas surveiller les nouvelles données qui entrent dans ce jeu de données et, par conséquent, n’ingérera pas ces données dans le profil)
1. Activez l’option **Activer l’ingestion partielle**
(Si vous ne l’activez pas, l’ingestion peut échouer si l’un des enregistrements comporte des erreurs)
1. Définissez le nom du flux de données sur **Commandes - Renvoi - VotreNomIci**
1. Activer toutes les alertes **Début/Succès/Échec du flux de données des sources**

![Écran Détails du flux de données configuré pour le jeu de données Commandes](assets/setup-source-dataflow-details-for-orders.png "Détails du flux de données pour les commandes")

>[!CAUTION]
>
>Assurez-vous que vous avez **activé** votre jeu de données pour l’ingestion de profil et partielle.

Cliquez sur **Suivant** dans le coin supérieur droit de l’écran pour passer à l’étape suivante
