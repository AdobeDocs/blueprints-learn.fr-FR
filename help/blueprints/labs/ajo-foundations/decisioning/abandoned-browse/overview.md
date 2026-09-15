---
title: Navigation abandonnée
description: Découvrez comment créer un workflow de prise de décision de navigation abandonnée de bout en bout qui fournit des offres téléphoniques personnalisées et basées sur l’éligibilité sur l’ensemble des canaux.
doc-type: overview-page
solution: Experience Platform
exl-id: 37b8a0b3-2820-4303-81d2-19890a3c5782
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%
---

# Navigation abandonnée

## Conditions préalables

>[!WARNING]
>
>Les exercices ci-dessous doivent avoir été terminés avant de démarrer cet exercice

- Installation de **&#x200B;**&#x200B;**—>** installation de [Postman](../../postman-setup/postman-installation.md)
- **Magasins de données — Profil en action** **—>** [Créer un flux de données](../../data-stores/profile-in-action/create-datastream.md)

Si vous n&#39;avez pas terminé ces laboratoires, faites-le maintenant avant de continuer.

## Présentation de l’atelier

Dans cette vidéo, vous découvrirez comment la description du cas d’utilisation de navigation abandonnée révèle ses éléments de prise de décision, et ce que vous allez créer dans cet atelier pour diffuser en temps réel une offre téléphonique personnalisée et tenant compte de l’éligibilité.

>[!VIDEO](https://video.tv.adobe.com/v/3491316/)

## Objectifs commerciaux

Pour ce Lab, Connection 5G souhaite augmenter les ventes du nouveau téléphone phare d’Apple, iPhone 17, en ciblant les clients qui ont parcouru la page d’aperçu d’iPhone 17 sans effectuer d’achats. Les principaux objectifs de la campagne sont les suivants :

- **Identifiez les clients à forte intention** en détectant le moment où un utilisateur consulte plusieurs fois une page téléphonique phare sans effectuer d’achat.
- **Déclenchez une expérience personnalisée en temps réel** sur toutes les surfaces numériques de Connection 5G lorsque ce comportement se produit.
- **Proposez des offres contextuelles** basées sur les attributs clés du client, tels que l’âge du titulaire du compte **compte** et son **forfait mobile actuel**.
- **Assurez-vous que l’éligibilité de l’offre est appliquée** de sorte que les clients ne voient que les offres téléphoniques compatibles avec leur plan.
- **Ajustez de manière dynamique le niveau téléphonique proposé** (par exemple, de base, pro, ultra) en fonction de l’engagement ou de la réponse du client par rapport aux offres précédentes.
- **Personnalisation cohérente sur l’ensemble des canaux** en utilisant une logique de prise de décision centralisée pour déterminer la meilleure offre en temps réel.
- **Augmentez la probabilité de conversion** en présentant l’offre téléphonique phare la plus pertinente à chaque client au bon moment.

## Objectifs d’apprentissage du Lab

Pour atteindre les objectifs commerciaux ci-dessus dans cet atelier, vous apprenez à :

- **Étendez le modèle de données de l’offre** en ajoutant des attributs personnalisés au schéma de l’offre afin qu’ils puissent être utilisés dans la logique de prise de décision.
- **Créez des règles d’éligibilité** qui déterminent les profils qui remplissent les critères pour des offres spécifiques en fonction des attributs de profil.
- **Créez et configurez des éléments d’offre** notamment en définissant des priorités, en définissant des conditions d’éligibilité et en appliquant un capping de la fréquence.
- **Organisez les offres en une collection** afin qu&#39;elles puissent être facilement référencées et évaluées au cours de l&#39;activité de prise de décision.
- **Créez une formule de classement** qui ajuste dynamiquement la priorité des offres en fonction des caractéristiques du profil.
- **Configurez une stratégie de sélection** qui combine des collections d’offres, des règles d’éligibilité et une logique de classement afin de déterminer les offres à prendre en compte et leur classement.
- **Configurez un canal d’expérience basée sur le code (CBE)** pour permettre aux systèmes externes de demander des résultats de décision et de recevoir des offres au format JSON.
- **Testez le workflow de prise de décision de bout en bout** en envoyant des événements d’expérience et des requêtes de décision pour valider la logique d’éligibilité, le comportement de classement et le capping de la fréquence.

En terminant cet atelier, vous acquérez une expérience pratique dans la conception et la validation d’un **workflow complet d’Offer Decisioning dans Adobe Journey Optimizer** pour répondre au cas d’utilisation professionnel.
