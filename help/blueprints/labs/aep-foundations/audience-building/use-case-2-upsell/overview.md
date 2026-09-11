---
hold: true
title: Cas d’utilisation
description: Définissez un cas d’utilisation de montée en gamme ciblant les clients utilisant beaucoup de données sans plan téléphonique final, en comparant les approches d’agrégation des audiences pour l’activation.
doc-type: overview-page
solution: Experience Platform
exl-id: d0268de8-87eb-4dd9-b699-99d42716f20c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Cas d’utilisation #2 - montée en gamme

## Présentation

Dans cette vidéo, vous apprendrez à aborder le cas d’utilisation de montée en gamme, qui cible les clients à forte utilisation de données pour activation via les canaux de publipostage payant et direct.

>[!VIDEO](https://video.tv.adobe.com/v/3459487/?quality=12&learn=on)



**Définition de cas d’utilisation**

Recherchez tous les clients qui ont utilisé un total de données de facturation au cours des 6 derniers mois >140GB, soit une moyenne mobile de 6 mois. utilisation mensuelle des données de >=20 Go et qui n’ont pas de forfait téléphonique ultime.

Activez dans les canaux Facebook / Google et Courrier.

Champs de personnalisation du publipostage direct :

- Prénom → utilisé pour la salutation
- → de l’adresse postale utilisée pour le publipostage
- Nom du plan → utilisé pour la déclaration de publipostage (par exemple, « Eric, passez à un plan ultime dès aujourd’hui ! »).



## Tâches d&#39;analyse

Analysez ce qui précède et notez ce qui suit :

1. Quels champs pensez-vous nécessaires pour résoudre ce cas d’utilisation ?
1. La méthode d’évaluation doit-elle être Diffusion en continu ?
1. Que devons-nous garder à l’esprit avec les données de facturation ?
1. Quelles autres informations souhaitez-vous connaître ?

Souvenez-vous : lorsque nous obtenons les exigences des parties prenantes de l’entreprise, elles ont tendance à être incomplètes, à utiliser une autre terminologie et à émettre des hypothèses sans les connaître. C&#39;est votre travail de faire ressortir le plus de choses possible et de les guider vers quelque chose qui peut être fait.



## Approche

Pour ce cas d’utilisation, nous allons évaluer deux options :

- #1 d’option (utiliser l’audience pour l’agréger)
  - L’audience effectue alors l’agrégation.
    - Somme d’utilisation des données de facturation >140GB (6 derniers mois)
    - Utilisation des données de facturation Moy. >20 Go (6 derniers mois)
    - Utilisation Élevée Des Données De Facturation, Mais Pas De Plan Ultimate
- #2 D’Option (Utilisation De Pré-Agrégats)
  - Cette opération utilise l’agrégation qui a été effectuée avant de placer les données sur le profil
    - Utilisation Élevée Des Données De Facturation, Mais Pas De Plan Ultimate (Agg)
