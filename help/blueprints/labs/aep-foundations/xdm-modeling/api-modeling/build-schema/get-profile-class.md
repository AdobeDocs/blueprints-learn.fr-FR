---
hold: true
title: Get Profile Class
description: Appelez l’API Global Schema Registry pour récupérer et enregistrer le $id de la classe XDM Individual Profile en vue de l’utiliser dans un schéma personnalisé.
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Get Profile Class

## Exécutez l’étape 3 - Obtenir la classe de profil

1. Cliquez sur la demande de `Step 3 - Get Profile Class` dans le dossier `XDM API Lab -> Create Schema`
1. Exécuter en cliquant sur le bouton `Send`

![Étape 3 - Requête de l’API Get Profile Class](assets/get-profile-class-step-3-api-request.jpeg "Étape 3 - Requête de l’API Get Profile Class")

>[!NOTE]
>
>Notez que dans la requête GET, le chemin d’accès `global` : .../schemaregistry/**global**/classes. N’oubliez pas que l’utilisation de `global` indique au registre des schémas que nous voulons uniquement renvoyer les objets XDM standard d’Adobe


## Recherchez et enregistrez la classe $id

Après avoir exécuté la requête d’API, effectuez les étapes suivantes pour localiser et enregistrer le `$id` pour la classe XDM Individual Profile.

1. Recherchez la classe `XDM Individual Profile` dans la réponse
1. Copiez le `$id` de la classe `XDM Individual Profile` et enregistrez-le à un emplacement auquel vous pourrez faire référence ultérieurement.

![Classe XDM Individual Profile située dans la réponse de l’API](assets/get-profile-class-xdm-individual-profile-class.png "Classe XDM Individual Profile")

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré le `$id` quelque part.  Elle sera nécessaire ultérieurement pour créer le schéma Compte client
