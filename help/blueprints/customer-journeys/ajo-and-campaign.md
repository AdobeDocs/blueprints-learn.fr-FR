---
title: Journey Optimizer avec plan directeur Adobe Campaign
description: Illustre l’utilisation d’Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: ht
source-wordcount: '504'
ht-degree: 100%

---

# Journey Optimizer avec Adobe Campaign

Illustre l’utilisation d’Adobe Journey Optimizer avec Adobe Campaign pour envoyer des messages en mode natif à l’aide du serveur de messagerie en temps réel dans Campaign.

<br>

## Architecture

<img src="assets/ajo-campaign-architecture.svg" alt="Plan directeur Journey Optimizer de l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>L’utilisation de Journey Optimizer et de Campaign pour envoyer des messages indépendamment les uns des autres est possible mais présente des considérations techniques à prendre en compte. Si vous souhaitez suivre cette route, contactez votre architecte d’entreprise de prévente afin de vous assurer que vous comprenez ce qui sera nécessaire pour prendre en charge l’implémentation.

<br>

## Conditions préalables

### Adobe Experience Platform

* Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer les sources de données Journey Optimizer.
* Pour les schémas basés sur la classe Événement d’expérience, ajoutez le groupe de champs « Orchestration eventID » lorsque vous souhaitez qu’un événement déclenché ne soit pas basé sur des règles.
* Pour les schémas basés sur une classe Profil individuel, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec Journey Optimizer.
* Journey Optimizer et Campaign sont configurés dans la même organisation IMS.

### Campaign v7/v8 ou Campaign Standard

* L’instance d’exécution du service de messagerie en temps réel (soit le Message Center) doit être hébergée par les Managed Cloud Services Adobe.
* La création de tous les messages s’effectue dans l’instance Campaign elle-même.

<br>

## Garde-fous

[Lien de produit pour les garde-fous de Journey Optimizer](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr)

### Autres garde-fous Journey Optimizer

* La limitation est désormais disponible par le biais de l’API pour garantir que le système de destination n’est pas saturé au point d’échec. Cela signifie que les messages qui vont au-delà du plafond seront ignorés et ne sont jamais envoyés. La limitation n’est pas prise en charge.
   * Connexions max. - Nombre maximal de connexions http/s qu’une destination peut gérer
   * Nombre d’appels max - Nombre maximal d’appels pouvant être effectués dans le paramètre periodInMs
   * periodInMs - temps en millisecondes
* Les parcours initiés d’abonnement à un segment peuvent fonctionner suivant deux modes :
   * Segments par lot (actualisés toutes les 24 heures)
   * Segments par diffusion en flux continu (qualification de moins de 5 minutes)
* Segments par lot : veillez à connaître le volume quotidien des utilisateurs qualifiés et à garantir que le système de destination peut gérer les pics de débit par parcours et sur tous les parcours.
* Segments en diffusion en continu : veillez à ce que le pic initial des qualifications de profil puisse être traité en même temps que le volume de qualification des diffusion en continu quotidien par parcours et sur tous les parcours
* Gestion des décisions non prise en charge
* Les événements métier ne sont pas pris en charge.
* Intégrations sortantes vers des systèmes tiers :
   * Pas de prise en charge d’une seule adresse IP statique, car notre infrastructure est définie pour plusieurs clients (doit mettre en liste autorisée toutes les adresses IP du centre de données).
   * Seules les méthodes de POST et de PUT sont prises en charge pour les actions personnalisées.
   * Prise en charge de l’authentification : token | password | OAuth2
* Il n’est pas possible de regrouper et de déplacer des composants individuels d’Adobe Experience Platform ou de Journey Optimizer entre différentes sandbox. Vous devez les réimplémenter dans les nouveaux environnements.

<br>

### Intégrations de Campaign

Pour plus d’informations sur l’intégration dans votre version spécifique d’Adobe Campaign et Adobe Journey Optimizer, consultez le guide correspondant à chaque version d’Adobe Campaign.

* [Adobe Journey Optimizer et Campaign v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer et Campaign v8](ajo-and-campaign-v8.md)