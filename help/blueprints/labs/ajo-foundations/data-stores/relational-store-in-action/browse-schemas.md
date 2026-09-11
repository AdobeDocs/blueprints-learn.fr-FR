---
hold: true
title: Parcourir les schémas
description: Découvrez comment parcourir les schémas relationnels et afficher les diagrammes de relation d’entité dans Adobe Experience Platform pour comprendre les relations de schéma utilisées dans les campagnes.
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# Parcourir les schémas

## Objectif

Dans les étapes suivantes, vous allez parcourir l’interface utilisateur pour afficher les schémas et leurs relations.  Il est important de se familiariser avec les schémas et les relations disponibles lorsque vous créez votre campagne.

## Affichage des schémas

Le modèle de données relationnelles Connection 5G a déjà été créé pour vous. Vous pouvez afficher les schémas vous-même en accédant à la page **Schémas -> Parcourir** dans l’interface utilisateur.

Dans la zone de recherche, saisissez `dep-rel` pour afficher tous les schémas.

![Résultats de la recherche affichant tous les schémas relationnels profonds](assets/browse-schemas-search-results.png)

>[!NOTE]
>
>Notez que le type de tous les schémas est *Relationnel*



## Afficher le diagramme de relation

Avec les schémas XDM relationnels, vous pouvez facilement afficher le diagramme de relation d’entité (ERD) en sélectionnant n’importe quel schéma et en cliquant sur le bouton Afficher le diagramme de relation .

Procédez comme suit :

1. Cliquez sur l’onglet **Relations**, puis sur le bouton **Afficher le diagramme de relation**

![Onglet Relations avec le bouton Afficher le diagramme de relation](assets/browse-schemas-relationships-tab.png)



&#x200B;2. Cliquez sur **Sélectionner des schémas**
&#x200B;3. Dans la fenêtre contextuelle, sélectionnez `dep-rel: Customer Account`, puis cliquez sur **Confirmer**

![Fenêtre contextuelle Sélectionner les schémas avec dep-rel : compte client choisi](assets/browse-schemas-select-schema-popup.png)



&#x200B;4. Sur l’ERD, cliquez sur les points **3** et sélectionnez **Afficher les entités associées**

![Option Afficher les entités associées dans le menu contextuel ERD](assets/browse-schemas-show-related-entities.png)



&#x200B;5. Affichez l’ERD avec toutes les tables directement liées à Deep-rel : Customer Account. Vous pouvez éventuellement télécharger l’ERD sous la forme d’un fichier PNG.

![Diagramme de relation d’entité présentant les tables liées au compte client](assets/browse-schemas-erd-diagram.png)

>[!TIP]
>
>Plutôt cool hein ?!

## Récapituler

Vous avez maintenant vu à quel point il est facile de naviguer dans l’interface utilisateur Schéma et relations .  Vous pouvez sélectionner un ou plusieurs schémas spécifiques et accéder aux relations pour faciliter la compréhension et l’utilisation des données dans l’orchestration des campagnes.

Vous pouvez en savoir plus [ici](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/data-management/get-started-schemas) si cela vous intéresse.
