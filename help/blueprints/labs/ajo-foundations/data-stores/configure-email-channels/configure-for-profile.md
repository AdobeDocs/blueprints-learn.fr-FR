---
title: Configuration d’pour le profil
description: Découvrez comment configurer un canal e-mail à l’aide de l’attribut personalEmail.address du profil AEP pour les Parcours et les campagnes orchestrées.
doc-type: article
solution: Experience Platform
exl-id: bb85e0aa-554e-4527-bf91-e7fd4f69ce71
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: bcc54e483dddad7417ee13613323198c8ce12bec
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 5%
---

# Configuration d’pour le profil

## Objectif

Dans l’ensemble d’étapes suivant, vous allez créer une configuration de canal e-mail avec des Parcours et des campagnes orchestrées à l’aide de l’attribut de profil AEP `personalEmail.address`

## Créer une configuration de canal

1. Accédez à **Configurations de canal** dans le menu **Administration → Canaux → Paramètres généraux**
2. Cliquez sur le bouton **Créer une configuration**

   ![Créer une configuration de canal](assets/configure-for-profile-create-configuration-button.png)

3. Dans l’assistant Créer , définissez les valeurs suivantes :
   - **Nom :** `Profile-Email`
   - **Canal :** `Email`
   - **Action marketing :** `Email Targeting`

![Détails de la configuration du canal](assets/configure-for-profile-channel-configuration-name-values.png)

>[!NOTE]
>
>Lorsque vous sélectionnez E-mail comme canal, une nouvelle section **Paramètres d’e-mail** s’affiche.

## Configurer le type d’e-mail

Définissez le **type d’e-mail** sur **marketing**

![Type D’E-Mail](assets/configure-for-profile-set-email-type-marketing.png)

## Configurer le sous-domaine

Dans la liste déroulante **Sous-domaine**, sélectionnez **email.dep-labs.com**

Liste déroulante ![Sous-domaine avec email.dep-labs.com sélectionné](assets/configure-for-profile-select-email-subdomain.png "Configurer le sous-domaine")

>[!NOTE]
>
>Le sous-domaine peut être différent pour votre environnement.
>Si vous choisissez votre propre rythme et ne disposez pas d’un sous-domaine préconfiguré, sélectionnez ici votre propre sous-domaine délégué à Adobe au lieu de `email.dep-labs.com`. Voir [Installation](../../setup.md) pour savoir comment en déléguer une.

## Configurer les détails du groupe d’adresses IP

Dans la liste déroulante **Groupe d’adresses IP**, sélectionnez **marketing**

![Liste déroulante du groupe d’adresses IP avec marketing sélectionné](assets/configure-for-profile-select-marketing-ip-pool.png "Détails du groupe d’adresses IP")

## Configurer le désabonnement de la liste

1. Assurez-vous que le bouton bascule est **activé** pour list-unsubscribe
1. Sous la zone de préférence Désabonnement de la liste , assurez-vous que toutes les cases à cocher sont **cochées**
1. Sous Gestion des liens , assurez-vous que **Adobe géré** est sélectionné
1. Pour le niveau de consentement, assurez-vous qu’il est défini sur **Canal**

![Désabonnement de la liste de configuration](assets/configure-for-profile-configure-list-unsubscribe-settings.png)

## Configurer les paramètres d’en-tête

1. Définissez les champs suivants comme suit :
   - **Nom de l’expéditeur :** `DEP Labs`
   - **Préfixe d&#39;e-mail de l&#39;expéditeur :** `dep`
   - **Répondre au nom :** `DEP Labs Support`
   - **Répondre à l&#39;e-mail :** `reply@email.dep-labs.com`
   - **Préfixe d&#39;e-mail d&#39;erreur :** `error`

![Paramètres d&#39;en-tête](assets/configure-for-profile-email-header-parameters.png)

## Configurer l’e-mail Cci

Laisser ce champ vide

>[!NOTE]
>
>Vous pouvez conserver une copie des e-mails envoyés en les envoyant à une boîte de réception en Cci. Pour copier chaque e-mail envoyé vers cette adresse en Cci, saisissez l’adresse e-mail de votre choix. Notez que le domaine de l’adresse en copie (Cci) doit être différent de celui d’un sous-domaine délégué à Adobe. Cette fonctionnalité est facultative. *Utilisation de la fonctionnalité Cci pour les e-mails*

## Configurer les paramètres de reprise d’e-mail

Laissez les paramètres par défaut de **Heures** définis sur **84**

## Configuration des paramètres de tracking d’URL

Conserver les paramètres par défaut

## Détails d’exécution

1. Renseignez la section **Détails d’exécution**. Sous l’onglet **Parcours et action** -> **Dimension d’exécution**, sélectionnez **Profil** en tant que **Source** et cliquez sur l’icône Modifier de **Adresse de diffusion** sous la section **Adresse d’exécution**

   ![Détails d’exécution](assets/configure-for-profile-execution-details-journey-tab.png)

2. Cliquez sur le dossier **E-mail personnel** pour l’ouvrir

   ![Adresse de diffusion](assets/configure-for-profile-personal-email-folder.png)

3. Cliquez sur la **case à cocher** dans le champ `Address`, puis sur le bouton **Sélectionner**

   ![Adresse e-mail personnelle en tant qu&#39;adresse de diffusion](assets/configure-for-profile-select-address-checkbox-journeys.png)

4. Pour le **profil**, le `personalEmail.address` est désormais configuré comme **adresse de diffusion** sous la section **Adresse d’exécution**

   ![Adresse de diffusion configurée](assets/configure-for-profile-delivery-address-configured-journeys.png)

5. Cliquez sur l’onglet Campagne orchestrée et **cochez** la case Activé .

   ![Configuration de campagne orchestrée](assets/configure-for-profile-enable-orchestrated-campaign-tab.png)

6. Sous l’en-tête Dimension d’exécution , configurez les éléments suivants :
   - **Diffuser un message par :** `Target Dimension`
   - **Dimension De Profil Cible :** `dep-rel: Customer Account - customer_id`

   ![Dimension Target](assets/configure-for-profile-target-dimension-settings.png)

7. Sous Adresse d’exécution , configurez les éléments suivants :
   - **Source:** `Profile`
   - **Adresse de diffusion :** `click on the Edit icon`

   ![Adresse D’Exécution](assets/configure-for-profile-execution-address-source-profile.png)

8. Recherchez et cliquez sur le dossier `Personal Email` pour l’ouvrir

   ![Attribut de profil d’e-mail personnel](assets/configure-for-profile-search-personal-email-folder.png)

9. Sélectionnez le champ `Address` dans le dossier E-mail personnel et cliquez sur **Sélectionner**

   ![Adresse e-mail personnelle en tant qu&#39;adresse de diffusion](assets/configure-for-profile-select-address-field-orchestrated.png)

10. Pour la **campagne orchestrée**, le **dep-rel : compte client - customer\_id** est configuré en tant que **Dimension de profil Target** pour la **dimension d’exécution** avec **adresse d’exécution** ayant un **Source** de **profil** et `personalEmail.address` comme **adresse de diffusion**

![Dimension d’exécution configurée](assets/configure-for-profile-orchestrated-execution-dimension-configured.png)

>[!NOTE]
>
>Pour les campagnes orchestrées, vous ciblez le compte client avec un e-mail. Il vous suffit donc d’envoyer *un message par profil*.  L&#39;adresse d&#39;exécution que vous utilisez provient du profil lui-même (en particulier, ce qui est stocké dans le profil AEP sous l&#39;attribut **personalEmail.address**)


## Vérifier et enregistrer

1. Vérifiez à nouveau tous les détails pour vous assurer qu’ils correspondent.
1. Faites défiler vers le haut et cliquez sur **Envoyer**.

>[!NOTE]
>
>Il a été observé que le traitement de la configuration du canal e-mail prend jusqu’à 2 heures.
>
>Passez à l’exercice suivant pendant que vous attendez le traitement de cette configuration de canal.

>[!TIP]
>
>🚀 Une fois que le statut de configuration du canal e-mail est **Actif**, il est prêt et peut désormais être sélectionné directement dans les **activités E-mail** dans les campagnes orchestrées.

## Récapituler

Vous avez maintenant appris à créer une configuration du canal e-mail pour utiliser l’attribut de profil AEP pour les campagnes Parcours et orchestrées.
