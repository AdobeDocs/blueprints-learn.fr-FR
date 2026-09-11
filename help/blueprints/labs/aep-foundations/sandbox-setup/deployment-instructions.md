---
hold: true
title: Instructions de déploiement
description: Utilisez l’interface de ligne de commande DEP pour déployer les schémas, les jeux de données, les flux de données et les exemples de données de profil du pack AEP Foundations dans votre sandbox.
doc-type: article
solution: Experience Platform
exl-id: 9f2b6d4a-8e1c-4b7a-a3d5-6c9f0e2a4b8d
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 1%

---


# Instructions de déploiement

&#x200B;> [!NOTE]
>
>Cela n&#39;est nécessaire que si vous travaillez dans les laboratoires à votre propre rythme. Si vous suivez un cours ou un événement de formation en direct, votre sandbox a déjà été déployé pour vous.

Le pack de démonstration AEP Foundations est déployé sur votre sandbox à l’aide de l’interface de ligne de commande DEP, un outil de ligne de commande qui crée les schémas, les jeux de données, les flux de données et les exemples de données que vous utiliserez dans les ateliers.

## Éléments déployés

- 4 espaces de noms d’identité
- 1 classe de schéma, 13 groupes de champs, 10 schémas
- 12 descripteurs d’identité, 6 descripteurs de relation/référence, 3 descripteurs de noms conviviaux
- 10 jeux de données de catalogue
- 1 connexion source API HTTP et 10 flux de données
- Données de profil : un profil en mode Proche unique (3 jeux de données de caractéristiques, 7 jeux de données d’événement) plus 3 jeux de données de recherche
- 2 politiques de fusion de profil et 1 audience (tous les événements en flux continu, dans l’heure)

>[!NOTE]
>
>Le déploiement de bout en bout prend environ 2 heures 24 minutes, dont la plupart sont des temps d’attente sans surveillance entre les étapes. L’interface de ligne de commande applique automatiquement ces attentes, vous n’avez donc pas besoin de programmer quoi que ce soit vous-même.

## Conditions préalables

- **Droits de licence.** Privilèges d’administration pour une organisation IMS avec Real-Time CDP (avec segmentation en flux continu)
- **Droits d’accès.** Un rôle Adobe Experience Platform avec toutes les autorisations sur le sandbox cible, y compris les informations d’identification d’API que vous avez créées à partir de la configuration de [Developer Console](developer-console-setup.md).
- **Informations d’identification Developer Console.** Un projet qui comprend des API Adobe Experience Platform. Si vous ne les avez pas encore, suivez d’abord la configuration de [&#128279;](developer-console-setup.md)
- **Sandbox.** Vide, de type `dev` et à l’état « Prêt » pendant au moins 60 minutes avant le démarrage du déploiement
- **Node.js.** Toute version récente de LTS, sous Windows ou Mac

## &#x200B;1. Installation de l’interface de ligne de commande

1. Clonez ou téléchargez le référentiel [dep-cli](https://github.com/adobe/dep-cli)
1. Dans le répertoire `dep-cli`, exécutez `npm install`
1. Démarrer l’interface de ligne de commande avec `npm start`

>[!NOTE]
>
>Node.js est requis avant d’exécuter les commandes ci-dessus. Si vous n’avez pas encore installé Node.js, commencez par consulter la page [Configuration de Node.js](https://github.com/adobe/dep-cli/wiki/Nodejs-Setup) du wiki. Pour plus d’informations sur l’installation, notamment des captures d’écran et la mise à jour d’une installation existante, consultez la page [Installation](https://github.com/adobe/dep-cli/wiki/Installation)wiki

## &#x200B;2. Configurer votre fichier d’environnement

L’interface de ligne de commande déploie sur le sandbox vers lequel pointe votre fichier d’environnement. Par conséquent, cette configuration doit être correcte avant toute exécution.

1. Copiez `envFiles/sample-env.json` et donnez-lui un nouveau nom, par exemple `my-env.json`
2. Ouvrez le fichier et renseignez les champs suivants à l&#39;aide des valeurs de la configuration de [Developer Console &#x200B;](developer-console-setup.md) :

| **Champ** | **Valeur** |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `API_KEY` | Identifiant client |
| `CLIENT_SECRET` | Secret client |
| `IMS_ORG` | Identifiant de l’organisation |
| `SCOPES` | Doit inclure les portées d’API Experience Platform (openid, session, AdobeID, read_organisations, additional_info.expectedProductContext) |
| `SANDBOX_NAME` | Le sandbox que vous ciblez doit être vide et de type `dev` |

&#x200B;3. Enregistrer et fermer le fichier

>[!NOTE]
>
>Le nom de ce fichier vous est demandé chaque fois que vous exécutez une commande d’interface de ligne de commande, afin que vous puissiez le réutiliser à chaque étape ci-dessous.

## &#x200B;3. Exécuter le menu de base d’AEP

Dans le menu principal, sélectionnez **Fondations**. Il y a trois étapes, et elles doivent être exécutées dans l&#39;ordre.

>[!WARNING]
>
>Le sandbox doit avoir été à l’état « Prêt » pendant au moins 60 minutes avant l’exécution de l’étape 1.

| **Étape** | **À quoi cela sert-il** | **Avant de l’exécuter** |
| ----------------------- | ------------------------------------------------------------------------------------------ | ------------------------------- |
| &#x200B;1. Créer une base de profils | Déploie des espaces de noms d’identité, des schémas, des jeux de données, des politiques de fusion et des audiences | Sandbox « Prêt » pendant plus de 60 minutes |
| &#x200B;2. Charger les données de profil | Crée des flux de données et diffuse des données de profil et de recherche | Patientez plus de 60 minutes après l’étape 1. |
| &#x200B;3. Vérifier l’intégrité du profil | Vérifie que toutes les données ont été chargées correctement | Patientez 15+ minutes après l’étape 2 |

L’étape 1 prend environ 2 minutes pour s’exécuter, l’étape 2 environ 6 minutes et l’étape 3 est une validation rapide sans attente. Les intervalles de 60 et 15 minutes entre les étapes permettent à AEP de terminer la propagation des données en arrière-plan, ce qui représente la majeure partie de votre chronologie de 2 heures.

&#x200B;> [!NOTE]
>
>L’interface de ligne de commande vérifie automatiquement ces temps d’attente. Si vous exécutez une étape trop tôt, elle bloque et vous indique combien de minutes il reste - vous n&#39;avez pas besoin de suivre l&#39;horloge vous-même.

>[!NOTE]
>
>L’étape 2 peut être exécutée à nouveau en cas de problème. Il remplace les enregistrements de caractéristiques existants et ignore les événements en double.

## Dépannage

>[!WARNING]
>
>**La vérification d’intégrité échoue avec des événements manquants**. Certaines données de profil n’ont pas encore fini de se propager. Patientez encore 15 minutes et réexécutez la fonction Vérifier l’intégrité du profil. Si l’opération échoue toujours, exécutez à nouveau Charger les données de profil, patientez 15 minutes, puis vérifiez à nouveau.

**Un autre problème apparaît.** En dernier recours, vous pouvez réinitialiser le sandbox à partir du menu Gestion des sandbox de l’interface de ligne de commande et le redéployer à partir de l’étape 1.

>[!CAUTION]
>
>La réinitialisation d’un sandbox est destructive. L’interface de ligne de commande vous demande de saisir le nom du sandbox à confirmer avant de continuer.
