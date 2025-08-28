---
title: '[!DNL Journey Optimizer] - Plan directeur des Parcours'
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: e96b48e55c0fe2f48dc83f48ad41f5b686ec8dc1
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 15%

---

# [!DNL Journey Optimizer] Blueprints

Adobe [!DNL Journey Optimizer] est une application native cloud basée sur Adobe Experience Platform qui permet une orchestration planifiée et en temps réel des parcours clients sur plusieurs canaux. Il prend en charge les déclencheurs pilotés par les événements, la segmentation des audiences et les services de prise de décision pour fournir des expériences personnalisées par e-mail, SMS, notification push, web et messagerie in-app. Il s’intègre aux systèmes entrants et sortants, ce qui permet une gestion unifiée de l’état des audiences et de l’engagement contextuel tout au long du cycle de vie du client.

Ce plan directeur décrit les fonctionnalités techniques de l’application et offre une exploration approfondie des différents composants architecturaux qui la [!DNL Journey Optimizer].

<br>

## Cas d’utilisation

>[!BEGINTABS]
>[!TAB Parcours (Piloté Par Les Événements, En Temps Réel)]

- **Récupération des abandons :** déclenchez des messages personnalisés lorsqu’un utilisateur abandonne un panier, un formulaire ou une session par e-mail, push ou in-app.
- **Inscription d’un nouvel utilisateur :** engagez les nouveaux utilisateurs immédiatement après leur enregistrement avec de nouvelles préférences de compte, des promotions ou des avantages pertinents
- **Messages transactionnels :** envoyez des confirmations, des alertes ou des mises à jour en temps réel (par exemple, la commande envoyée, la réinitialisation du mot de passe) à l’aide de déclencheurs d’événement.
- **Ciblage contextuel :** communiquer avec les utilisateurs sur le moment en fonction de leurs signaux et de leur emplacement pour les aider à orienter et à diriger leur expérience
- **Vente contextuelle/vente croisée :** proposez des offres personnalisées basées sur des attributs de profil en temps réel et des interactions récentes.

>[!TAB Orchestration Des Campagnes (Planifiée, Lancée Par La Marque)]

- **Campagnes promotionnelles** : lancez des campagnes à plusieurs étapes et multicanaux pour les lancements de produits, les offres saisonnières ou les événements de vente.
- **Marketing tout au long du cycle de vie** : automatisez les campagnes récurrentes telles que les messages d’anniversaire, les rappels de renouvellement ou les jalons de fidélité.
- **Entonnoirs basés sur l’audience** : segmentez et insérez des audiences dans des campagnes structurées en fonction de la logique commerciale ou des attributs CRM.
- **Newsletter et distribution de contenu** : planifiez et diffusez du contenu personnalisé aux audiences ciblées par e-mail et mobile.
- **Campagnes de réengagement** : identifiez les utilisateurs inactifs et réintroduisez-les dans les flux d’engagement en fonction des seuils d’inactivité.

>[!ENDTABS]

<br>

## Architecture

<img src="images/ajo-architecture.svg" alt="Plan directeur de Adobe Journey Optimizer pour l’architecture de référence" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Scénarios de plan directeur

| Scénario | Description |
| :-- | :-- |
| [Parcours ](journey-optimizer-journeys.md) | Les Parcours AJO dans Adobe Journey Optimizer sont des expériences client personnalisées et automatisées déclenchées par des événements en temps réel ou des segments d’audience. Ils permettent aux spécialistes marketing de diffuser des messages pertinents sur plusieurs canaux tels que les e-mails, les SMS et les notifications push. |
| [Orchestration des campagnes](journey-optimizer-campaigns.md) | L’orchestration des campagnes d’AJO permet aux spécialistes marketing de concevoir et d’exécuter des campagnes cross-canal personnalisées à l’aide de données en temps réel et d’informations sur les audiences. Elle prend en charge le ciblage dynamique, la diffusion des messages et la logique de parcours pour optimiser l’engagement des clients sur les canaux e-mail, SMS, Push et personnalisés. | |

<br>

## Modèles d’intégration

| Intégration | Description | Considérations techniques |
| :-- | :-- | :-- |
| [Messagerie tierce](3rd-party-messaging.md) | Montre comment Adobe [!DNL Journey Optimizer] peut s’intégrer à des plateformes de messagerie tierces pour orchestrer et diffuser des communications personnalisées aux clients. | <ul><li>Le système tiers doit prendre en charge **authentification par jeton du porteur**</li><li>**Les adresses IP statiques ne sont pas prises en charge** en raison de l’architecture multi-utilisateur.</li><li>Tenez compte des **limites de débit d’API** sur les systèmes tiers ; les clients peuvent avoir besoin d’acheter de la capacité supplémentaire pour gérer le trafic provenant de **Adobe Journey Optimizer**.</li><li>La **gestion des décisions** n’est pas prise en charge dans les payloads de message ou la logique de diffusion.</li></ul> |
| [[!DNL Journey Optimizer] avec Adobe Campaign v8](../campaign-v8/ajo-and-campaign-v8.md) | Montre comment Adobe [!DNL Journey Optimizer] peut s&#39;intégrer aux fonctionnalités de messagerie transactionnelle d&#39;Adobe Campaign v8 pour exécuter la diffusion finale des messages. | <ul><li>Les messages ne sont pas limités. Limite de 4 000 messages par période de 5 minutes.</li><li>Ne prend en charge que les parcours déclenchés par un événement</li><li>La gestion des décisions n’est pas prise en charge dans les messages envoyés par Campaign</li></ul> |

<br>

## Conditions préalables

[!DNL Experience Platform] ADOBE :

- Les schémas et les jeux de données doivent être configurés dans le système avant de pouvoir configurer des sources de données [!DNL Journey Optimizer]
- Pour les schémas basés sur la classe d’événement d’expérience XDM, ajoutez le groupe de champs eventID d’orchestration lorsque vous souhaitez déclencher un événement qui n’est pas un événement basé sur des règles
- Pour les schémas basés sur la classe XDM Individual Profile, ajoutez le groupe de champs « Détails du test de profil » pour pouvoir charger des profils de test à utiliser avec [!DNL Journey Optimizer]

<br>

E-mail :

- Vous devez disposer d’un sous-domaine prêt à être utilisé pour l’envoi de messages.
- Le sous-domaine peut être entièrement délégué à Adobe (recommandé) ou les CNAME peuvent être utilisés pour pointer vers des serveurs DNS spécifiques à Adobe (personnalisés).
- Un enregistrement TXT Google est nécessaire pour chaque sous-domaine afin de garantir une bonne délivrabilité.

<br>

Mobile Push :

- Le client doit disposer des services d’un développeur mobile pour créer l’application
- SDK mobile Adobe Experience Platform

<br>

## Garde-fous

[[!DNL Journey Optimizer] Lien du produit Mécanismes de sécurisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Documentation connexe

- [[!DNL Experience Platform] documentation ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
- [[!DNL Experience Platform] Documentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
- [[!DNL Experience Platform Mobile SDK] documentation ](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)