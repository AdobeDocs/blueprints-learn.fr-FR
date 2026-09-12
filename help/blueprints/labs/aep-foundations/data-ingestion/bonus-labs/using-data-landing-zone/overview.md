---
title: Utilisation de Data Landing Zone
description: Installez et configurez Azure Storage Explorer avec une URL SAS pour vous connecter à la zone d’atterrissage de données de Adobe Experience Platform.
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Utilisation de Data Landing Zone

## Conditions préalables

Si vous n’avez pas téléchargé l’explorateur de stockage Azure, faites-le maintenant, car c’est une exigence de cet atelier.  Vous trouverez le téléchargement sur le lien ci-dessous :

[Télécharger l’explorateur de stockage Azure](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. Installation de l’application
1. Lors du premier lancement, acceptez le contrat de licence de l’utilisateur final.

![Écran Contrat de licence de l’utilisateur final dans l’explorateur de stockage Azure](assets/overview-end-user-license-agreement-screen.png "écran Contrat de licence de l’utilisateur final")


## Configuration de l’explorateur de stockage Azure avec Experience Platform

1. Ouvrez l’Explorateur de stockage Azure et cliquez sur l’icône **Sélectionner la ressource** puis sélectionnez **Conteneur ou répertoire ADLS Gen 2**

   ![Sélection du conteneur ou répertoire ADLS Gen2 comme ressource dans l’explorateur de stockage Azure](assets/overview-choose-the-resource-as-shown-above.png)



1. Sélectionnez **URL de signature d’accès partagé (SAS)** puis cliquez sur **Suivant**

   ![Choix de l’option URL SAS comme mode de connexion](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "Choisissez l’option URL SAS comme mode de connexion")



1. Saisissez le nom d’affichage **Zone d’atterrissage des données**

   >[!NOTE]
   >
   >Vous ne pouvez pas continuer à cette étape tant que vous n’avez pas fourni l’URL SAS.  Vous obtenez cela à partir d’Experience Platform, que vous pouvez voir à l’étape suivante.

   ![Nommer la connexion Zone d’atterrissage des données](assets/overview-name-the-connection.png "Nommer la connexion")



1. Accédez à Adobe Experience Platform et effectuez les opérations suivantes pour accéder à la zone d’atterrissage des données :

   - Accédez à **Sources -> Catalogue**
   - Sélectionnez **Cloud Storage** sous les sources
   - Recherchez ensuite la carte **Data Landing Zone**
   - Cliquez sur la carte Data Landing Zone, puis sur **Afficher les informations d’identification** dans le rail de droite

   ![Carte source Data Landing Zone avec l’option Afficher les informations d’identification dans Adobe Experience Platform](assets/overview-data-landing-zone-view-credentials.png "Accéder à la carte Source Data Landing Zone dans Adobe Experience Platform")



1. Copiez le **SASUri** à partir de la boîte de dialogue modale qui s’affiche.

   Revenez à l’Explorateur de stockage Azure et collez la valeur **SASUri** dans le **Conteneur Blob ou URL du répertoire SAS** que vous avez laissé vide à l’étape précédente

   ![Copie de la valeur SASUri d’Experience Platform dans l’explorateur de stockage Azure](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "Copiez les informations d’identification d’URL SAS de Adobe Experience Platform et copiez-les dans l’explorateur de stockage Azure")



1. Cliquez sur **Suivant** pour continuer

   ![Copie des informations d’identification d’URL SAS dans la section URL SAS des informations de connexion](assets/overview-copy-sas-url-into-connection-info.png "Copiez les informations d’identification d’URL SAS dans la section URL SAS des informations de connexion")



1. Dans l’écran Résumé, cliquez sur **Connexion**

![Écran de résumé avec bouton Connexion](assets/overview-connect-screen.png "Écran de connexion")



Vous devriez maintenant voir un écran qui ressemble à ce qui suit

![Explorateur de stockage Azure affichant le compte Data Landing Zone correctement connecté](assets/overview-successfully-connected-account.png)

>[!TIP]
>
>Félicitations !  Vous avez correctement configuré l’explorateur de stockage Azure
