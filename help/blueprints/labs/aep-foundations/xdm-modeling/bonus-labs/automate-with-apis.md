---
hold: true
title: Automatisation avec des API
description: Exécutez une collection Postman qui automatise la création de schémas, de groupes de champs, de descripteurs d’identité et de relation, ainsi que de jeux de données en une seule passe.
doc-type: article
solution: Experience Platform
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Automatisation avec des API

## Introduction

Pour découvrir comment automatiser les déploiements à l’aide d’API, vous exécutez un dossier d’API qui crée les objets suivants :

- Compte client et plan \[Recherche] schéma(s)
- Groupes de champs qui composent les schémas ci-dessus
- Descripteurs d’identité requis pour le profil
- Descripteurs de relation et de référence requis pour créer les relations entre le compte client et le plan \[Recherche]
- Deux jeux de données correspondant à chaque schéma créé



## Exécution du dossier

1. Dans Postman, accédez au dossier **Automatisation avec API** dans le dossier **XDM Schema Lab**

![Dossier Automatisation avec API dans le dossier XDM Schema Lab dans Postman](assets/automate-with-apis-postman-automation-folder.png)



1. Cliquez sur le dossier **Automatisation avec API** et dans l’espace de travail, cliquez sur le bouton **Exécuter**

>[!NOTE]
>
>Le bouton d’exécution se trouve en haut à droite de votre espace de travail Postman

![Bouton Exécuter en haut à droite de l’espace de travail Postman pour le dossier Automatisation avec les API](assets/automate-with-apis-click-folder-run-button.png "cliquez sur le dossier Exécuter")



1. Une nouvelle fenêtre doit s’afficher, qui affiche tous les appels API dans le dossier . Définissez le **Délai** sur **500 ms**, puis cliquez sur le bouton **Exécuter**.

![Boîte de dialogue Exécuter l’automatisation avec un délai défini sur 500 ms avant de cliquer sur Exécuter ](assets/automate-with-apis-execute-automation-dialog.png "’automatisation")



1. Les appels d’API commencent à s’exécuter dans l’ordre, et une fois terminés, vous devriez voir 32 tests réussis.

![Exécution réussie de l’automatisation avec 32 tests réussis](assets/automate-with-apis-successful-automation-32-passed-tests.png "Automatisation réussie")



1. Accédez à l’interface utilisateur d’Experience Platform pour afficher deux schémas et deux jeux de données créés et activés pour le profil avec le préfixe **postman:**

![Deux schémas créés et activés pour le profil avec Postman : prefix](assets/automate-with-apis-schemas-created-in-ui.png "Automation Schemas")



![Deux jeux de données créés avec Postman : préfixe correspondant aux schémas automatisés](assets/automate-with-apis-datasets-created-in-ui.png "Jeux de données d’automatisation")

> [!TIP]
>
>Félicitations !  Vous venez d’automatiser le déploiement des espaces de noms d’identité, des groupes de champs, des schémas, des descripteurs d’identité/de relation et d’activer un schéma pour le profil et de générer un jeu de données utilisant le schéma
