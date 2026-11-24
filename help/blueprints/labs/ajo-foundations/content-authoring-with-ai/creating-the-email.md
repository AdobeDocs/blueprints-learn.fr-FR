---
title: Créer l’email
description: Découvrez comment appliquer un modèle de contenu de marque à un e-mail de campagne dans Adobe Journey Optimizer et remplacer les images de héros et de produit.
doc-type: article
solution: Experience Platform
exl-id: bf823714-7298-48fc-a18b-9bf2462ae52e
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 8a0e198d205b9003fa61cf555debc6c20585b70a
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%
---

# Créer l’email

## Création de contenu avec des modèles

**Objectif :** Découvrez comment créer des modèles réutilisables dans Adobe Journey Optimizer, puis les appliquer dans un e-mail réel au sein d’une campagne.

## Objectifs d’apprentissage

À la fin de ce module, vous serez en mesure de :

1. Créez une campagne et utilisez votre nouveau modèle de marque.
1. Mettez à jour les images principales, les images de produit, les boutons et le style de disposition.

## Créer et mettre à jour l’e-mail dans une campagne

### Objectif

Dans cet exercice, nous allons apprendre à appliquer le modèle que vous avez créé à un e-mail dans un parcours. Dans un scénario idéal, vous pouvez utiliser n’importe quel parcours ou campagne existant et remplacer son contenu d’e-mail par un modèle normalisé afin d’assurer la cohérence de la marque et une exécution plus rapide.

Cette étape montre comment les modèles peuvent être réutilisés sur plusieurs parcours, ce qui permet aux équipes de mettre à jour les conceptions sans devoir reconstruire les e-mails à partir de zéro.

## Créer une campagne par e-mail

1. Revenez à l’écran principal et cliquez sur **Parcours Management → Campagnes**.
2. Cliquez sur **Créer une campagne**

   ![Bouton Créer une campagne dans la gestion des Parcours](assets/creating-the-email-click-create-campaign-button.png)

3. Sélectionnez « **Orchestration Marketing et transactionnel** » et cliquez sur **Confirmer**

   ![Sélection d&#39;Orchestration - Marketing et clic sur Confirmer](assets/creating-the-email-select-orchestration-marketing.png)

4. Nommez votre campagne `Flagship Phone Launch Branded`. Appuyez sur le bouton **Enregistrer**.

   ![Attribuer un nom à la marque du lancement téléphonique phare de la campagne et cliquer sur Enregistrer](assets/creating-the-email-name-campaign-save.png)

5. Cliquez sur le signe **+** et sélectionnez l’activité **Lecture d’audience**

   ![Signez plus pour sélectionner l’activité Lecture d’audience](assets/creating-the-email-click-plus-read-audience.png)

6. L’étape suivante consiste à sélectionner la case **« Lecture d’audience »** et à cliquer sur l’icône **Dossier d’audience**

   ![Boîte Lecture d’audience et icône Dossier d’audience](assets/creating-the-email-read-audience-folder-icon.png)

7. Sélectionnez l’audience **dep : intéressée par iPhone 17** et cliquez sur le bouton « **Ajouter une audience** »

   ![Sélectionnez l’audience iPhone 17 qui vous intéresse et cliquez sur Ajouter une audience](assets/creating-the-email-select-audience-add-button.png)

8. Sélectionnez Entité - **dep-rel : Compte client - customer\_id** (ou tout autre, car cela n’a pas d’importance pour cette partie).
9. Ajoutez l’activité **E-mail** en cliquant sur **+ sign**, puis sélectionnez **E-mail** dans les activités Canal.

   ![Ajout de l’activité E-mail à partir des activités de canal](assets/creating-the-email-add-email-channel-activity.png)

10. Cliquez sur **Modifier l’e-mail**.

![Option Modifier l&#39;e-mail pour l&#39;activité d&#39;e-mail de campagne](assets/creating-the-email-click-edit-email.png)

1. Cliquez sur l’onglet **Action** et sélectionnez **votre** configuration d’e-mail. Votre sandbox peut l’afficher comme E-mail relationnel. (Sélectionnez-en un)

   ![Onglet Action avec la configuration d’e-mail sélectionnée](assets/creating-the-email-action-tab-email-configuration.png)

1. Cliquez sur **Onglet Contenu**

   ![Onglet Contenu dans l’éditeur d’e-mail](assets/creating-the-email-click-content-tab.png)

1. Cliquez sur **Appliquer le modèle de contenu**

   ![Appliquer le modèle de contenu dans l’éditeur d’e-mail](assets/creating-the-email-click-apply-content-template.png)

1. Sélectionnez le modèle **« Modèle promotionnel »** que vous avez créé et cliquez sur **Confirmer**

   ![Sélection du modèle promotionnel et clic sur Confirmer](assets/creating-the-email-select-promotional-template-confirm.png)

1. Cliquez sur **Modifier le corps de l’e-mail**

   ![Option Modifier le corps de l’e-mail après application du modèle](assets/creating-the-email-click-edit-email-body.png)

1. Vérifiez que les nouveaux blocs d’en-tête, de héros, de pied de page et de contenu s’affichent correctement.

![Les blocs d’en-tête, de héros, de pied de page et de contenu apparaissent correctement dans l’e-mail](assets/creating-the-email-header-hero-footer-blocks-confirmed.png)


## Remplacer les images principales et les images de produits

Modifiez les images du héros et du téléphone. Vous devez charger du contenu vers les ressources à partir du dossier de la boîte à outils. Actuellement, votre image de bannière principale de produit est un espace réservé.

1. Cliquez sur l’image de bannière principale rompue.

   ![Cliquer sur l’image de bannière principale de l’espace réservé](assets/creating-the-email-click-broken-hero-banner-image.png)

2. Supprimez l’URL source temporaire.

   ![Suppression de l&#39;URL source temporaire de l&#39;image](assets/creating-the-email-remove-temporary-source-url.png)

3. Cliquez sur **Sélectionner une ressource**

   ![Sélectionnez un bouton de ressource pour l’image principale](assets/creating-the-email-click-import-media.png)

4. Sélectionnez le `hero.png` dans votre dossier et cliquez sur **Sélectionner**.

   ![Sélection de hero.png dans le dossier Assets](assets/creating-the-email-select-hero-png-file.png)

5. Votre modèle d’e-mail s’affiche correctement. Cela ressemble à ce qui suit. Cliquez sur **« Enregistrer »** pour enregistrer votre travail.

![Modèle d&#39;e-mail mis à jour avec la nouvelle image principale avant d&#39;enregistrer](assets/creating-the-email-save-updated-email-template.png)


## Exercice facultatif

### Remplacer les images du produit

Continuez et mettez à jour toutes les images du produit (les images ont été fournies dans le dossier toolkit, vous les avez chargées dans Assets) et ajoutez une bordure arrondie à votre convenance. Votre e-mail s’affiche mieux sans aucun lien rompu, comme illustré ci-dessous. Répétez le processus pour toutes les cartes de produits.

![E-mail avec toutes les images du produit mises à jour et aucun lien rompu](assets/creating-the-email-product-images-updated-no-broken-links.png)

## Récapituler

Dans ce module, vous avez réussi à :

- Création d’une campagne avec un e-mail à l’aide de votre modèle de marque
- Mise à jour des images de héros et de produits
- Style amélioré

Vous êtes maintenant prêt à passer au module suivant : **Personnalisation de contenu assistée par l’IA**, où vous utiliserez l’IA pour affiner le texte et générer automatiquement des images.
