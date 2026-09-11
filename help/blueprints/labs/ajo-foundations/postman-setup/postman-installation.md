---
hold: true
title: Installation de Postman
description: Installez Postman et familiarisez-vous avec ses collections, environnements et interface d’espace de travail avant d’effectuer des appels API dans les ateliers ultérieurs.
doc-type: article
solution: Experience Platform
exl-id: c277edb5-f758-4955-bcd7-b15a9b9ab949
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Installation de Postman

## Objectif

À l’issue de cet atelier, vous serez en mesure d’installer Postman, de configurer un espace de travail et un environnement de base afin de pouvoir effectuer les appels d’api suivants dont les prochains ateliers auront besoin.

&#x200B;> [!IMPORTANT]
>
>Postman est nécessaire pour divers laboratoires de ce cours.  Même si vous avez déjà installé Postman, vous devrez terminer cet atelier pour vous assurer que les fichiers d’environnement et la collection d’API sont installés et correctement configurés.



## Installation de Postman

Accédez au site web Postman et téléchargez l’application Postman ou utilisez la version web —> [https://www.postman.com/download/](https://www.postman.com/download/)

Page de téléchargement de ![Postman sur le site web de Postman](assets/postman-installation-postman-download.png)

## Création d’un espace de travail Postman (facultatif)

Si vous découvrez Postman *et qu’il s’agit de votre première installation, vous n’avez pas besoin de créer un espace de travail.* Lors du premier lancement, choisissez de continuer sans vous connecter et vous utilisez le client léger qui ne nécessite pas d’espace de travail.

Si vous *connaissez déjà Postman* et que vous l’avez installé, alors il est probable que vous soyez déjà connecté et que vous disposiez de plusieurs espaces de travail. Si c’est le cas, nous vous recommandons de créer un nouvel espace de travail pour *ce bootcamp*. Vous trouverez des instructions sur le site Web de [Postman.](https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/create-workspaces/)

## Interface de Postman

Ouvrez Postman et familiarisez-vous rapidement avec quelques zones de l’application. Dans le cadre de notre collaboration avec Experience Platform, il nous suffit de nous concentrer sur quelques aspects essentiels de l’application.

![Présentation de l’interface de Postman avec la barre latérale, l’en-tête et la zone de travail principale intitulée](assets/postman-installation-interface-overview.png "Interface de Postman")

## Barre latérale

La barre latérale vous permet de naviguer rapidement entre les différents éléments de Postman. Pendant les ateliers, vous n&#39;utiliserez que les deux éléments ci-dessous :

**Collections** - groupes de requêtes enregistrées qui peuvent être importées à partir d’un emplacement externe ou créées par vous-même.

**Environnements** : ensemble de variables que vous pouvez référencer dans vos requêtes Postman. Dans Experience Platform, vous pouvez considérer les environnements Postman comme synonymes de sandbox Adobe au sein d’une organisation IMS. Nous utiliserons la fonction Environnement dans Postman



## En-tête

Espaces de travail : permettent d&#39;organiser votre travail en différents regroupements (c&#39;est-à-dire projets, équipes, etc.)



## Espace de travail principal

La zone de travail principale est l’endroit où vous exécuterez la majorité de votre travail lorsque vous travaillerez dans Postman. Toutes les requêtes d’API sont exposées dans un onglet spécifique de l’espace de travail principal.

**Barre latérale droite** - fournit un accès supplémentaire aux outils en fonction de l’onglet actuel sélectionné. Il s’agit par exemple de la documentation de la requête, des commentaires et des fragments de code, pour ne citer que quelques fonctionnalités.

**Sélecteur d’environnement** : permet de basculer rapidement entre différents environnements pour accéder à des variables préconfigurées lors de l’utilisation d’API. Lorsque vous travaillez avec Experience Platform, vous exploiterez cette fonctionnalité lors de l’utilisation d’un sandbox AEP spécifique au sein de l’organisation IMS qui vous est attribuée.



## Pied de page

Tout au bas de l’application Postman, vous trouverez un ensemble de fonctions qui vous permettent d’afficher rapidement les journaux des appels que vous avez passés, un accès rapide à la recherche et au remplacement, ainsi que diverses autres fonctions.



## Récapituler

Postman doit maintenant être installé et vous connaissez certains principes de base de l’interface utilisateur
