---
title: Mécanismes de sécurisation, modèles d’IA et avenir de la prise de décision
description: Découvrez les principaux mécanismes de sécurisation de la prise de décision, en quoi les modèles de classement par l’IA diffèrent des formules et comment les blocs de création de la prise de décision se connectent de bout en bout.
doc-type: article
solution: Experience Platform
exl-id: 90902f6e-ba3c-4852-ab82-ad852698b227
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Mécanismes de sécurisation, modèles d’IA et avenir de la prise de décision

## Objectif d’apprentissage

À la fin de cette leçon, vous serez en mesure de :

- Rappelez-vous les deux mécanismes de sécurisation les plus courants dans la pratique
- Différencier l’optimisation automatique des modèles d’IA d’optimisation personnalisée
- Expliquez comment la prise de décision s’étend au-delà de l’ancien produit ODE.
- Résumez comment les huit blocs de création s’intègrent de bout en bout

## Conférence

La vidéo ci-dessous couvre les deux mécanismes de sécurisation de prise de décision les plus courants, la manière dont les modèles de classement par l’IA diffèrent des formules de classement manuelles, la manière dont la prise de décision s’étend au-delà de l’ancien moteur Offer Decisioning et un résumé de la manière dont les huit blocs de création se connectent de bout en bout.

>[!VIDEO](https://video.tv.adobe.com/v/3502212/)

## Principaux points à retenir

- Les deux mécanismes de sécurisation les plus fréquemment consultés : 10 000 éléments de décision par organisation IMS (et non par sandbox) et 100 attributs personnalisés par schéma ; consultez la documentation du produit pour connaître les chiffres actuels, car ils sont susceptibles d’être modifiés
- Les modèles d’IA peuvent être utilisés dans les formules de classement. L’optimisation automatique n’est pas personnalisée et s’optimise sur les performances globales, tandis que l’optimisation personnalisée sert des éléments vers des objectifs commerciaux spécifiques par profil
- Les scores des modèles calculés en dehors d’AEP peuvent être importés en tant qu’attributs de profil et utilisés dans des règles d’éligibilité ou des formules de classement
- La prise de décision va au-delà de l’ancien moteur Offer Decisioning : elle utilise XDM pour la réutilisation, fournit JSON aux applications découplées et sépare l’élément de décision du traitement
- Decisioning peut conditionner le cheminement du parcours et la priorité d&#39;entrée sur une réponse de prise de décision
- De bout en bout : le XDM d’élément de décision définit les attributs → la création d’élément de décision attribue des valeurs et l’éligibilité → éléments de groupe de collections → les formules de classement ajustent la priorité par profil → les stratégies de sélection classent et filtrent une collection → les politiques de décision appliquent des stratégies à un canal → les packages de décision actifs sur le hub ou le edge
