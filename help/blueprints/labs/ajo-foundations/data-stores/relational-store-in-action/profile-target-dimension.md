---
title: Dimension de Profile Target
description: Découvrez comment étiqueter un champ de schéma relationnel comme identité et créer un Dimension de cible de profil pour joindre le profil client en temps réel au magasin relationnel.
doc-type: article
solution: Experience Platform
exl-id: bfc71051-e471-4d5c-a9a7-bb6805a5acb1
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Dimension de Profile Target

## Objectif

Dans les étapes suivantes, vous allez parcourir l’interface utilisateur pour afficher le schéma et configurer l’identité. Ensuite, vous allez configurer le Dimension de la cible du profil, qui est le type d’entité que la campagne cible et réconcilie avec le profil AEP pour la diffusion.

## Pourquoi c’est important

Le Dimension Profile Target est utilisé pour indiquer à Adobe Journey Optimizer comment les données entre le profil client en temps réel et le magasin relationnel peuvent être jointes. Les composants de cette configuration sont les suivants :

- Un schéma relationnel
- Un seul champ du schéma relationnel
- Un espace de noms d’identité associé à ce champ

>[!CAUTION]
>
>Sans cette configuration, aucune lecture ou partage d’audiences ne peut avoir lieu et aucun message ne peut être envoyé en dehors des campagnes orchestrées

## Étiqueter l’identité

1. Cliquez sur l’icône **Applications** et sélectionnez **Journey Optimizer**

   ![Menu de l’icône des applications avec Journey Optimizer sélectionné](assets/profile-target-dimension-navigate-to-journey-optimizer.png)

2. Cliquez sur **Schémas** dans le menu Gestion des données et assurez-vous que l’onglet **Parcourir** est sélectionné.
3. Recherchez le schéma appelé `dep-rel: Customer Account`

   ![Recherche de schéma pour dep-rel : compte client](assets/profile-target-dimension-search-schema.png)

4. Ouvrez le schéma en cliquant sur son nom, puis cliquez sur le champ **customer\_id**

   ![Liste des champs de schéma avec customer_id sélectionné](assets/profile-target-dimension-select-customer-id-field.png)

5. Dans le rail de droite, cochez la case **Identité**, **cochez la case** et choisissez l’espace de noms d’identité intitulé **customerID**

   ![Case à cocher Identité avec l’espace de noms customerID sélectionné](assets/profile-target-dimension-choose-identity-namespace.png)

6. Cliquez sur le bouton **Enregistrer** pour enregistrer le schéma. Un message de confirmation s’affiche
7. Cliquez sur le bouton **Annuler** ou sur le **Schémas** dans le rail de gauche pour quitter l’interface utilisateur du schéma

>[!CAUTION]
>
>Si vous n’enregistrez pas le schéma après l’ajout du libellé d’identité, l’ensemble d’étapes de configuration suivant ne fonctionne pas

>[!NOTE]
>
>Après l’enregistrement, cela prend quelques minutes (moins de 5 minutes) avant d’apparaître dans le menu déroulant Dimension de Profile Target à l’étape suivante.

## Création du Dimension de Profile Target

1. Cliquez sur **Configurations** sous **Administration**

   ![Menu Administration avec Configurations sélectionné](assets/profile-target-dimension-configurations-menu.png)

2. Sélectionnez **Profile Target Dimension** et cliquez sur **Gérer**

   ![Configuration de Profile Target Dimension avec l’option Gérer &#x200B;](assets/profile-target-dimension-manage-configuration.png)

3. Le volet Dimension de Profile Target s’ouvre. Cliquez sur **Créer**

   ![Volet Dimension de Profile Target avec le bouton Créer](assets/profile-target-dimension-create-button.png)

4. Sélectionnez le schéma `dep-rel: Customer Account` dans la liste déroulante.

   >[!NOTE]
   >
   >Le schéma peut prendre quelques minutes pour apparaître dans cet écran après le marquage de l’identité. Actualisez la page et répétez les deux étapes précédentes jusqu’à ce que le schéma s’affiche.

   ![Création d’un formulaire Dimension Profile Target avec la liste déroulante de schéma](assets/profile-target-dimension-select-schema-dropdown.png)

5. Pour l’**Valeur d’identité** sélectionnez `/customer_id`

   ![&#x200B; Liste déroulante Valeur d’identité avec /customer_id sélectionné](assets/profile-target-dimension-select-identity-value.png)

   >[!NOTE]
   >
   >Un schéma relationnel peut comporter de nombreux champs étiquetés avec des identités, il s’agit donc d’une zone de liste.



6. Cliquez sur le bouton **Enregistrer** pour créer le Dimension cible du profil. L’enregistrement s’affiche alors.

![Enregistrement Dimension cible de profil enregistré dans la liste](assets/profile-target-dimension-saved-record.png)

>[!NOTE]
>
>Le nom de l’enregistrement créé est une concaténation du nom du schéma *(dep-rel : Customer Account)* et du champ libellé avec l’identité *(customer\_id)*

>[!TIP]
>
>Félicitations ! Cela conclut l’étape de création du Dimension de Profile Target dans l’atelier.

## Récapituler

Vous avez maintenant vu à quel point il est facile de naviguer dans le schéma, de marquer un attribut comme une identité et de créer le Dimension cible de profil.

Vous pouvez en savoir plus [ici](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/data-configuration/target-dimension) si cela vous intéresse.
