---
title: Simulation de contenu
description: Découvrez comment utiliser l’outil de simulation Adobe Journey Optimizer avec des exemples de données de profil pour valider les champs personnalisés, les variantes de contenu et le comportement de secours.
doc-type: article
solution: Experience Platform
exl-id: 3e2b064f-5680-461c-a49e-2a61514e146f
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Simulation de contenu

**Objectif :** valider la personnalisation, la logique conditionnelle et les variantes de contenu à l’aide des outils de simulation et de BAT de Adobe Journey Optimizer.

## Objectifs d’apprentissage

À la fin de ce module, vous serez en mesure de :

1. Chargez et utilisez les données de profil de test pour la simulation.
1. Validez les champs personnalisés et la logique de variante.
1. Testez le comportement de secours en cas de données manquantes ou non correspondantes.

## Introduction

Dans ce dernier module, vous testerez votre e-mail avec **deux variantes conditionnelles** à l’aide de l’outil Simulation dans Adobe Journey Optimizer.
Vous pouvez ainsi prévisualiser la manière dont différents clients recevront votre message personnalisé, en veillant à la précision avant le lancement de la campagne.

Vous utiliserez l’exemple de fichier de profil de test **sample.csv** de votre boîte à outils.

![Exemple de fichier de profil de test sample.csv de la boîte à outils](assets/content-simulation-sample-csv-toolkit-file.png)

## Ouvrir l’outil de simulation

1. Ouvrez l’e-mail que vous avez terminé.
1. Cliquez sur **Simuler du contenu**.
1. Sélectionnez **Simuler une variation de contenu**.

![Cliquez sur Simuler du contenu et sélectionnez Simuler une variation de contenu](assets/content-simulation-click-simulate-content-variation.png)

Un panneau de simulation s’ouvre au bout de quelques secondes.

## Charger les données du profil de test

1. Ouvrez **sample.csv** à partir du dossier toolkit.
   - **Alex** → Plus de 40 ans
   - **Jason** → Moins de 40 ans
2. Cliquez sur **Charger les données d’entrée**.

   ![Bouton Charger les données d’entrée dans le panneau de simulation](assets/content-simulation-click-upload-input-data.png)

3. Choisissez **sample.csv** et cliquez sur **Continuer**.

![Sélection de sample.csv et clic sur Continuer](assets/content-simulation-choose-sample-csv-continue.png)

AJO traite le fichier et prépare les aperçus.


## Vérifier le rendu des variantes

AJO affiche les deux variantes côte à côte en fonction des profils chargés.

**Résultats attendus :**

- **Alex** → Voir **Variante 1** (Âge supérieur à 40 ans)

![Rendu de profil Alex Variante 1 pour les personnes de plus de 40 ans](assets/content-simulation-variant-1-age-above-40.png)

Si vous faites défiler l’écran vers le haut, vous verrez également des champs personnalisés portant le nom maintenant, comme vous pouvez le voir ci-dessous.

![Champ de nom personnalisé affiché pour Alex dans la variante 1](assets/content-simulation-personalized-name-field-variant-1.png)

- **Jason** → Voir **Variante 2** (Âge inférieur à 40 ans)

![Rendu de profil Jason Variante 2 pour les moins de 40 ans](assets/content-simulation-variant-2-age-below-40.png)

Avec le nom complet de Jason aussi. Comme c&#39;est cool !

![Champ de nom complet personnalisé affiché pour Jason dans la variante 2](assets/content-simulation-personalized-name-field-variant-2.png)



## Validation du comportement de secours

**Secours et valeurs par défaut :** vérifiez que votre e-mail gère correctement les données manquantes ou les scénarios de non-correspondance. Par exemple, simulez un profil avec un champ d’année de naissance vide ou qui n’est éligible à aucune offre ciblée. L’aperçu doit afficher un bloc de contenu par défaut ou un espace réservé pratique au lieu d’un contenu rompu ou vide. Si votre simulation affiche une section vide où le contenu doit se trouver, cela indique que vous devrez peut-être configurer une offre de secours ou un texte par défaut dans votre conception.


## Récapituler

Dans ce module, vous avez réussi à :

- Simulation de contenu personnalisé à l’aide de profils types
- Logique de changement de variante validée
- Les champs personnalisés confirmés sont correctement renseignés

Vous êtes maintenant prêt pour le module suivant : **Alignement des marques**,
où vous évaluerez votre e-mail par rapport aux directives de la marque Connection 5G à l’aide de l’IA.
