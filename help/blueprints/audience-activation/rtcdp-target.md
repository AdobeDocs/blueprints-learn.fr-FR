---
title: Personalization client connu avec Target
description: Intégrez des profils et des audiences RTCDP à Adobe Target.
landing-page-description: Intégrez des profils et des audiences RTCDP à Adobe Target.
short-description: Intégrez des profils et des audiences RTCDP à Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
  - id: ee602049-8a18-43df-9299-a689a025a371
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 213e2d7d73d91fa7b487289dfe62685bc32d5029
workflow-type: tm+mt
source-wordcount: 735
ht-degree: 37%

---

# Personalization client connu avec Target

>[!TIP]
>Ce plan directeur est également disponible en tant que [&#x200B; modèle de cas d’utilisation &#x200B;](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md) sous Personalization.

## Cas d’utilisation

* Personnalisation en ligne avec des données client connu
* Optimisation de la page de destination
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit/contenu, des attributs environnementaux et des données démographiques, en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées
* Partager et cibler des audiences définies dans Real-time Customer Data Platform sur des sites web et des applications mobiles à l’aide d’Adobe Target

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### Documentation de référence

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr)
* [Configuration du flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=fr)

## Modèles d’intégration

| Motif d’intégration | Fonctionnalité | Conditions préalables |
|--------------------|------------|---------------|
| **Évaluation des segments en temps réel sur Edge, partagée de Real-time Customer Data Platform vers Target** | - Évaluez les audiences en temps réel pour la personnalisation de la même page ou de la page suivante sur Edge. <br>- Tous les segments évalués en flux continu ou par lots seront également projetés dans Edge Network pour être inclus dans l’évaluation et la personnalisation des segments Edge. | - Web/Mobile SDK doit être implémenté pour l’API Edge Network Server. <br>- Le flux de données doit être configuré dans Experience Edge avec l’extension Target et Experience Platform activée. <br>- La destination cible doit être configurée dans les destinations Real-time Customer Data Platform. <br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform. |
| **Partage d’audiences par lots et en flux continu depuis Real-time Customer Data Platform vers Target via l’approche Edge** | - Partagez des audiences en continu et par lots à partir de Real-time Customer Data Platform vers Target par le biais d’Edge Network. <br>- Les audiences évaluées en temps réel nécessitent l’implémentation de Web SDK et d’Edge Network. | - L’implémentation de l’API Web/Mobile SDK ou Edge de Target n’est pas nécessaire pour partager des audiences RTCDP en flux continu et par lots vers Target, mais elle est nécessaire pour permettre l’évaluation des segments Edge en temps réel. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espace de noms d’identité personnalisées sur Edge, le déploiement de l’API Web SDK/Edge est obligatoire et chaque identité doit être définie comme identité dans le mappage d’identités. <br>- La destination cible doit être configurée dans les destinations de Real-time Customer Data Platform. Seul le sandbox de production par défaut dans RTCDP est pris en charge. <br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform. |
| **Partage d’audiences par lots et en flux continu depuis Real-time Customer Data Platform vers Target et Audience Manager via l’approche du service de partage d’audience** | - Ce modèle d’intégration peut être utilisé lorsque vous souhaitez un enrichissement supplémentaire à partir de données et d’audiences tierces dans Audience Manager. | - Le SDK web/mobile n’est pas nécessaire pour partager des audiences par lots et en flux continu avec Target, mais il est nécessaire pour activer l’évaluation des segments Edge en temps réel. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espace de noms d’identité personnalisées sur Edge, le déploiement de l’API Web SDK/Edge est obligatoire et chaque identité doit être définie comme identité dans le mappage d’identités. <br>- La projection d’audience via le service de partage d’audience doit être configurée. <br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform. <br>- Seules les audiences du sandbox de production par défaut prennent en charge le service principal de partage d’audiences. |

## Partage d’audiences en temps réel, en flux continu et par lots vers Adobe Target

Architecture

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/RTCDP+Target.png)

Détails de la séquence

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/RTCDP+Target_flow.png)

Architecture d’aperçu

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/personalization_with_apps.png)

## Documentation connexe

### Documentation du SDK

* [Documentation Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
* [Documentation Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation du service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)

### Documentation sur la segmentation

* [Présentation de la segmentation Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en temps réel](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=fr)
* [Segmentation par flux](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Configuration de la politique de fusion](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=fr#create-a-merge-policy)

### Tutoriels

* [Personnalisation des accès suivants avec Real-Time CDP et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=fr)
