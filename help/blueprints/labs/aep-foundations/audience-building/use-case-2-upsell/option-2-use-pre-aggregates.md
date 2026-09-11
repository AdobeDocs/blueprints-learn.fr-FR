---
hold: true
title: null
description: Créez une audience entièrement en flux continu en utilisant des attributs d’utilisation préagrégés calculés en amont au lieu d’agréger les événements dans la règle d’audience.
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# #2 d’options - Utilisation de pré-agrégats

Le problème avec les agrégats dans notre audience est que notre audience (tout en diffusant en continu) est basée sur des agrégations effectuées dans les audiences qui sont des audiences par lots. Étant donné que le service marketing a déterminé qu’une approche plus en temps réel était nécessaire, nous avons effectué trois opérations pour l’intégrer à la conception :

- Calculer les agrégats avant de diffuser les données dans

>[!NOTE]
>
>Cela est assez rare, car la plupart des données diffusées en continu sont conçues autour d’un seul événement par rapport à un agrégat

- Utiliser le nom de plan dénormalisé
- Diffusion des données en continu

## Création de l’audience

Créez une audience de tous les profils dont l’utilisation des données de facturation est élevée, mais qui n’ont pas actuellement de plan de téléphone ultime.

1. Création d’une audience
1. Recherchez « Agg » dans l’onglet Attributs et non Événement et faites glisser les deux Agrégats sur la zone de travail. Définissez les opérateurs et les valeurs appropriés pour chacun d’eux.

![Définissez les opérateurs et les valeurs appropriés pour chaque agrégat](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



&#x200B;3. Recherchez le nom du plan sur le profil et ajoutez-le (Profil individuel XDM > Devbc > Détails du plan > Nom du plan). Sélectionner N’Est Pas Égal À « Ultimate »

![Sélectionner Le Nom Du Plan N’Est Pas Égal À Ultimate](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



&#x200B;4. Fournissez une description.  La méthode d’évaluation Valider est Diffusion en continu.

&#x200B;5. Enregistrez l’audience en tant que « *Utilisation élevée des données de facturation, mais pas de plan Ultimate (Agg)* »

>[!NOTE]
>
>Rappelez-vous, nous avons déplacé la logique d’agrégat dans notre couche ETL de streaming en amont.
>
>Ce choix consiste à choisir entre avoir une audience par lots, où le marketeur contrôle la logique par rapport à une audience par flux, mais en poussant la définition et le contrôle vers la couche ETL où l&#39;ingénierie doit être impliquée.

>[!TIP]
>
>**Laboratoire de défis facultatif**
>
>Fini tôt ?
>
>Nous aimerions contacter nos VIP en temps réel avec un message spécial lors de leur achat.  Créez une audience de « VIP ».  Un VIP est une personne qui a acheté plus de 1 000 $ au cours du dernier mois.
