---
hold: true
title: XDM d’élément de décision
description: Découvrez le schéma XDM préconfiguré que chaque élément de décision partage et comment les attributs personnalisés sont imbriqués sous un espace de noms client.
doc-type: article
solution: Experience Platform
exl-id: c42503a2-24e7-4a5d-98bf-38c16fe69733
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# XDM d’élément de décision

## Objectif d’apprentissage

À la fin de cette leçon, vous serez en mesure de :

- Identifier le schéma XDM préconfiguré utilisé pour chaque élément de décision
- Expliquez où se trouvent les attributs personnalisés dans le schéma et la limite qui s’y applique
- Reconnaître comment l’imbrication d’attributs sous un objet parent prend en charge la réutilisation

## Matériaux nécessaires

- bloc-notes d&#39;au moins 12 notes autocollantes (plus en cas d&#39;erreur)

## Conférence

Au cours de la vidéo, vous allez vous arrêter pour écrire quatre noms d’attributs dans le haut de vos 12 pense-bêtes. Vous allez renseigner les valeurs réelles dans la leçon suivante.

>[!VIDEO](https://video.tv.adobe.com/v/3502206/)

## Principaux points à retenir

- Chaque élément de décision utilise le même schéma préconfiguré : éléments d&#39;offre personnalisés - prise de décision basée sur l&#39;expérience
- Tout ce qui se trouve sous le nœud \_experience est requis par le système et ne peut pas être modifié
- Les attributs personnalisés se trouvent sous l’espace de noms du client de votre organisation et sont limités à 100 par schéma
- Il n&#39;y a qu&#39;un seul schéma pour chaque élément de décision : aucun doublon ni aucune autre version
