---
hold: true
title: Libellé
description: Étiquetez les tables de l’entrepôt de données relationnelles en tant que classes XDM Individual Profile, Experience Event ou Lookup dans le cadre de la méthodologie LID.
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Libellé

## Conférence

Dans cette vidéo, vous apprendrez à libeller les tables relationnelles en tant que table XDM Individual Profile (P), Experience Event (E) ou Lookup (L) à l’aide de l’ERD de connexion 5G à titre d’exemple.

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## Détails de l’atelier

Étiquetez les tables de l’ERD de l’entrepôt de données Connection 5G et de l’ERD de diffusion en continu avec le libellé de classe XDM approprié pour les tables de profil individuel, d’événement d’expérience et de recherche.

Gardez à l’esprit les points suivants lors de l’exécution du Lab :

- **Profil individuel (caractéristiques) -** décrit de manière unique les caractéristiques d’une personne (par exemple, nom, adresse e-mail, adresse, préférences, etc.)
- **Événement d’expérience (comportements) -** décrire les interactions et les points de contact d’une personne avec une marque/entreprise (par exemple, visite de la page web, achat, interactions du centre d’appels, envoi de la demande, etc.)
- **Recherches (prise en charge)** fournissent des informations contextuelles supplémentaires à l’appui du profil individuel ou de l’événement d’expérience



## Étape 1. Étiqueter les tableaux de profils individuels XDM

1. Identifiez toutes les tables source qui représentent une personne individuelle à la fois dans l’ERD de l’entrepôt de données client et dans l’ERD de diffusion en continu client.
1. Marquez chaque tableau avec un « **P** » signifiant qu’il fait partie de la classe XDM Individual Profile

>[!NOTE]
>
>Ne marquez que les tableaux qui représentent de manière unique les caractéristiques d’une personne



## Étape 2. Étiqueter les tableaux d’événements d’expérience XDM

1. Identifiez toutes les tables sources qui représentent le comportement d’une personne individuelle dans l’ERD de l’entrepôt de données de connexion 5G et l’ERD de diffusion en continu.
1. Marquez chaque tableau avec un « **E** » signifiant qu’il fait partie de la classe Événement d’expérience XDM.

>[!NOTE]
>
>Ne marquez que les tableaux qui représentent de manière unique le comportement d’une personne individuelle



## Étape 3. Étiqueter les tables de prise en charge XDM

1. Identifiez toutes les tables sources qui représentent les données de recherche et qui sont directement liées à une table **« P »** ou **« E »** que vous avez marquée dans l’ERD de l’entrepôt de données de connexion 5G et l’ERD de diffusion en continu.
1. Marquez chaque tableau avec un **« L »** ce qui signifie qu’il fait partie d’une classe XDM personnalisée non personnelle.

>[!NOTE]
>
>Les tables de recherche ne peuvent se trouver qu&#39;à 1 niveau de jointure ou à « hop » d&#39;une table étiquetée « P » ou « E »



## Révision

La vidéo ci-dessous passe en revue les libellés corrects pour les ERD de l’entrepôt et de la diffusion en continu Connection 5G, expliquant pourquoi les tables du compte client, des commandes et des relevés de facturation ont été libellées comme elles l’étaient.

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)
