---
title: Personnalisation de contenu assistée par l’IA
description: Utilisez l’IA de Adobe Journey Optimizer pour générer des lignes d’objet de la marque, affiner la copie et le ton des e-mails et créer des images générées par Firefly dans le concepteur d’e-mail.
doc-type: article
solution: Experience Platform
exl-id: 1f30c920-7b2b-4343-b663-ebbed1ae4709
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: ea468b0eddaacdb7beaa1227c9c335371d089f34
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 5%
---

# Personnalisation de contenu assistée par l’IA

**Objectif :** Découvrez comment utiliser l’IA de Adobe Journey Optimizer pour générer des lignes d’objet, affiner le texte des e-mails, ajuster le ton et créer des images Firefly sur la marque directement dans le concepteur d’e-mail.

## Objectifs d’apprentissage

À la fin de ce module, vous serez en mesure de :

1. Utilisez l’IA pour générer des objets et des pré-en-têtes.
1. Affinez le texte, les descriptions, le ton et les messages des héros.
1. Appliquez une reformulation, une synthèse et des ajustements de tonalité pilotés par l’IA.
1. Générez des images à l’aide d’Adobe Firefly avec le style de référence et les paramètres de marque.
1. Remplacez les espaces réservés par les images générées dans votre conception d’e-mail.

## Introduction

L’assistance de l’IA dans AJO vous permet de créer du contenu plus intelligent sur la marque.
Il peut :

- Générer les lignes d&#39;objet
- Améliorer le texte existant
- Ajuster le ton et la clarté
- Création d’images de marque à l’aide de Firefly
- Assurez-vous que tout est conforme aux directives de la connexion 5G

Pour cet exercice, vous allez améliorer l’e-mail que vous avez créé à l’aide de l’IA.

>[!NOTE]
>
>L’IA est **non déterministe**, ce qui signifie qu’elle peut générer un contenu légèrement différent chaque fois qu’elle est utilisée. Ce que vous voyez au cours de votre entraînement peut ne pas correspondre exactement aux captures d&#39;écran ou aux exemples de ce guide. C’est correct : concentrez-vous sur l’apprentissage du processus et des concepts plutôt que sur l’attente de résultats identiques.

## Créer l’objet de l’e-mail à l’aide de l’IA

1. Revenez à la campagne en cliquant sur le bouton Précédent ou modifiez l’e-mail que vous avez créé dans le module précédent. À partir de l’étape précédente, vous pouvez cliquer sur l’onglet **Paramètres** sur le côté droit.
2. Cliquez sur Conteneur d’e-mail > Cliquez sur le bouton Modifier l’e-mail .
3. Cliquez sur l’onglet Contenu , puis sur Corps de l’e-mail .
4. Sélectionnez le champ **Objet**.
5. Cliquez sur l’icône **AI**. (voir ci-dessous)

   Icône ![AI dans la barre d’outils du champ Objet](assets/ai-assistant-and-content-personalization-ai-assistant-icon.png)

6. Notez que Brand Guideline est sélectionné par défaut.
7. Saisissez l’invite :

   >Nous lançons iPhone 17 et souhaitons que l’objet soit accrocheur

8. Appuyez sur **Générer**.
9. Examinez les quatre variantes générées.
10. Sélectionnez la variante présentant le meilleur score d’alignement et cliquez sur **Sélectionner**.

![Sélection de la variante de ligne d&#39;objet la mieux alignée à partir de l&#39;IA](assets/ai-assistant-and-content-personalization-select-subject-line-variant.png)

>[!NOTE]
>
>Vos résultats peuvent être complètement différents de ceux du guide de laboratoire, vous n&#39;avez donc pas à vous inquiéter. Sélectionnez ce que vous pensez être un titre correct et poursuivez avec le Lab.




## Améliorer le titre et la description des héros

1. Ouvrez l’e-mail en cliquant sur le bouton « Modifier le corps de l’e-mail ».

   ![Bouton Modifier le corps de l’e-mail dans l’éditeur Campaign](assets/ai-assistant-and-content-personalization-edit-email-body-button.png)

2. Cliquez sur l’en-tête **Product Catchy line**.
3. Lancez l’assistance de l’IA en cliquant sur **Générer et sélectionner un texte**

   ![Générer et sélectionner une option de texte ouvrant AI](assets/ai-assistant-and-content-personalization-generate-and-select-text.png)

4. Sélectionnez **Consignes relatives à la marque de connexion 5G** dans la liste déroulante.

   ![L’option Consignes relatives à la marque de connexion 5G est sélectionnée dans la liste déroulante IA](assets/ai-assistant-and-content-personalization-brand-guidelines-dropdown.png)

5. Invite :

   >*Écrivez un titre audacieux et captivant pour le lancement d&#39;iPhone 17. Conserver sous 10 mots*

6. Cliquez sur Paramètres de texte pour modifier le ton et la stratégie de communication. Modifiez la stratégie de communication en **FOMO (peur de manquer)**, la langue en **anglais** et le ton en **excitant**.

   ![Panneau de paramètres de texte avec stratégie de communication FOMO et tonalité intéressante sélectionnée](assets/ai-assistant-and-content-personalization-text-settings-fomo-tone.png)

7. Cliquez sur le bouton **Générer**
8. Vérifiez et **Sélectionnez** la meilleure version

![Sélection du texte de titre héroïque généré](assets/ai-assistant-and-content-personalization-select-generated-hero-text.png)

## Invite de description

Cette fois, vous testez la manière dont l’IA peut vous aider à résoudre les problèmes.

1. Sélectionnez le texte sous lequel se trouve le texte modélisé et qui n’a aucune signification.

   ![Texte d’espace réservé modélisé sélectionné pour évaluation](assets/ai-assistant-and-content-personalization-select-templated-text.png)

2. Cliquez sur le bouton d’évaluation comme illustré ci-dessous.

   ![Bouton Évaluer dans le panneau de texte de l’IA](assets/ai-assistant-and-content-personalization-click-evaluate-button.png)

3. Votre contenu d’origine est automatiquement sélectionné avec votre marque, comme indiqué dans les étapes 1 et 2 ci-dessous. Cliquez sur le bouton **Évaluer** pour continuer.

   ![Contenu original automatiquement sélectionné selon les directives de la marque avant évaluation](assets/ai-assistant-and-content-personalization-evaluate-brand-alignment.png)

4. Comme prévu, vous remarquez de nombreuses erreurs qui enfreignent les directives de la marque. Bien que ces erreurs puissent être corrigées à l’aide de l’IA, dans ce cas, vous n’avez pas besoin de réviser ce texte d’espace réservé. À la place, vous pouvez saisir tout le nouveau contenu pour la description.

   ![Résultats de l’évaluation de l’IA montrant des violations des directives de la marque](assets/ai-assistant-and-content-personalization-brand-guideline-errors.png)

5. Vous pouvez suivre les mêmes étapes que vous avez suivies pour le titre de héros précédent, en utilisant l’invite ci-dessous ou... pour gagner du temps, vous pouvez également remplacer le texte d’espace réservé par un paragraphe prêt à l’emploi fourni ci-dessous.

Invite :

>*Rédigez une description de produit attrayante pour la nouvelle iPhone 17. Mettez en avant ses fonctionnalités les plus impressionnantes, telles que l&#39;appareil photo avancé, l&#39;autonomie de la batterie et les performances. Le ton doit être premium, passionnant et facile à comprendre pour un large public. Conserver sous 3 phrases.*

Paragraphe prêt à l’emploi :

>Découvrez iPhone 17™, doté d&#39;un appareil photo de pointe pour des photos époustouflantes, d&#39;une autonomie de batterie toute la journée pour vous maintenir en vie et de performances ultra-rapides qui vous maintiennent en tête. Ne manquez pas cette expérience innovante.



Votre e-mail ressemble à l’exemple illustré ci-dessous.

![Aperçu de l’e-mail après l’ajout du nouveau texte de description généré par l’IA](assets/ai-assistant-and-content-personalization-email-with-description-text.png)


## Ajout d’une image générée par Firefly

Jusqu’à présent, nous avons testé l’IA sur la ligne d’objet et le texte. Qu&#39;en est-il des images ?

Avant de passer à la génération d’images par l’IA, examinez les types d’expériences que vous pouvez créer.

Nous comprenons que nous avons l&#39;année de naissance du profil. L’une des expériences que nous pouvons faire est de créer un bloc avec différentes variantes. Avec Adobe Journey Optimizer, c’est possible et l’un des plus grands avantages d’avoir Adobe Experience Platform comme base. Nous aborderons l’expérimentation dans notre prochain module, mais préparez d’abord le bloc ci-dessous.

1. Faites glisser un composant **Image** vers la colonne de gauche sous le bloc Famille de l’iphone 17.

   ![Faites glisser un composant Image sous le bloc Famille iPhone 17](assets/ai-assistant-and-content-personalization-drag-image-component.png)

2. Cliquez à l’extérieur, puis sélectionnez l’espace réservé pour l’image. (Veillez à cliquer sur l’image, sinon vous ne verrez pas l’option Firefly.)

   ![Sélection de l’espace réservé de l’image pour accéder aux options de Firefly](assets/ai-assistant-and-content-personalization-select-image-placeholder.png)

3. Sous **Firefly**, cliquez sur **Générer et sélectionnez image**.

![Générer et sélectionner l’option d’image sous Firefly](assets/ai-assistant-and-content-personalization-firefly-generate-select-image.png)

## Charger l’image de référence

1. Activer le **style de référence**.
2. Sélectionnez **Guide de la marque de connexion 5G** lors de la sélection de la marque

   ![Guide de marque de connexion 5G sélectionné pour le style de référence d’image](assets/ai-assistant-and-content-personalization-select-brand-guideline-reference.png)

3. Cliquez sur **Charger l&#39;image**

   ![Bouton Charger l’image dans le panneau de style de référence Firefly](assets/ai-assistant-and-content-personalization-click-upload-image.png)

4. Sélectionnez reference.jpg dans le dossier toolkit

   ![Sélection de reference.jpg dans le dossier toolkit](assets/ai-assistant-and-content-personalization-select-reference-jpg.png)

5. Ajouter une invite d’image
   `Portrait-oriented image of a confident man in his early to mid-40s, standing alone at night in a neon-lit urban street, focused on his smartphone. Cinematic cyberpunk-inspired city atmosphere with colorful LED signs, cool blue and warm orange lighting, shallow depth of field, soft bokeh lights in the background. Modern lifestyle, tech-savvy mood, realistic skin tones, high contrast, photorealistic, professional lighting, ultra-detailed`.

Champ d’invite d’image Firefly ![avec description de portrait saisie](assets/ai-assistant-and-content-personalization-firefly-image-prompt.png)

## Choisir les paramètres d’image

Faites défiler la colonne de gauche vers le bas et cliquez sur **Plus de paramètres**

![Sélectionner d&#39;autres paramètres](assets/ai-assistant-and-content-personalization-select-more-settings.png)

1. Choisissez les paramètres suivants :
   - **Rapport :** Paysage (4:3)
   - **Type de contenu :** Photo
   - **Couleur et ton :** Tonalité froide
   - **Éclairage :** Éclairage Dramatique

2. Appuyez sur le bouton **Générer**

![Paramètres d’image Firefly, notamment le rapport, le type de contenu et l’éclairage avant la génération](assets/ai-assistant-and-content-personalization-firefly-image-settings.png)

&#x200B;3. Sélectionnez les variations sur le côté droit pour les afficher et **Enregistrez** quelques-unes de vos favoris dans votre dossier Assets pour les utiliser ultérieurement. Vous pouvez également cliquer sur Générer plusieurs fois pour obtenir d’autres variations.

![Parcourez les variations et enregistrez-en quelques](assets/ai-assistant-and-content-personalization-browse-image-variations.png)

![Enregistrer dans votre dossier Assets](assets/ai-assistant-and-content-personalization-save-image-variations-into-assets.png)

&#x200B;4. Ensuite, il vous suffit de **Annuler** l’interface de génération d’images pour l’instant.



## Finalisation de la conception du bloc

1. De retour dans l’interface du concepteur d’e-mail, cliquez sur **Parcourir** dans le bloc d’image.

![Cliquez sur Parcourir dans le bloc d’image](assets/ai-assistant-and-content-personalization-click-browse-in-image-block.png)

&#x200B;2. Sélectionnez une de vos variations et cliquez sur **Sélectionner**

![Sélectionnez une de vos variations](assets/ai-assistant-and-content-personalization-select-one-of-your-variations.png)

&#x200B;3. Sélectionnez l’onglet **Styles** dans la colonne de droite et appliquez un rayon de bordure arrondi de 10 à l’image

![Conception finale du bloc d’e-mail avec des angles d’image arrondis](assets/ai-assistant-and-content-personalization-final-block-design.png)

Après quelques itérations et variations, vous obtenez la conception finale. Votre mise en page finale ressemble à l’exemple ci-dessus.

À ce stade, vous devriez vous sentir en confiance en utilisant l’IA pour accélérer et élever la création de contenu.

## Récapituler

Vous avez correctement utilisé l’IA pour :

- Générer les lignes d&#39;objet
- Affiner le texte de référence
- Reformuler les paragraphes
- Modifier le ton des messages
- Créer des images Firefly de marque à l’aide du style de référence
- Insertion des images générées dans votre e-mail

Vous êtes maintenant prêt pour le module suivant : **Personalization et expérimentation de contenu**, où vous allez créer des variantes et des tests pilotés par les profils.
