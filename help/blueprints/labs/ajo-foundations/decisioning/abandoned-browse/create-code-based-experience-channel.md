---
title: Créer un canal d’expérience basé sur du code
description: Configurez un canal d’expérience basé sur le code dans Adobe Journey Optimizer qui renvoie des données d’offre JSON à tout système web, mobile ou IoT demandant une décision.
doc-type: article
solution: Experience Platform
exl-id: c3353d3d-cd97-46b7-8ef8-c72fa9e7dfe5
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Créer un canal d’expérience basé sur du code

## Objectif

Rappelez-vous que les exigences commerciales sont que l&#39;un des systèmes de Connection 5G doit être en mesure de renvoyer une offre appropriée. Qu’il s’agisse de l’ordinateur d’un agent client, d’un kiosque en magasin, d’une application mobile ou du site web, le client doit bénéficier de la même expérience d’offre. Le seul canal AJO capable de le faire est une expérience basée sur le code (CBE), l’un des canaux AJO entrants. Bien qu’un CBE puisse renvoyer HTML, sa fonction principale est de renvoyer des informations sur l’offre qui doit être présentée au système récepteur, ce système sachant quoi faire avec ces informations d’offre. Contrairement au canal web, les fichiers CBE ne sont pas automatiquement rendus ou signalés. Bien qu’il s’agisse d’un travail un peu plus manuel pour le client, ils offrent une grande flexibilité, car ils peuvent être configurés pour renvoyer des fichiers JSON que tout système mobile, web ou IoT peut utiliser pour exécuter des décisions.

1. Si nécessaire, développez l’élément de menu **Administration** dans le rail de gauche (vous devrez probablement faire défiler vers le bas) et cliquez sur **Canaux**. Vous accédez à la page « Configurations de canal ».
2. Cliquez sur le bouton bleu **Créer une configuration de canal**
3. Sur la page « Détails de configuration du canal », nommez le canal **jsonOffer\_cbe**

   >[!NOTE]
   >
   >Comme un CBE peut être appelé par un nombre illimité de clients sur *N* nombre de plateformes, nous allons donner à ce CBE un nom générique pour l’emplacement, mais spécifique au fait qu’il renvoie des offres au format JSON.

4. Définissez la liste déroulante **Sélectionner le canal** sur **Expérience basée sur le code.**

   >[!WARNING]
   >
   >Nous ne définirons pas d’action marketing dans cet atelier, car cela ajoute une complexité inutile à notre démonstration. Toutefois, comme plusieurs systèmes peuvent accéder aux fichiers CBE, dans un cas d’utilisation réel, vous définissez toutes les actions marketing possibles pour ce canal afin que les libellés DULE soient appliqués.

5. Cochez la case **Web** dans la zone « Paramètres de l’expérience basés sur le code » et conservez l’option **Une seule page** sélectionnée.
6. Dans la zone de texte **URL de la page**, saisissez le texte `https://connection5g.com/home`
7. Dans la zone de texte **Emplacement sur la page** saisissez le texte **jsonOfferContainer**

   >[!NOTE]
   >
   >Tous les événements d’expérience envoyés à Edge ne déclenchent pas de demande d’offres personnalisées. Vous allez créer un Parcours dans la section suivante où ce CBE sera configuré avec la stratégie de sélection que vous venez de configurer. Le paramètre « Emplacement sur la page » est le nom du paramètre transmis dans les Événements d’expérience qui indique à Experience Edge de renvoyer toutes les offres affectées à ce CBE. On parle aussi souvent de surface. Qu’il s’agisse d’une application mobile, d’une page web ou de tout autre appareil IoT, si la valeur jsonOfferContainer est transmise à Edge, avec le eventType correct via un événement d’expérience, Edge exécutera la logique configurée jusqu’à présent dans le Lab et renverra l’offre appropriée.

8. Cliquez sur le bouton radio **JSON** dans la section « Format ». Lorsque vous avez terminé, la configuration de votre canal CBE doit se présenter comme suit :

   ![Configuration du canal d’expérience basé sur le code terminée avec le format JSON sélectionné](assets/create-code-based-experience-channel-completed-config.png)

9. Une fois que tout semble correct, cliquez sur le bouton bleu **Envoyer** dans le coin supérieur droit.

>[!TIP]
>
>Une fois l’enregistrement effectué, vous revenez à la page de configuration du canal et votre nouvel environnement CBE s’affiche.

## Récapituler

Sur cette page, vous avez configuré un canal d’expérience basée sur le code (CBE) et configuré un nouveau canal entrant qui peut renvoyer les décisions d’offre au format JSON afin que les systèmes externes (tels que les pages web, les applications ou les kiosques) puissent demander et recevoir les offres appropriées en fonction de la stratégie de sélection que vous avez créée précédemment.
