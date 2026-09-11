---
title: Configuration de Developer Console
description: Créez un projet Adobe Developer Console avec des informations d’identification de serveur à serveur OAuth pour les API Experience Platform et Journey Optimizer utilisées par l’interface de ligne de commande DEP.
doc-type: article
solution: Experience Platform
exl-id: 8b8f2a3e-2f4a-4b0e-9c5a-6e0c2b7a1d4f
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Configuration de Developer Console

>[!WARNING]
>
>Cela n&#39;est nécessaire que si vous travaillez dans les laboratoires à votre propre rythme. Si vous suivez un cours ou un événement de formation en direct, votre sandbox a déjà été déployé pour vous.

L’interface de ligne de commande DEP s’authentifie auprès de votre sandbox à l’aide des informations d’identification de serveur à serveur OAuth d’un projet Adobe Developer Console. Cette page décrit comment créer ce projet. Vous n’avez à le faire qu’une seule fois : les mêmes informations d’identification fonctionnent à la fois sur les pistes AEP Foundations et AJO Architectural Foundations, à condition d’ajouter les deux API décrites ci-dessous.

>[!NOTE]
>
>Si vous disposez déjà d’un projet Developer Console avec des informations d’identification pour Adobe Experience Platform (et, si nécessaire, Adobe Journey Optimizer), ignorez cette section et accédez directement à [ Instructions de déploiement ](deployment-instructions.md).

## Conditions préalables

- Une Adobe ID avec un accès développeur à votre organisation
- Un sandbox Adobe Experience Platform vide et de type `dev`
- Un rôle Adobe Experience Platform avec toutes les autorisations accordées pour ce sandbox (demandez à votre administrateur système si vous n’êtes pas sûr)

## Créer le projet

1. Accéder à [](https://developer.adobe.com/console) et se connecter
1. Si vous avez accès à plusieurs organisations, utilisez le sélecteur d’organisations en haut à droite pour sélectionner la bonne
1. Sélectionnez **Créer un projet**
1. Renommez le projet en quelque chose que vous reconnaîtrez ultérieurement (par exemple, `DEP Sandbox`).

## Ajout de l’API Experience Platform

1. Dans la présentation du projet, sélectionnez **Ajouter une API**
1. Sélectionnez l’icône du produit **** puis sélectionnez l’API **Adobe Experience Platform**
1. Sélectionnez **Suivant**
1. Choisissez **OAuth serveur à serveur** comme type d’authentification et sélectionnez **Suivant**
1. Attribuez un nom aux informations d’identification et sélectionnez **Suivant**
1. Sélectionnez le profil de produit correspondant au sandbox que vous utilisez, puis sélectionnez **Enregistrer l’API configurée**

## Ajout de l’API Adobe Journey Optimizer

1. Dans la présentation du projet, sélectionnez **Ajouter une API**
1. Sélectionnez l’icône de produit **** et sélectionnez l’API appropriée
1. Sélectionnez **OAuth serveur à serveur**
1. Sélectionnez le même profil de produit et sélectionnez **Enregistrer l’API configurée**

>[!NOTE]
>
>Réutilisez les informations d’identification créées ci-dessus au lieu d’en créer une nouvelle. L’interface de ligne de commande n’a besoin que d’un seul jeu d’informations d’identification avec des portées combinées.



## Collecter vos valeurs

Ouvrez la page d’aperçu **OAuth de serveur à serveur** de vos informations d’identification. Vous aurez besoin de quatre valeurs pour le fichier d’environnement de l’interface en ligne de commande :

| **Valeur de la console de développement** | **Champ du fichier d’environnement** |
| --------------------- | ------------------------------- |
| Identifiant client | `API_KEY` |
| Secret client | `CLIENT_SECRET` |
| Identifiant de l’organisation | `IMS_ORG` (se termine par `@AdobeOrg`) |
| Portées | `SCOPES` |

>[!NOTE]
>
>Copiez les étendues par défaut affichées sur la page des informations d’identification — vous n’avez pas besoin d’ajouter quoi que ce soit manuellement. Si vous avez ajouté les deux API ci-dessus, la liste des portées les inclut automatiquement.

Gardez cette page ouverte ou copiez ces quatre valeurs en lieu sûr. Vous les collez dans le fichier d’environnement de l’interface en ligne de commande à l’étape suivante du guide de configuration de votre suivi.
