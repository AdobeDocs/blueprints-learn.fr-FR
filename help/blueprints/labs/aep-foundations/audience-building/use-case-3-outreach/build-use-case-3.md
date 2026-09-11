---
title: Création de
description: Créez une audience par lots qui utilise des variables de conteneur pour faire correspondre, en une semaine, les événements de commande passée et de commande annulée pour la même commande.
doc-type: article
solution: Experience Platform
exl-id: 4b72b76f-de64-4712-85a6-ec7890b23b97
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Création de #3 de cas d’utilisation

## Création de l’audience

1. Création d’une audience
1. Ajoutez Événement de commande passée à la zone de travail
1. Ajoutez Événement de commande annulée à droite de Événement de commande passée .
1. Remplacez la durée par dans la semaine

>[!NOTE]
>
>**Champ de type d’événement**
>
>Nous aurions pu utiliser :
>
>- Tout événement filtré par Type d’événement=order.put
>- Tout événement filtré par type d’événement=order.canceled

![Modifier la fenêtre temporelle de l’événement sur dans la semaine](assets/build-use-case-3-change-time-to-within-a-week.png)



![Les événements Commande passée et Commande annulée sont configurés pour se produire dans la semaine](assets/build-use-case-3-change-time-to-within-a-week--2.png)

>[!NOTE]
>
>**Heure**
>
>Le moteur d’audience utilise uniquement la date et l’heure pour interpréter l’ordre des événements. Ainsi, si l’Événement comporte plusieurs champs datetime, gardez à l’esprit que le champ Timestamp est celui utilisé.



## Configuration de l’événement annulé

Recherchez l’ID de commande et faites glisser le champ sur l’événement Commande annulée .

![Recherchez l’ID de commande et faites glisser le champ sur l’événement Commande annulée](assets/build-use-case-3-search-order-id-drag-onto-order-cancelled-event.png)

>[!NOTE]
>
>Nous ajoutons un filtre pour ID de commande afin de nous assurer que la commande passée est la même que la commande annulée



Effacez toute recherche et cliquez sur **Placé** sous le **Parcourir les variables**

![Cliquez dans Placé sous Parcourir les variables](assets/build-use-case-3-click-into-placed-under-browse-variables.png)



Descendre jusqu’à l’identifiant de commande, puis faire glisser pour ajouter un opérande de comparaison

![Accéder à l’identifiant de commande et le faire glisser pour ajouter un opérande de comparaison](assets/build-use-case-3-drill-down-to-order-id-add-compare-operand.png)

>[!WARNING]
>
>**N’utilisez pas la recherche dans une variable**
>
>Il ne conserve pas le contexte de la variable



Votre résultat final devrait être comme vous l&#39;avez vu ci-dessous

![Configuration finale de l’audience avec l’opérande de comparaison d’ID de commande ajouté](assets/build-use-case-3-final-audience-configuration-result.png)

>[!NOTE]
>
>**Conteneurs**
>
>Cette opération utilise le conteneur de variables pour s’assurer que la commande annulée correspond à la commande passée
>
>Auparavant, nous utilisions un conteneur pour isoler un élément dans un tableau . Ici, nous utilisons des conteneurs pour référencer un événement spécifique dans un critère de filtre à l’intérieur d’un autre événement.
>
>L’événement de commande annulée s’assure que son propre ID de commande est identique à l’ID de commande passée
>
>Comment pourrions-nous utiliser ceci d&#39;autre ?
>
>- La comparaison d’un SKU de produit pour une page vue correspond au SKU de produit acheté
>- Comparer un Livraison à la Ville est différent de la Facturation à la Ville
>- La comparaison de deux champs du même type de données doit être possible même si les événements peuvent provenir de schémas différents
>
>https\://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-exact-do-containers-work-in-aep-segmentation-a-deep-look/ba-p/458780

>[!NOTE]
>
>**Noms de conteneurs**
>
>Les conteneurs héritent de leur nom de variable de leur contexte.
>
>Par exemple, si vous utilisez la carte N’importe quel événement , le nom du conteneur est N’importe lequel1.



## Enregistrer l’audience

1. Fournissez une description. Définissez votre méthode d’évaluation sur Lot.
1. Enregistrez votre audience en tant que « Commande passée et Commande annulée *moins d’une semaine »*

>[!TIP]
>
>**Laboratoire de défis facultatif**
>
>Fini tôt ? Essayez ceci...
>
>Nous aimerions lancer une nouvelle campagne pour Abandonner le panier.  Créez une audience pour abandonner le panier , mais assurez-vous de ne pas commencer à cibler les personnes pendant une heure.
>
>
>
>Vous avez encore du temps ? Essayez ceci...
>
>L&#39;entreprise a fait l&#39;objet d&#39;une fusion et a acquis deux nouvelles unités commerciales pour :
>
>- FAI
>- Câble
>
>Comment devrez-vous modifier les schémas pour les inclure ?
