---
title: Instructions de déploiement
description: Utilisez l’interface de ligne de commande DEP pour déployer les schémas, les jeux de données, les flux de données et les données d’exemple du pack AJO Architectural Foundations dans votre sandbox.
doc-type: article
solution: Experience Platform
exl-id: 3d6e9a1c-7b2f-4e8a-9d0c-1f5a8b6c2e3d
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 1%

---


# Instructions de déploiement

>[!WARNING]
>
>Cela n&#39;est nécessaire que si vous travaillez dans les laboratoires à votre propre rythme. Si vous suivez un cours ou un événement de formation en direct, votre sandbox a déjà été déployé pour vous.

Le pack de démonstration AJO Architectural Foundations est déployé sur votre sandbox à l’aide de l’interface de ligne de commande DEP, un outil de ligne de commande qui crée les schémas, les jeux de données, les flux de données et les exemples de données que vous utiliserez dans les ateliers (couvrant à la fois le magasin de profils et le magasin relationnel AJO utilisés pour les campagnes orchestrées).

## Éléments déployés

**Suivi du profil**

- Espaces de noms d’identité (customerID, planID, productID)
- Groupes de champs, descripteurs et schémas XDM standard activés pour le profil
- Jeux de données de catalogue activés pour le profil
- Fusionner les politiques et les audiences
- Données de profil pour trois échantillons de jeux de données : mode de vérification (caractéristiques + événements), éléments étrangers (caractéristiques) et prise de décision (caractéristiques)

**Suivi relationnel**

- Espace de noms d’identité customerID
- 11 schémas XDM relationnels avec clé primaire, clé étrangère et descripteurs de version
- 11 jeux de données activés pour les campagnes orchestrées par AJO
- 11 flux de données chargeant des données à partir de la zone d’atterrissage des données

>[!NOTE]
>
>Le déploiement de bout en bout prend environ 2 heures 23 minutes. Les pistes de profil et relationnelles s’exécutent en parallèle et la plupart du temps, il s’agit d’un temps d’attente sans assistance que l’interface de ligne de commande applique automatiquement.

## Conditions préalables

- **Droits de licence.** Privilèges d’administration pour une organisation IMS avec Real-Time CDP (avec segmentation en flux continu) et Adobe Journey Optimizer (avec campagnes orchestrées)
- **Droits d’accès.** Un rôle Experience Platform avec toutes les autorisations sur le sandbox cible, y compris les informations d’identification d’API que vous avez créées à partir de la configuration de [Developer Console](developer-console-setup.md).
- **Informations d’identification Developer Console.** Un projet qui inclut les API Adobe Experience Platform et Adobe Journey Optimizer. Si vous ne disposez pas de ces éléments, commencez par suivre la configuration de [](developer-console-setup.md)
- **Sandbox.** Vide, de type `dev` et à l’état « Prêt » pendant au moins 120 minutes avant le démarrage du déploiement
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
2. Ouvrez le fichier et renseignez les champs suivants à l’aide des valeurs de la configuration de [Developer Console ](developer-console-setup.md) :

   | **Champ** | **Valeur** |
   | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `API_KEY` | Identifiant client |
   | `CLIENT_SECRET` | Secret client |
   | `IMS_ORG` | Identifiant de l’organisation |
   | `SCOPES` | Doit inclure à la fois les portées de l’API Experience Platform et de l’API Adobe Journey Optimizer <br />*(par exemple, cjm.suppression\_service.client.delete, cjm.suppression\_service.client.all, openid, session, AdobeID, read\_organization, additional\_info.expectedProductContext)* |
   | `SANDBOX_NAME` | Le sandbox que vous ciblez doit être vide et de type `dev` |

3. Enregistrer et fermer le fichier

>[!NOTE]
>
>Le nom de ce fichier vous est demandé chaque fois que vous exécutez une commande d’interface de ligne de commande, afin que vous puissiez le réutiliser à chaque étape ci-dessous.

## &#x200B;3. Exécution du menu AJO Architectural Foundations

Dans le menu principal, sélectionnez **AJO arch foundation**. Il y a six étapes réparties sur deux pistes.

### Suivi du profil (exécution dans l’ordre)

>[!WARNING]
>
>Le sandbox doit avoir été à l’état « Prêt » pendant au moins 60 minutes avant l’exécution de l’étape 1.

| **Étape** | **À quoi cela sert-il** | **Avant de l’exécuter** |
| ------------------------ | ------------------------------------------------------------------------------------------- | ---------------------------------- |
| &#x200B;1. Créer une base de profils | Déploie des espaces de noms d’identité, des schémas, des jeux de données, des politiques de fusion et des audiences | Sandbox « Prêt » pendant plus de 60 minutes |
| &#x200B;2. Charger les données de profil | Crée des flux et des flux de données pour le mode Dépression, les éléments étrangers et les données de profil Decisioning | Patientez plus de 60 minutes après l’étape 1. |
| &#x200B;3. Vérifier l’intégrité du profil | Vérifie que toutes les données de profil sont correctement chargées | Patientez 15+ minutes après l’étape 2 |

L’étape 1 prend environ 2 minutes, l’étape 2 environ 6 minutes.

>[!NOTE]
>
>L’étape 2 peut être réexécutée en toute sécurité en cas d’échec : elle remplace les caractéristiques existantes et ignore les événements en double.

### Suivi relationnel

>[!WARNING]
>
>Le sandbox doit avoir été à l’état « Prêt » pendant au moins 120 minutes avant l’exécution des étapes 4 ou 6.

| **Étape** | **À quoi cela sert-il** | **Avant de l’exécuter** |
| ----------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| &#x200B;4. Créer une base relationnelle | Crée l&#39;espace de noms customerID et les schémas/descripteurs/jeux de données relationnels | Sandbox « Prêt » pendant plus de 120 minutes |
| &#x200B;5. Chargement des données relationnelles | Charge 11 fichiers CSV et crée les flux de données qui les chargent | S&#39;exécute juste après l&#39;étape 4 — aucune attente manuelle nécessaire |
| &#x200B;6. Déployer la base relationnelle et les données | Combine les étapes 4 et 5 en une seule exécution de ~5 minutes | Sandbox « Prêt » pendant plus de 120 minutes |

>[!NOTE]
>
>Utilisez l’étape 6 au lieu d’exécuter les étapes 4 et 5 séparément ; elle effectue la même chose en une seule passe avec l’attente de propagation gérée pour vous.

>[!NOTE]
>
>Tous les temps d’attente ci-dessus sont vérifiés automatiquement par l’interface de ligne de commande. Si vous exécutez une étape trop tôt, elle se bloque et vous indique combien de temps d’attente.

## Dépannage

>[!WARNING]
>
>**La vérification de l’intégrité du profil échoue avec des événements manquants.** Certaines données de profil n’ont pas encore fini de se propager. Patientez encore 15 minutes et réexécutez la fonction Vérifier l’intégrité du profil. Si l’opération échoue toujours, exécutez à nouveau Charger les données de profil, patientez 15 minutes, puis vérifiez à nouveau.

>[!WARNING]
>
>**Le chargement des données relationnelles échoue en cours de route.** Chaque appel API fait l’objet de 3 reprises maximum. S’il échoue toujours, le nettoyage supprime les connexions source, les connexions cible et les flux de données qu’il a créés afin que vous puissiez réexécuter proprement l’étape 5 (ou l’étape 6). Les jeux de mappages ne peuvent pas être supprimés via l’API et peuvent être laissés pour compte, ce qui n’affecte pas le redéploiement.

**Un autre problème apparaît.** En dernier recours, vous pouvez réinitialiser le sandbox à partir du menu Gestion des sandbox de l’interface de ligne de commande et le redéployer à partir de l’étape 1.

>[!CAUTION]
>
>La réinitialisation d’un sandbox est destructive. L’interface de ligne de commande vous demande de saisir le nom du sandbox à confirmer avant de continuer.
