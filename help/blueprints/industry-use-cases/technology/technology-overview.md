---
title: Cas d’utilisation de la technologie
description: Découvrez comment les entreprises technologiques utilisent Adobe Experience Platform pour unifier la collecte de données, transférer des événements en temps réel et alimenter l’analyse et l’activation sur les produits numériques.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 77908fd8a9f4309cbe66063cd33f065424697e55
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Cas d’utilisation de la technologie

Les entreprises technologiques utilisent Adobe Experience Platform pour centraliser la collecte de données à partir de surfaces web, mobiles et de produits et distribuer des événements en temps réel aux destinations d’analyse, d’entrepôt de données et d’activation qui alimentent leurs produits et programmes marketing. En consolidant la collecte d’événements à la périphérie, les équipes technologiques réduisent la complexité côté client, améliorent la qualité des données et s’assurent que tous les systèmes en aval reçoivent des données comportementales cohérentes d’une source unique faisant autorité.

## Transfert d’événement en temps réel

Transférez les événements comportementaux en temps réel collectés via Edge Network à des analyses tierces, des entrepôts de données et des plateformes partenaires pour enrichissement et activation. La centralisation de la collecte d’événements à la périphérie et du transfert vers plusieurs destinations réduit la surcharge des balises côté client, améliore la qualité des données et garantit que tous les systèmes en aval reçoivent des données d’événement cohérentes d’une source unique faisant autorité.

### Impact commercial

Les entreprises technologiques mettant en œuvre le transfert d’événement en temps réel réduisent la charge des balises côté client et la surcharge de performances associée, tout en améliorant la cohérence des données d’événement sur les destinations d’analyse, d’entrepôt de données et d’activation. Le transfert côté serveur réduit également le poids de la page et améliore les performances de chargement, ce qui bénéficie directement aux mesures d’expérience utilisateur.

### Mise en œuvre

Utilisez le modèle [Transfert d’événement](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md) pour acheminer les événements collectés par Adobe Experience Platform Web SDK via Edge Network vers des destinations côté serveur configurées. Il s’agit du modèle approprié lorsque l’objectif est la distribution d’événements serveur à serveur à partir d’un seul point de collecte, plutôt que de gérer des balises distinctes pour chaque destination côté client, ce qui ajoute du poids à la page et crée des incohérences de données entre les systèmes.

### Considérations techniques

- Le transfert d’événement Edge Network nécessite la migration de la collecte d’événements vers Adobe Experience Platform Web SDK ou Mobile SDK. La compatibilité des implémentations existantes basées sur les balises doit être évaluée avant que les destinations de transfert ne soient configurées.
- Les règles de transfert doivent être configurées pour envoyer uniquement les champs requis par chaque destination. Évitez de transférer des payloads XDM complètes vers des destinations qui n’ont besoin que d’un petit sous-ensemble de champs, car cela augmente les coûts de transfert de données et entraîne une exposition à la conformité.
- Les connecteurs de destination doivent gérer les échecs de manière élégante. Les pipelines de transfert d’événement doivent implémenter une logique de reprise et des alertes pour les destinations qui ne sont plus disponibles, afin d’éviter la perte de données lors des pannes.
- Les politiques de gouvernance des données doivent être examinées pour chaque destination de transfert afin de s’assurer que les préférences de consentement des utilisateurs capturées à la périphérie sont respectées dans la configuration de transfert.
