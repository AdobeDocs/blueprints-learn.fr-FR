---
title: Fichier d’environnement
description: Importez le fichier d’environnement Postman et renseignez son projet de développement et ses variables sandbox nécessaires aux appels API du bootcamp.
doc-type: article
solution: Experience Platform
exl-id: 1461fac5-0714-44d4-b5c8-949df6bcff83
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%
---

# Fichier d’environnement

## Fichier d’environnement Postman

Télécharger le fichier — [AEP Bootcamp.postman_environment.json](assets/aep-bootcamp.postman_environment.json)



## Importer le fichier d’environnement

1. Ouvrez le `Environment File` ci-dessus dans votre navigateur en cliquant sur le fichier .
1. Copiez l’URL du fichier dans le presse-papiers
1. Lancez Postman sur votre ordinateur local et cliquez sur le bouton `Import` dans votre espace de travail
1. Collez l’URL du `Environment File` dans la zone de texte modale d’importation sur le recouvrement.  Cette action déclenche une importation automatique

![Cliquer sur le bouton Importer dans l’espace de travail Postman pour importer le fichier d’environnement](assets/environment-file-click-import-button.png "Bouton Importer")



![Collage de l’URL du fichier d’environnement dans la zone de texte modale d’importation Postman](assets/environment-file-import-modal-paste-url.png "Superposition du bouton d’importation")



Une fois le fichier importé, vérifiez s’il existe déjà, puis cliquez sur l’onglet `Environments` dans la barre latérale gauche.  Quelque chose de similaire s’affiche ci-dessous.

![Environnement de bootcamp AEP répertorié sous l’onglet Environnements Postman après l’importation](assets/environment-file-aep-bootcamp-environment-listed.png "Environnement de bootcamp AEP")



## Variables d’environnement

Avant d’effectuer des appels d’API, vous devez mettre à jour certaines des variables du fichier d’environnement que vous venez d’importer.  Ces variables sont référencées dans les appels API afin de s’assurer qu’elles sont correctement renseignées.  Les variables sont divisées en deux groupes :

- **Valeurs du projet du développeur** -> il s’agit des variables par défaut générées à partir du projet du développeur qui ont été créé dans le Adobe Developer Console
- **Autres valeurs** -> il s’agit de variables personnalisées, généralement créées par un utilisateur pour fonctionner avec les différentes API d’Experience Platform

>[!NOTE]
>
>Ces valeurs proviennent des informations d’identification de serveur à serveur OAuth que vous avez créées dans la configuration de [&#128279;](../sandbox-setup/developer-console-setup.md#collect-your-values)



### Mise à jour des valeurs des projets de développement

1. Cliquez sur l’onglet `Environments` dans la barre latérale gauche de Postman
1. Cliquez ensuite sur le fichier d’environnement `AEP Bootcamp`
1. Mettez à jour le `current values` pour les variables répertoriées ci-dessous :
   - CLIENT\_SECRET
   - CLIENT\_ID (également appelé CLÉ API)
   - TECHNICAL\_ACCOUNT\_ID
   - IMS\_ORG

Une fois cette opération terminée, votre fichier d’environnement doit ressembler à cette image :

![Fichier d’environnement après la mise à jour de CLIENT_SECRET, CLIENT_ID, TECHNICAL_ACCOUNT_ID et IMS_ORG values](assets/environment-file-with-developer-project-values.png "Environment File avec les valeurs du projet de développement")

### Mettre à jour d’autres valeurs

Les seules autres valeurs qui doivent être mises à jour sont la variable `SANDBOX_NAME` et la variable `TENANT_NAME`.

- `SANDBOX_NAME` : indique à Adobe Experience Platform le sandbox à exécuter.
- `TENANT_NAME` : utilisé pour préremplir le nom du client dans des appels XDM spécifiques

>[!NOTE]
>
>Si vous travaillez dans ces laboratoires de manière indépendante plutôt que lors d’un événement de formation en direct avec un fichier sandbox-assignment.pdf, recherchez les deux valeurs lorsque vous êtes connecté à votre sandbox à partir de l’URL de l’interface utilisateur de Adobe Experience Platform. Par exemple :
>
>`https://experience.adobe.com/#/@dep/sname:prod/platform/home`
>
>- `SANDBOX_NAME` est la valeur après `sname:` — dans cet exemple, `prod`
>- `TENANT_NAME` est la valeur suivant le symbole `@`, précédé d’un trait de soulignement ; dans cet exemple, `_dep`

1. Mettez à jour le `current values` pour les variables répertoriées ci-dessous :
   - SANDBOX\_NAME
   - TENANT\_NAME
1. Enregistrez vos mises à jour en cliquant sur le bouton `Save` en haut à droite de l’espace de travail de l’environnement

Lorsque vous avez terminé, votre fichier d’environnement doit se présenter comme suit :

![Fichier d’environnement après la mise à jour des valeurs SANDBOX_NAME et TENANT_NAME](assets/environment-file-with-sandbox-name-and-tenant-name.png "Fichier d’environnement avec SANDBOX_NAME")

>[!SUCCESS]
>
>Félicitations ! Vous avez terminé la configuration de l’environnement Postman
