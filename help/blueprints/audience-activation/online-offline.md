---
title: Plan d'Audience Activation en ligne/hors ligne
description: Audience Activation en ligne/hors ligne.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Plan d&#39;Audience Activation en ligne/hors ligne

Utilisez des attributs et des événements hors ligne tels que les commandes, les transactions, la gestion de la relation client ou les données de fidélité, ainsi que le comportement en ligne pour le ciblage et la personnalisation en ligne.

Activez les audiences vers des destinations profils connues, telles que les fournisseurs de messagerie, les réseaux sociaux et les destinations publicitaires.

## Cas d’utilisation

* Ciblage des Audiences pour les audiences connues sur les destinations sociales et publicitaires.
* Personnalisation en ligne avec attributs en ligne et hors ligne.
* Activez les audiences sur des canaux connus, tels que les courriels et les SMS.

## Applications

* Adobe Experience Platform
*  de la plateforme de données clients en temps réel

## Architecture

<img src="assets/onoff.svg" alt="Architecture de référence pour le scénario Audience Activation en ligne/hors ligne" style="border:1px solid #4a4a4a" />

## Gardiens

* [Instructions relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* Les tâches de segments par lot s’exécutent une fois par jour en fonction du calendrier prédéfini. Les tâches d’exportation de segments sont alors exécutées avant la diffusion de destination planifiée. Notez que les tâches des segments par lot et des diffusions de destination s’exécutent séparément. Les tâches de segments par lot et les performances des tâches d’exportation dépendent du nombre de profils, de la taille des profils et du nombre de segments évalués.
* Les tâches de segmentation en flux continu sont évaluées en quelques minutes après l’arrivée des données en flux continu au profil et écrivent immédiatement l’appartenance au segment au profil et envoient un événement à lequel les applications peuvent s’abonner.
* L’appartenance à un segment de diffusion en continu est appliquée immédiatement pour les destinations de diffusion en continu et est diffusée soit dans des événements d’adhésion à un segment unique, soit dans un micro-lot de plusieurs événements de profil en fonction des schémas d’assimilation de la destination. Les destinations planifiées lancent une tâche d’exportation de segments à partir d’un profil avant la diffusion, pour tous les segments évalués en flux continu qui sont distribués par diffusion de segments par lot planifiés.
* Pour le partage de l’appartenance à un segment RTCDP à l’Audience Manager, cela se produit en quelques minutes pour les segments en flux continu et en quelques minutes à la fin de l’évaluation du segment par lot pour la segmentation par lots.
* Les segments partagés de l’Experience Platform à l’Audience Manager sont partagés dans les minutes qui suivent la réalisation du segment, que ce soit par le biais de la diffusion en continu ou de la méthode d’évaluation par lot. Il existe une synchronisation initiale de configuration de segment entre AEP et AAM une fois le segment créé initialement, après environ 4 heures les adhésions au segment AEP peuvent commencer à être réalisées dans AAM profils. Audience L’adhésion réalisée avant la configuration du partage des audiences Experience Platform et Audiences Manager ou avant la synchronisation des métadonnées d’audience entre l’Experience Platform et l’Audience Manager ne se réalisera pas en Audience Manager tant que la tâche de segmentation suivante ne sera pas effectuée lorsque les adhésions de segments &quot;existantes&quot; seront partagées.
* Les tâches de destination par lot ou en flux continu issues des tâches de segments par lot peuvent partager les mises à jour des attributs de profil ainsi que les adhésions aux segments.
* La diffusion en continu des tâches de segmentation vers les destinations de diffusion en continu ne partage que les mises à jour de l’appartenance aux segments.

## Etapes de mise en oeuvre

1. Configurez des schémas et des jeux de données dans l’Experience Platform.
1. Configurez les identités et les espaces de nommage d&#39;identité corrects sur le schéma pour vous assurer que les données saisies peuvent être associées dans un profil unifié.
1. Activez le schéma et les jeux de données pour le Profil.
1. Envoi de données dans la plate-forme.
1. Configurez le partage de segments de plateforme de données clientes en temps réel entre l’Experience Platform et l’Audience Manager pour que les audiences définies dans l’Experience Platform soient partagées avec l’Audience Manager.
1. Segments d’auteur dans l’Experience Platform, à évaluer par lot ou en flux continu. Le système détermine automatiquement si le segment est évalué en tant que lot ou flux continu.
1. Configurez les destinations pour le partage d&#39;attributs de profil et d&#39;adhésions d&#39;audience vers les destinations souhaitées.

## Considérations relatives à la mise en oeuvre

* Le partage des données de profil vers les destinations requiert que vous incluiez la valeur d&#39;identité spécifique utilisée par la destination dans la charge utile de destination. Toute identité nécessaire pour une destination de cible doit être assimilée à la plate-forme et configurée comme identité pour le Profil client en temps réel.

* Pour les scénarios d’activation où les audiences sont partagées de l’Experience Platform à l’Audience Manager, toutes les identités incluses dans le [!UICONTROL Profil client en temps réel] sont partagées à l’Audience Manager. Les audiences de l&#39;Experience Platform peuvent être partagées par le biais des destinations d&#39;Audience Manager lorsque les identités de destination requises sont incluses dans le [!UICONTROL Profil client en temps réel] ou lorsque les identités dans le [!UICONTROL Profil client en temps réel] peuvent être liées aux identités de destination requises qui sont liées dans l&#39;Audience Manager.

## Documentation connexe

* [Description du produit de la plate-forme de données client en temps réel](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Instructions relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Vidéos et Tutorials connexes

* [Présentation de la plate-forme de données clientes en temps réel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Démonstration de la plateforme de données client en temps réel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
