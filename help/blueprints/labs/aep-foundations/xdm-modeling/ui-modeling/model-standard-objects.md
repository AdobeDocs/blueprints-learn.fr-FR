---
title: Objets standard du modèle
description: Créez un schéma Profil individuel dans l’interface utilisateur et ajoutez et supprimez des groupes de champs standard tels que Détails démographiques et Consentement et préférences.
doc-type: article
solution: Experience Platform
exl-id: ea516c0b-3644-483c-a167-0264cc795449
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%
---

# Objets standard du modèle

## Accès aux schémas

1. Cliquez sur l’onglet **Schémas** dans le rail de gauche

   ![Onglet Schémas dans le volet de navigation du rail de gauche](assets/model-standard-objects-schemas-tab-left-rail.png "Accédez aux schémas à l’aide du rail de gauche")



1. Dans le volet de navigation supérieur, vous pouvez parcourir les schémas existants et afficher les groupes de champs et les types de données qui se trouvent actuellement dans le registre XDM.

![Options de navigation principales pour parcourir les schémas, les groupes de champs et les types de données](assets/model-standard-objects-browse-schemas-top-nav.png "Navigation dans les schémas")

>[!NOTE]
>
>Vous remarquerez qu’il existe déjà des schémas précréés dans votre sandbox. Il s’agit notamment des schémas qui ont été précréés dans le cadre de ce bootcamp (ils sont précédés du préfixe `dep`), ainsi que des schémas générés par le système pour Adobe Real-Time CDP et Adobe Journey Optimizer.


## Créer un schéma de profil individuel

1. Commencez par cliquer sur **Créer un schéma**

   ![bouton Créer un schéma](assets/model-standard-objects-create-schema-button.png "Créer un schéma")



1. Sélectionnez **Manuel**

   ![Sélectionner l’option de création manuelle de schéma](assets/model-standard-objects-select-manual-option.png "Sélectionner manuelle")



1. Sélectionnez **Profil individuel**

![Sélectionner la classe de profil individuel](assets/model-standard-objects-select-individual-profile-class.png "Sélectionner la classe de profil individuel")


## Nommer le schéma

Les schémas basés sur la classe XDM Individual Profile vous permettent de collecter les attributs d’un individu qui sont assemblés au profil. La classe elle-même contient des champs qui ne sont pas modifiables, tels que *modifiedByBatchID*, *PersonID*, etc.

1. Donnez un nom et une description à votre schéma.
   - **Nom D’Affichage Du Schéma** —> *Compte Client - \[Vos Initiales]*
   - **Description** —> Ce schéma collecte les identités, les informations de plan, les détails démographiques et les coordonnées d’une personne.
1. Enregistrez votre schéma à l’aide du bouton **Terminer** en haut à droite.

![Nommez votre schéma, ajoutez une description, puis enregistrez](assets/model-standard-objects-name-schema-and-save.png "Nommez votre schéma, ajoutez une description, puis enregistrez")

## Ajouter un groupe de champs Détails démographiques

Il existe de nombreux groupes de champs qui existent en tant que XDM standard dans Adobe Experience Platform et que vous pouvez ajouter à votre schéma et personnaliser.

1. Cliquez sur le **+ (ajouter)** sur le rail de gauche dans la section groupe de champs .

   ![Bouton Ajouter un groupe de champs dans le rail de gauche](assets/model-standard-objects-add-field-group-button.png "Ajouter un groupe de champs")



1. Recherchez **Détails démographiques** ou trouvez-les en parcourant la liste.

   - Lorsque vous trouvez le groupe de champs, cliquez sur la loupe située à droite du groupe de champs pour en afficher la structure.  Cette étape est utile pour prévisualiser ce que vous êtes sur le point d’ajouter à votre schéma sans l’ajouter.
   - Fermer l’aperçu une fois la révision terminée



   ![Cliquez sur la loupe pour prévisualiser la structure du groupe de champs](assets/model-standard-objects-click-magnify-glass-to-preview-field-group-structure.png "Cliquez sur la loupe pour prévisualiser la structure du groupe de champs")

   ![Aperçu de la structure du groupe de champs Détails démographiques](assets/model-standard-objects-demographic-details-structure-preview.png)



&#x200B;3. **Cochez** case en regard du groupe de champs, puis cliquez sur le bouton **Ajouter des groupes de champs**

![Sélectionnez le groupe de champs Détails démographiques pour l’ajouter à votre schéma](assets/model-standard-objects-select-demographic-details-field-group.png "Sélectionnez le groupe de champs Détails démographiques pour l’ajouter à votre schéma")


## Ajouter d’autres groupes de champs standard

Vous devez ajouter des groupes de champs standard supplémentaires à votre schéma. Répétez les étapes précédentes pour ajouter les deux groupes de champs supplémentaires à votre schéma :

- Coordonnées personnelles
- Détails relatifs au consentement et aux préférences

Lorsque vous avez terminé, votre schéma ressemble à l’image ci-dessous. Veillez à cliquer sur le bouton **Enregistrer** et à enregistrer votre travail !

![Schéma après l’ajout des groupes de champs Détails démographiques, Détails de contact personnels et Détails de consentement et de préférence](assets/model-standard-objects-final-schema-after-adding-field-groups.png "Schéma final après l’enregistrement des ")

>[!NOTE]
>
>Notez que les groupes de champs que vous avez sélectionnés et ajoutés apparaissent maintenant dans votre schéma et s’affichent dans le rail de gauche. Notez que tous les champs de chaque groupe de champs que vous avez ajouté ne sont pas nécessairement nécessaires.  L’étape suivante supprime les champs superflus.

>[!WARNING]
>
>Veillez à enregistrer votre schéma avant de continuer.


## Personnaliser les groupes de champs standard

### Groupe de champs Détails démographiques

Le groupe de champs Détails démographiques a importé de nombreux champs, mais en fonction de la conception de votre schéma à partir de la méthodologie LID, vous n’avez besoin que des champs suivants :

- person.name.firstName
- person.name.lastName
- person.bornDayAndMonth
- person.bornYear

Pour supprimer des champs de n’importe quel groupe de champs standard d’Adobe, utilisez l’option **Gérer les champs associés**. La gestion des champs associés permet de supprimer les champs standard du schéma afin que seuls les champs dont vous avez besoin restent.

1. Sélectionnez l’objet **personne** dans le schéma
1. Cliquez sur le **Gérer les champs associés** dans le rail de droite

   ![Option Gérer les champs associés pour l’objet de personne dans le groupe de champs Détails démographiques](assets/model-standard-objects-manage-related-fields-person-object.png "Gérer les champs associés pour l’objet de personne dans le cadre du groupe de champs Détails démographiques")



1. Développez l’objet personne en cliquant sur le chevron à gauche de personne et développez l’objet nom complet en cliquant sur le chevron à gauche de l’objet nom. Conserver uniquement les champs suivants :

   - person.name.firstName
   - person.name.lastName
   - person.bornDayAndMonth
   - person.bornYear

   Une fois que vous avez terminé, cliquez sur le bouton **Confirmer** dans le coin supérieur droit.

   ![Boîte de dialogue Gérer les champs associés affichant les champs de personne Détails démographiques sélectionnés](assets/model-standard-objects-demographic-details-person-fields-dialog.png "Gérer les champs associés de l’objet de personne Détails démographiques")

   >[!NOTE]
   >
   >Vous pouvez cocher la case située en haut de l’écran pour **Détails démographiques** afin de désélectionner automatiquement tous les objets enfants, puis de ne sélectionner à nouveau que ceux dont vous avez besoin.



1. Lorsque vous avez terminé, vous devriez voir l’objet personne dans votre schéma comme illustré ci-dessous. Pour enregistrer votre schéma, cliquez sur le bouton **Enregistrer** si tout semble correct.

![Objet de personne Détails démographiques finaux contenant uniquement les champs nécessaires](assets/model-standard-objects-final-demographic-details-person-object.png "groupe de champs Détails démographiques finaux contenant uniquement les champs nécessaires")

### Groupe de champs Consentement et Préférences

Effectuez le même ensemble d’étapes que précédemment, mais cette fois pour le groupe de champs Consentement et préférences .

1. Cliquez sur le nom du groupe de champs **Consentement et préférences** dans le rail de gauche pour mettre en surbrillance ses champs dans votre schéma.
1. Sélectionnez l’objet **consentements**, puis utilisez le processus **Gérer les champs associés** pour supprimer les champs non nécessaires de l’objet consentements. Conserver uniquement les champs suivants :

- consentements.marketing.email.val
- consentements.marketing.sms.val

>[!NOTE]
>
>Assurez-vous que le bouton (bascule) est désactivé pour **Afficher les noms d’affichage des champs** dans le coin supérieur droit de l’espace de travail des schémas
>
>![Le bouton (bascule) Afficher les noms d’affichage des champs est désactivé](assets/model-standard-objects-show-display-names-toggle-off.png)



Lorsque vous avez terminé, votre schéma final ressemble désormais à ceci. Veillez à cliquer sur **Enregistrer** avant de continuer.

![Schéma après gestion des champs associés pour le groupe de champs Consentement et préférences](assets/model-standard-objects-final-consent-and-preferences-fields.png "Champs associés gérés pour le groupe de champs Consentement et préférences")

>[!SUCCESS]
>
>Vous avez à présent terminé d’ajouter des composants standard à votre schéma. Très bon travail ! Passez à la création d’attributs personnalisés pour votre schéma.
