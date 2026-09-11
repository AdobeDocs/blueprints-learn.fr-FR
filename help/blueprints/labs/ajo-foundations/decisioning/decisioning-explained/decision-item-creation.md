---
title: Création d’un élément de décision
description: Découvrez en quoi les attributs des éléments de décision diffèrent des paramètres d’éligibilité, ainsi que le mécanisme de sécurisation au niveau de l’organisation sur les éléments de décision et les impressions par rapport aux événements de décision.
doc-type: article
solution: Experience Platform
exl-id: 28752ac1-118c-41d9-af6a-9907f854df1e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Création d’un élément de décision

## Objectif d’apprentissage

À la fin de cette leçon, vous serez en mesure de :

- Différencier les attributs d&#39;un élément de décision de ses paramètres d&#39;éligibilité
- Indiquez le mécanisme de sécurisation sur les éléments de décision par organisation IMS et pourquoi il est au niveau de l’organisation, et non au niveau du sandbox
- Distinguer une impression d’un événement de décision
- Différenciez les règles de décision des audiences par portée, durée et données auxquelles chacune d&#39;elles peut accéder

## Matériaux nécessaires

- 12 cartes à jouer (Jack, Reine, Roi de chaque couleur)
- 12 notes autocollantes, avec des noms d’attributs déjà écrits dans la leçon précédente

## Conférence

Il s’agit de la leçon la plus pratique à ce jour : vous allez attacher une note autocollante à chaque carte, puis faire une pause à plusieurs reprises pour écrire le niveau, la capacité, l’affichage, la caméra, la priorité et les valeurs d’éligibilité à mesure que chaque concept est introduit.

>[!VIDEO](https://video.tv.adobe.com/v/3502207/)

## Principaux points à retenir

- Un élément de décision comporte deux parties : attributs (nom, description, attributs personnalisés, balises, priorité) et éligibilité (dates, inclusion de règle de décision, inclusion d’audience, limitation)
- Un client peut avoir jusqu’à 10 000 éléments de décision, cette limite étant définie par organisation IMS et non par sandbox
- Les scores de priorité plus élevés sont renvoyés en premier
- Une règle de décision est une condition if/true étendue à une seule campagne ou à un seul parcours, évaluée au moment de la décision, et peut utiliser des attributs d’élément de décision. Une audience est un groupe plus large de profils, évalué à la vitesse de lot/streaming/edge, et ne peut pas accéder aux attributs d’élément de décision
- Utilisez une règle de décision au lieu d’une audience lorsque l’éligibilité dépend des propres attributs de l’élément de décision
- Un élément de décision peut comporter plusieurs déclencheurs de limitation (impressions, clics, événements de décision, événements personnalisés) à la fois
- Une impression est prise en compte lorsque l’élément est réellement affiché sur le serveur Edge ; un événement de décision est pris en compte chaque fois que la prise de décision évalue et renvoie une réponse, visible ou non
- La limitation se réinitialise tous les jours, toutes les semaines ou tous les mois à minuit GMT, et non à l’heure locale
