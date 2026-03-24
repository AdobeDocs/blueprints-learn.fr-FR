---
title: Activation des messages sortants par lots
description: Découvrez comment évaluer une audience et diffuser un message sortant planifié dans une seule exécution par lots.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 1%

---

# Activation des messages sortants par lots

Ce guide fournit une référence d’implémentation complète pour la diffusion de messages sortants planifiés vers des segments d’audience définis à l’aide de [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Il est conçu pour les architectes de solutions, les technologues marketing et les ingénieurs en implémentation qui ont besoin de comprendre toutes les approches d’implémentation viables, les considérations décisionnelles qui guident chaque choix et où trouver une documentation détaillée sur les [!DNL Adobe Experience League].

L’activation des messages sortants par lots est le modèle de campagne fondamental pour les messages sortants un-à-plusieurs. Il couvre l’ensemble du cycle de vie, de la définition de l’audience à la diffusion des messages et l’analyse des performances. Ce guide présente trois options d’implémentation (Campagne planifiée, Parcours déclenché par l’audience et Campagne déclenchée par l’API) et fournit des conseils de décision structurés pour sélectionner la bonne approche pour chaque cas d’utilisation.

Il fournit des options d’implémentation, une analyse comparative, des chemins de navigation dans l’interface utilisateur et des références à la documentation [!DNL Experience League].

## Présentation du cas d’utilisation

Les entreprises ont souvent besoin de diffuser un seul message à un segment d’audience connu à un moment spécifique ou en réponse à un événement système. Ce modèle répond à cette exigence en combinant l’évaluation des audiences dans [!DNL RT-CDP] avec la création de messages et l’exécution de campagnes dans [!DNL Journey Optimizer].

Le scénario commercial est simple : définissez qui doit recevoir le message, créez le contenu du message avec une personnalisation, liez l&#39;audience et le message dans une campagne ou un parcours et exécutez l&#39;envoi selon un planning, via la qualification de l&#39;audience ou via un déclencheur système. Le résultat est un message diffusé avec des rapports complets sur les mesures de diffusion, d’engagement et de conversion.

Ce modèle s’applique chaque fois qu’un objectif commercial peut être avancé en diffusant un seul message à une audience connue en une seule exécution. Elle se différencie des messages déclenchés par un événement, qui répondent aux événements comportementaux en temps réel, et des parcours orchestrés en plusieurs étapes, qui guident les profils à travers plusieurs points de contact au fil du temps. L’activation par lots est le modèle de campagne le plus simple et le point de départ le plus courant pour les cas d’utilisation de messagerie sortante.

## Objectifs commerciaux clés

Cette section identifie les principaux objectifs commerciaux pris en charge par l&#39;activation des messages sortants par lots.

### Augmenter l’engagement des e-mails et des campagnes

**Description :** améliorer les taux d’ouverture, les taux de clics publicitaires et la réponse globale de la campagne par le biais d’un contenu et d’un ciblage optimisés.

**KPI :** taux d’ouverture, d’engagement, de conversion

### Augmenter le chiffre d’affaires et les ventes

**Description :** stimuler la croissance du chiffre d’affaires de premier plan grâce à des canaux numériques, des campagnes et des parcours client optimisés.

**KPI : Taux de conversion**, Chiffre d’affaires incrémentiel, Valeur de commande moyenne

**Objectif commercial associé :** [Augmenter le chiffre d’affaires et les ventes](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Rationaliser l’exécution des campagnes

**Description :** réduire le temps de création de la campagne et simplifier la diffusion de campagnes multicanaux par le biais de modèles, d’une automatisation et de processus normalisés.

**KPI :** % de vitesse de mise sur le marché, d’efficacité, d’exécution dans les délais

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent les applications courantes de l’activation des messages sortants par lots.

- **Annonce de vente ou explosion d’e-mail promotionnel** — Diffusez une offre promotionnelle à un segment de clients éligibles à une date planifiée
- **Notification push de lancement du produit** — Notifiez les clients intéressés par une nouvelle disponibilité du produit via push
- **Newsletter ou e-mail de résumé** — Diffusez des résumés de contenu périodiques aux audiences abonnées
- **Invitation à l’inscription à un événement** — Invitez des prospects qualifiés à des webinaires, des conférences ou des événements en personne
- **E-mail de rappel de renouvellement d’abonnement** — Rappeler aux clients dont la date de renouvellement approche de prendre des mesures
- **Notification de jalon du programme de fidélité** — Félicitez les membres qui atteignent les niveaux de fidélité ou les seuils de point
- **E-mail call-to-action spécifique** — Entraînez une action ciblée telle que la réalisation d’un achat, la mise à jour des préférences ou l’enregistrement à un programme
- **Campagne SMS pour la vente flash ou l’offre limitée dans le temps** — Envoyez des promotions urgentes et limitées dans le temps par SMS aux audiences inscrites

## Indicateurs clés de performance

Le tableau suivant définit les KPI utilisés pour mesurer l’efficacité des campagnes.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux De Diffusion | Pourcentage de messages envoyés avec succès aux destinataires | Livrés / Envoyés x 100 |
| Taux d’ouvertures | Pourcentage de messages diffusés ouverts par les destinataires | Ouvertures uniques/diffusées x 100 |
| Taux de clic publicitaire (CTR) | Pourcentage de messages diffusés sur lesquels un utilisateur a cliqué sur un lien | Clics uniques / Diffusés x 100 |
| Taux de clic-ouverture (CTOR) | Pourcentage de messages ouverts sur lesquels un utilisateur a cliqué sur un lien | Clics uniques / Ouvertures uniques x 100 |
| Taux de conversion | Pourcentage de destinataires ayant effectué l’action souhaitée | Conversions / Livrés x 100 |
| Taux de désabonnement | Pourcentage de destinataires s’étant désabonnés après réception du message | Désabonnements / Diffusés x 100 |
| Taux de rebond | Pourcentage de messages qui n’ont pas pu être diffusés | Rebonds / Envoyés x 100 |
| Recettes par e-mail envoyé | Chiffre d’affaires attribué à la campagne divisé par les messages envoyés | Chiffre d’affaires total/envoyé |

## Modèle de cas d’utilisation

**Activation des messages sortants par lots**

Évaluez une audience, puis diffusez un message sortant planifié (e-mail, SMS, notification push) à tous les profils admissibles dans une seule exécution par lots.

**Chaîne de fonctions :** évaluation d’audience > création de messages > exécution de campagne > reporting

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle.

- **[!DNL Adobe Journey Optimizer](AJO)** — Création de messages, configuration des canaux, exécution de campagnes, orchestration des parcours, expérimentation de contenu, règles de fréquence et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Évaluation de l’audience, consentement et application de la gouvernance
- **[!DNL Adobe Experience Platform](AEP)** — Banque de profils, service d’identités, schémas, jeux de données, collecte de données

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction Fondamentale | Etat | Éléments devant être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | AJO sandbox est configuré avec une configuration de canal active. Envoi du sous-domaine délégué, du groupe d’adresses IP affecté et du préchauffage d’adresses IP terminé. Rôles utilisateur dotés d’autorisations de création de campagnes/parcours affectés. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schéma de profil individuel XDM avec les attributs utilisés pour la segmentation et la personnalisation (par exemple, nom, e-mail, préférences, niveau). Schéma XDM ExperienceEvent capturant l’action de conversion cible (par exemple, `commerce.purchases`, `web.webInteraction`) pour le suivi des conversions post-campagne. Jeux de données activés pour le profil pour les deux schémas. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Supposé en place | Le balisage Web SDK ou Analytics sur la destination CTA doit être actif pour capturer les événements de conversion. Les pipelines d’ingestion par flux ou par lots pour les attributs de profil doivent être opérationnels. | [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configuration des identités et des profils | Supposé en place | Espaces de noms d’identité pour les e-mails (et les identifiants entre appareils) configurés. Attributs de profil requis pour la personnalisation mappés, ingérés et résolvables au moment de l’envoi. Politique de fusion configurée. | [présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | Audience cible définie dans RT-CDP à l’aide du créateur de segments ou de la composition de l’audience. Audience publiée et évaluée avec une population différente de zéro. Couvert dans la phase de mise en œuvre 1 via l’évaluation de l’audience RT-CDP. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Importance de la résolution | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés, tels que les jours depuis le dernier achat, le nombre de commandes de durée de vie ou le score d’engagement, améliorent la précision de l’audience et permettent une personnalisation des messages plus riche. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Des politiques de conservation des données (expiration) doivent être en place pour les jeux de données d’événements qui pilotent le suivi des conversions. Les champs de schéma de consentement doivent être configurés pour l’application d’opt-in/opt-out au niveau du canal. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les libellés de gouvernance des champs PII utilisés dans la personnalisation garantissent la conformité lors de l’activation. Empêche l’utilisation non autorisée de données de profil sensibles dans le contenu des messages ou les exportations d’audience. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Inclus | La surveillance des envois en temps réel fait partie de la phase de création de rapports . Les alertes au niveau de la plateforme sur les échecs d’ingestion ou l’utilisation des licences offrent une visibilité opérationnelle au-delà des mesures au niveau de la campagne. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Rapports et analyses | Inclus | Les rapports de campagne et de parcours sont traités dans la phase de création de rapports. Pour une analyse cross-canal plus approfondie, l’intégration de CJA fournit une analyse funnel, une modélisation d’attribution et une analyse des cohortes qui vont au-delà des rapports intégrés d’AJO. | [Présentation de ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de canal | Phase 2 : configuration des canaux | Configurer ou valider la surface de canal (e-mail, SMS ou notification push), y compris le sous-domaine, le groupe d’adresses IP, les paramètres de l’expéditeur et la liste de suppression |
| Création de messages | Phase 3 : création de messages | Créez du contenu de message à l’aide de modèles, du Designer d’e-mail, d’expressions de personnalisation, de blocs de contenu conditionnel et de fragments de contenu |
| Exécution de la campagne | Phase 4 : création de campagne ou de Parcours | Créer, configurer et activer une campagne planifiée ou déclenchée par une API qui lie l’audience, le message et le planning d’exécution |
| Expérimentation de contenu | Phase 4 : création de campagne ou de Parcours | Configurez éventuellement des expériences A/B ou de contenu multivarié pour optimiser les performances des messages |
| Fréquence et règles métier | Phase 4 : création de campagne ou de Parcours | Vous pouvez éventuellement appliquer des règles de limitation de la fréquence pour empêcher la messagerie excessive dans les campagnes simultanées |
| Gestion des conflits et des priorités | Phase 4 : création de campagne ou de Parcours | Attribuez des scores de priorité et configurez la résolution des conflits lorsque plusieurs campagnes ciblent des audiences qui se chevauchent |
| Rapports et analyse des performances | Phase 5 : Rapports et analyse de la performance | Surveiller les mesures de diffusion au moyen de rapports dynamiques pendant l’exécution et analyser les performances des campagnes au moyen de rapports historiques une fois l’opération terminée |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 1 : évaluation de l’audience | Définissez des règles d’audience à l’aide du créateur de segments ou de la composition d’audience, sélectionnez la méthode d’évaluation (par lots, en flux continu ou Edge) et validez la population d’audience |
| Application du consentement et de la gouvernance | Phase 1 : évaluation de l’audience | Appliquez les préférences de consentement et les politiques d’utilisation des données pour vous assurer que seuls les profils consentants reçoivent le message de campagne |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] sandbox AJO est configuré et actif
- [ ] Sous-domaine d&#39;envoi est délégué et vérifié (SPF, DKIM, DMARC configuré)
- [ ] groupe d’adresses IP est affecté et préchauffé pour le volume d’envoi en production
- [ ] Il existe au moins une surface de canal active (e-mail, SMS ou notification push)
- [ ] Les comptes utilisateur disposent des autorisations de création de campagnes/parcours et de contenu
- [ ] schéma de profil XDM comprend les attributs nécessaires à la segmentation de l’audience et à la personnalisation des messages
- [ ] schéma d’événement XDM capture les événements de conversion pour le suivi post-campagne
- [ ] données de profil sont ingérées et unifiées via Identity Service
- [ ] balisage Web SDK ou Analytics est actif sur la page de destination CTA pour capturer les événements de conversion
- [ ] champs Consentement sont renseignés sur les profils pour le canal de messagerie cible
- [ ] Les ressources de contenu (images, logos, directives de la marque) sont disponibles pour la conception des messages

## Options de mise en œuvre

Cette section décrit trois options d’implémentation pour l’activation des messages sortants par lots, ainsi qu’une comparaison et des conseils de décision.

### Option A : Campagne planifiée (envoi par lots unique)

**Idéal pour** envois ancrés dans une date : annonces de vente, lancements de produits, délais d’enregistrement des événements, rappels de renouvellement, bulletins d’information et tout envoi dont la date d’exécution est connue à l’avance.

**Fonctionnement :**

Une campagne planifiée est la variante la plus simple de la messagerie sortante par lots. Le marketeur définit l’audience cible, crée le contenu du message, définit une date et une heure d’envoi et active la campagne. Au moment de l’exécution planifiée, AJO évalue l’audience pour déterminer la population éligible actuelle, puis diffuse le message à tous les profils qualifiants dans un seul lot.

La configuration complète se produit dans l’interface des campagnes AJO : il n’y a pas de zone de travail de parcours, pas de logique de branchement et pas d’étapes d’attente. Cela rend les campagnes planifiées les plus rapides à configurer et les plus faciles à gérer. La campagne peut être définie pour une exécution immédiate, une date/heure ultérieure spécifique ou un planning récurrent (quotidien, hebdomadaire, mensuel).

**Considérations principales :**

- L’audience est évaluée au moment de l’exécution, de sorte que les profils qui sont qualifiés entre la planification et l’exécution soient inclus
- Aucune logique d’embranchement, d’attente ou de condition n’est disponible - le message est diffusé à tous les profils admissibles
- Prend en charge l’expérimentation de contenu (tests A/B) directement dans la configuration de la campagne
- Les propriétés de la campagne incluent un score de priorité pour la résolution des conflits avec d’autres campagnes

**Avantages :**

- Configuration la plus simple avec le moins de surcharge
- Délai de lancement le plus rapide pour des envois par lots simples
- Prise en charge intégrée des plannings de périodicité
- Expérimentation de contenu prise en charge en mode natif
- Actualisation de l’audience réévaluée au moment de l’exécution

**Limitations :**

- Aucune étape d’attente, condition ou embranchement avant la diffusion
- Impossible de réagir au comportement du profil entre la planification et l’exécution
- Action de message unique uniquement — pas de séquences multipoint
- Modification impossible une fois activé (doit être dupliqué et modifié)

**Experience League:**

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B : parcours déclenché par l’audience

**Idéal pour** envois axés sur le comportement : notifications de panier abandonné, rappels d’expiration d’essai, célébrations jalonnées, sensibilisation basée sur les qualifications et tout envoi dont le déclencheur est la qualification d’audience ou un événement métier plutôt qu’une date de calendrier.

**Fonctionnement :**

Un parcours déclenché par une audience utilise la zone de travail du parcours pour diffuser un message lorsqu’un profil est qualifié pour une audience définie ou déclenche un événement de qualification. L’entrée par parcours est déclenchée par les modifications d’appartenance à l’audience (les profils entrant dans l’audience) plutôt que par un planning fixe. La zone de travail de parcours permet des étapes d’attente facultatives, des branches de condition et une logique de suppression avant l’action du message, offrant ainsi plus de flexibilité qu’une campagne planifiée.

Le parcours est configuré dans l’interface AJO Parcours à l’aide de l’événement d’entrée Lecture d’audience . Lorsque les profils sont qualifiés pour l’audience, ils entrent dans le parcours et parcourent les nœuds de la zone de travail. Une implémentation simple peut contenir un seul nœud d’action d’e-mail, ce qui la rend fonctionnellement similaire à une campagne planifiée, mais avec un timing d’entrée basé sur la qualification de l’audience. Des implémentations plus complexes peuvent ajouter des nœuds d’attente (par exemple, attendre 24 heures après la qualification), des nœuds de condition (par exemple, vérifier si le profil a ouvert un e-mail précédent) ou une logique de suppression avant la diffusion du message.

**Considérations principales :**

- L’entrée de parcours est déclenchée par la qualification de l’audience, et non par une date calendaire
- La zone de travail de parcours prend en charge les nœuds d’attente, de condition et de partage pour la logique de pré-diffusion
- Les règles de rentrée du parcours contrôlent si les profils peuvent entrer plusieurs fois dans le parcours
- Les paramètres d’arbitrage de parcours déterminent le comportement lorsqu’un profil se trouve déjà dans un parcours concurrent

**Avantages :**

- Planning d’entrée flexible basé sur la qualification de l’audience plutôt que sur un planning fixe
- Les nœuds d’attente et de condition autorisent la logique de pré-diffusion (par exemple, retard, vérification, suppression).
- Les contrôles de rentrée empêchent les envois en double au même profil
- Peut être étendu à un parcours à plusieurs étapes si le cas d’utilisation évolue
- Prise en charge des rapports au niveau du parcours avec des mesures d’entrée, de sortie et au niveau du nœud

**Limitations :**

- Surcharge de configuration plus importante qu’une campagne planifiée
- La zone de travail de parcours ajoute de la complexité, même pour les cas d’utilisation à message unique
- Le parcours doit être publié et ne peut pas être modifié en direct (une nouvelle version doit être créée)
- La limitation des entrées peut limiter le nombre de profils qui entrent dans une fenêtre temporelle

**Experience League:**

- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Lecture du parcours d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Option C : campagne déclenchée par API

**Idéal pour** envois déclenchés par le système : confirmation de commande avec contenu de montée en gamme, suivi de la résolution des tickets d’assistance, notifications transactionnelles avec contenu marketing et tout envoi dont l’événement déclencheur provient d’un système externe à un moment spécifique.

**Fonctionnement :**

Une campagne déclenchée par API est activée via un appel API REST au moment où un événement système déclencheur se produit. La campagne est préconfigurée dans AJO avec le contenu du message et les paramètres du canal, mais au lieu de lier une audience prédéfinie, l’appel API spécifie les profils des destinataires et peut transmettre des données contextuelles qui renseignent les paramètres de message dynamique.

Cette variante est idéale lorsque la durée d’envoi est déterminée par un système externe (par exemple, un système de gestion des commandes, un workflow CRM ou une plateforme d’assistance) plutôt que par une évaluation de l’audience ou un planning de calendrier. Les données contextuelles transmises dans la payload de déclenchement de l’API, telles que les détails de commande, les numéros de ticket ou les noms de produit, peuvent personnaliser le contenu du message à l’aide d’attributs contextuels non stockés sur le profil.

**Considérations principales :**

- Aucune audience préliée n’est requise ; les destinataires sont spécifiés dans la requête de déclenchement de l’API
- Les données contextuelles dans la payload du déclencheur permettent une personnalisation dynamique au-delà des attributs de profil
- La campagne doit être de type « déclenchée par API » et doit être activée avant de pouvoir recevoir des requêtes de déclenchement
- Chaque requête de déclencheur d’API prend en charge jusqu’à 20 destinataires de profil
- L’évaluation de l’audience (phase 1) peut être ignorée, car les destinataires proviennent de l’appel API

**Avantages :**

- Déclenchement en temps réel depuis des systèmes externes au moment de l&#39;événement
- Personnalisation contextuelle avec des données non stockées sur le profil (détails de commande, informations sur le ticket)
- Pas de frais généraux d’évaluation d’audience : les destinataires sont directement spécifiés
- Prend en charge les messages hybrides transactionnels et marketing

**Limitations :**

- Nécessite une intégration système externe pour envoyer le déclencheur API
- Maximum de 20 destinataires par requête de déclencheur d’API
- Aucune évaluation d&#39;audience intégrée : le système appelant doit déterminer les destinataires
- Plus grande complexité technique en raison des exigences d’intégration des API
- L’expérimentation de contenu n’est pas prise en charge pour les campagnes déclenchées par API

**Experience League:**

- [Campagnes déclenchées par API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Déclenchement de campagnes à l’aide d’API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : Campagne Planifiée | Option B : Parcours Déclenché Par L’Audience | Option C : Campagne déclenchée par l’API |
| --- | --- | --- | --- |
| Idéal pour | Envois ancrés dans la date (promotions, lancements, newsletters) | Envois basés sur le comportement (événements de qualification, jalons) | Envois déclenchés par le système (confirmations de commande, transactionnels) |
| Complexité | Faible | Moyenne | Medium-Grand |
| Type de déclencheur | Date/heure du calendrier ou planning récurrent | Qualification de l’audience ou événement métier | Appel API du système externe |
| Logique de pré-diffusion | Aucune | Attente, condition, nœuds partagés disponibles | Aucun (logique dans le système appelant) |
| Liaison d’audience | Audience RT-CDP prédéfinie | Audience RT-CDP prédéfinie | Destinataires spécifiés dans la payload de l&#39;API |
| Données contextuelles | Attributs de profil uniquement | Attributs de profil uniquement | Attributs de profil + données de payload d’API |
| Expérimentation de contenu | Pris en charge | Pris en charge (sur l’action de message) | Non pris en charge |
| Capping de la fréquence | Pris en charge | Pris en charge | Pris en charge |
| Contrôle de rentrée | S.O. (exécution unique) | Règles de rentrée configurables | S.O. (par demande) |
| Interface de configuration | Campagnes AJO | AJO Parcours | Campagnes AJO + système externe |
| Requiert | Audience, surface de canal, message | Audience, surface de canal, message, zone de travail de parcours | Surface de canal, message, intégration d’API |

### Choisir la bonne option

Utilisez le flux de décision suivant pour sélectionner l’option d’implémentation appropriée :

1. **L’envoi est-il déclenché par un événement système externe (par exemple, commande passée, ticket résolu) ?** Si oui, choisissez **Option C : Campagne déclenchée par l’API**. Il s’agit de la seule option qui prend en charge les déclencheurs déclenchés par le système avec des données de payload contextuelles.

2. **L’envoi est-il ancré à une date de calendrier spécifique ou à une planification récurrente ?** Si oui, choisissez **Option A : Campagne planifiée**. Il s’agit de la configuration la plus simple et la plus rapide pour les envois pilotés par la date.

3. **L’envoi doit-il réagir à la qualification de l’audience ou nécessite-t-il une logique de pré-diffusion (attente, condition, suppression) ?** Si oui, choisissez **Option B : Parcours déclenché par l’audience**. La zone de travail de parcours offre la flexibilité nécessaire pour une logique de décision d’entrée et de pré-diffusion axée sur le comportement.

4. **L’envoi d’une diffusion simple à une audience connue sans aucune exigence spécifique de durée ou de logique ?** Choisissez **Option A : Campagne planifiée** pour la surcharge de configuration la plus faible.

## Phases de mise en œuvre

Cette section décrit en détail chaque phase de mise en œuvre, y compris les points de décision et les conseils spécifiques aux options.

### Phase 1 : évaluation de l’audience

**Fonction d’application :** RT-CDP : évaluation de l’audience

Cette phase définit et évalue le segment d’audience cible qui recevra le message de la campagne. Il détermine les profils qui remplissent les critères de l’envoi en fonction des attributs de profil, des signaux de comportement et des règles de suppression.

>[!NOTE]
>Pour l’option C (campagne déclenchée par l’API), cette phase peut être ignorée si les destinataires sont entièrement spécifiés dans la payload du déclencheur d’API. Cependant, même les campagnes déclenchées par API bénéficient d’une audience de suppression pour filtrer les profils qui ne doivent pas recevoir de messages.

#### Décision : critères d’audience

Quelles conditions définissent l’audience cible ? Quelles règles de suppression doivent exclure les profils ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Audience basée sur les attributs de profil | L’audience cible est définie par des attributs démographiques, de préférence ou de statut | Plus simple à construire ; prend en charge toutes les méthodes d’évaluation |
| Audience basée sur un événement comportemental | L’audience cible est définie par les actions entreprises (ou non) dans une fenêtre temporelle | Nécessite l’ingestion des données d’événement ; les règles de fenêtre temporelle peuvent limiter l’éligibilité du streaming |
| Composition de l’audience (audience dérivée) | L’audience cible nécessite des opérations de classement, de partage, d’exclusion ou d’enrichissement sur plusieurs audiences sources | Évaluation plus puissante, mais par lots uniquement ; limitée à 10 compositions par sandbox |

#### Décision : méthode d&#39;évaluation

À quelle vitesse l’audience doit-elle être mise à jour pour refléter les nouveaux profils admissibles ou disqualifiés ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Évaluation par lots | Campagnes planifiées dans lesquelles l’actualisation de l’audience au cours de la journée est acceptable ; audiences importantes et complexes | Valeur par défaut pour la plupart des types de segment ; traite selon un planning quotidien ou à la demande ; prend en charge toutes les fonctions de règle de segment |
| Évaluation en flux continu | Parcours déclenchés par une audience dans lesquels les profils doivent entrer en temps quasi réel lorsqu’ils remplissent les critères | Automatique pour les expressions de règle de segment éligibles ; tous les types de segment ne sont pas qualifiés pour la diffusion en continu ; latence en temps quasi réel (secondes à minutes) |
| Évaluation Edge | Non standard pour ce modèle (utilisé pour la personnalisation de la même page) | Prise en charge limitée des règles de segment ; latence en millisecondes ; pertinent uniquement si combiné avec des modèles de personnalisation web |

#### Décision : politique de fusion

Quelle politique de fusion l’audience doit-elle utiliser pour résoudre les fragments de profil ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Politique de fusion par défaut (horodatage ordonné) | Les plus courants pour les cas d’utilisation de campagnes par lots | La dernière valeur d’attribut est acceptée ; standard pour la messagerie sortante |
| Politique de fusion personnalisée (priorité du jeu de données) | Lorsqu’une source de données spécifique doit être prioritaire pour les attributs clés | Utile lorsque les données CRM doivent remplacer les données collectées sur le web pour certains champs |

#### Navigation dans l’interface utilisateur

Client > Audiences > Créer une audience > Créer une règle

#### Détails de configuration clés

- Définissez l’audience à l’aide du créateur de segments avec des règles de segment pour les attributs de profil, les événements comportementaux et l’appartenance à un segment
- Appliquez des règles de suppression pour exclure les profils qui ont déjà été convertis, qui ont reçu récemment un message similaire ou qui se sont désinscrits
- Vérifiez que l’audience a une population différente de zéro avant de continuer
- Pour les campagnes par lots, assurez-vous qu’un planning d’évaluation de segment est actif ou déclenchez une évaluation à la demande
- Confirmer les champs de consentement (`consents.marketing.email.val`, `consents.marketing.sms.val`, etc.) sont renseignées et appliquées ;

#### Là où les options divergent

**Pour L’Option A (Campagne Planifiée) :**

L’évaluation par lots est typique. L’audience est réévaluée au moment de l’exécution de la campagne, de sorte que la population éligible la plus récente est ciblée. Définissez l’audience et vérifiez sa population, puis passez à la création de la campagne.

**Pour L’Option B (Parcours Déclenché Par L’Audience) :**

L’évaluation par flux est préférable pour que les profils rejoignent le parcours lorsqu’ils remplissent les critères. Assurez-vous que l’expression de la règle de segment est éligible à la diffusion en continu (déclencheurs d’événement simples, comparaisons d’attributs, fenêtres de temps limitées). Configurez l’audience et vérifiez que la qualification du streaming est active.

**Pour l’option C (campagne déclenchée par l’API) :**

L’évaluation de l’audience peut être complètement ignorée. Si vous utilisez cette option, créez une audience de suppression pour filtrer les profils qui ne doivent pas recevoir le message (par exemple, ceux qui ont récemment été désabonnés, ceux qui ont déjà été convertis). Le système appelant détermine les destinataires principaux.

#### Documentation Experience League

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2 : configuration du canal

**Fonction d’application :** AJO : Configuration de canal

Cette phase valide ou crée la surface de canal (préréglage) qui définit l’infrastructure d’envoi du message (sous-domaine, groupe d’adresses IP, identité de l’expéditeur, adresse de réponse et paramètres de désabonnement). Une surface de canal valide doit exister avant que le contenu du message puisse être créé ou que les campagnes puissent être activées.

#### Décision : canal cible

Quel canal de messagerie diffuse le message de la campagne ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail | La plupart des types de campagne : newsletters, promotions, notifications, renouvellements | Nécessite un sous-domaine délégué, un pool d’adresses IP préchauffé, une identité d’expéditeur et une configuration de désabonnement |
| SMS | Messages urgents ou brefs — ventes flash, rappels de rendez-vous, codes OTP | Nécessite des informations d’identification de fournisseur de SMS (Sinch, Twilio ou Infobip) ; coût plus élevé par message ; exigences de consentement plus strictes |
| Notification push | Audiences mobiles : mises à jour d’applications, offres basées sur la localisation, annonces de fonctionnalités in-app | Nécessite des informations d’identification APNs (iOS) et/ou FCM (Android) ; l’application doit être installée avec les autorisations push accordées |

#### Décision : sélection de la surface de canal

Une surface de canal appropriée existe-t-elle déjà dans le sandbox ou devez-vous en créer une nouvelle ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Réutiliser une surface existante | Une surface active vérifiée correspond au sous-domaine, à l’identité de l’expéditeur et au type de canal requis | Chemin le plus rapide ; aucune configuration DNS ou de préchauffage nécessaire |
| Créer une nouvelle surface | Aucune exigence de correspondance de surface existante n’est requise ou un nouveau sous-domaine/identité d’expéditeur est nécessaire | Nécessite la délégation de sous-domaines, la vérification DNS, l’affectation de groupes d’adresses IP et potentiellement le préchauffage d’adresses IP (2 à 4 semaines pour les nouvelles adresses IP) |

#### Décision : gestion du désabonnement

Comment le processus d’opt-out doit-il être géré sur la surface du canal ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| En-tête list-unsubscribe en un clic | Standard pour tous les emails marketing ; requis par les principaux FAI (Gmail, Yahoo) pour la délivrabilité | Ajoute un en-tête de désabonnement mailto: ou basé sur une URL que les FAI affichent sous la forme d’un bouton « Se désabonner » |
| Lien de désabonnement dans le corps de l’e-mail | Requis comme solution de secours pour les clients de messagerie qui ne prennent pas en charge les en-têtes list-unsubscribe | Insérez un lien de désabonnement dans le pied de page de l’e-mail à côté de l’en-tête list-unsubscribe |
| Les deux (recommandé) | Bonne pratique pour tous les e-mails marketing | Couverture de conformité maximale et meilleur profil de délivrabilité |

#### Navigation dans l’interface utilisateur

Administration > Canaux > Surfaces de canal > Créer une surface (ou sélectionner existante)

#### Détails de configuration clés

- Pour l’e-mail : liez le sous-domaine d’envoi, le groupe d’adresses IP, le nom, l’adresse e-mail, l’adresse de réponse et l’adresse en Cci (si une copie d’audit est requise)
- Pour les SMS : configurer les informations d’identification du fournisseur SMS et les paramètres de code court ou long
- Pour les notifications push : configurez les identifiants APNs et/ou FCM avec le certificat ou la clé de serveur de l’application
- Vérifiez que la surface de canal affiche le statut « Actif » avant de continuer
- Vérifiez que les enregistrements DNS (SPF, DKIM, DMARC) sont correctement configurés pour le sous-domaine d’envoi
- Consultez la liste de suppression pour les entrées obsolètes ; nettoyez avant l’activation

#### Documentation Experience League

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Phase 3 : création du message

**Fonction d’application :** AJO : création de messages

Cette phase crée le contenu du message qui sera diffusé à l’audience. Elle comprend la sélection ou la création d’un modèle de contenu, la conception de la disposition du message, l’ajout d’une personnalisation à l’aide d’attributs de profil, la configuration de blocs de contenu conditionnel pour des variations spécifiques à l’audience, la création de fragments de contenu réutilisables et la prévisualisation/test du message avec des profils types.

#### Décision : approche du contenu

Comment le contenu du message doit-il être créé ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Commencer à partir d’un modèle existant | Il existe des modèles approuvés par la marque qui correspondent au type de message (promotionnel, transactionnel, newsletter). | Chemin de création le plus rapide ; garantit la cohérence de la marque ; les modèles sont spécifiques au sandbox |
| Créer en partant de zéro | Il n’existe aucun modèle approprié ou le message nécessite une disposition unique | Plus de flexibilité mais plus d’effort ; envisagez l’enregistrement comme modèle de réutilisation |
| Importer HTML | La conception du message a été créée en externe (dans un outil de conception, par exemple) et HTML est prêt pour l’importation | Préserve la conception externe ; des ajustements peuvent s’avérer nécessaires pour les jetons de compatibilité et de personnalisation AJO |

#### Décision : profondeur du Personalization

Quels attributs de profil doivent personnaliser le message et des blocs de contenu conditionnel sont-ils nécessaires ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Personnalisation de base (nom, salutations) | Campagnes simples où un contenu générique avec une formule de salutation personnalisée est suffisant | Effort faible ; risque minimal de problèmes de rendu ; utilise des attributs de profil standard |
| Personnalisation basée sur les attributs | Le contenu du message varie en fonction des attributs de profil (niveau, préférence, emplacement) | Nécessite des chemins XDM vérifiés ; testez-les avec plusieurs profils pour vous assurer que toutes les variations s’affichent correctement. |
| Blocs de contenu conditionnel | Différentes sections de contenu doivent être présentées à différents segments d’audience dans le même message | Création plus complexe ; chaque condition nécessite une version de secours par défaut ; tester toutes les permutations |
| Personnalisation contextuelle (option C uniquement) | Les campagnes déclenchées par API doivent effectuer le rendu des données transmises dans la payload de déclencheur (détails de commande, informations de ticket) | Les attributs contextuels ne sont pas stockés sur le profil ; ils définissent des espaces réservés dans le message et mappent vers les champs de payload |

#### Décision : stratégie de fragment

Les blocs de contenu partagés doivent-ils être créés en tant que fragments réutilisables ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Fragments réutilisables | Les en-têtes, pieds de page, clauses de non-responsabilité ou blocs de désabonnement sont partagés dans plusieurs campagnes | Les modifications apportées à un fragment se propagent à tous les messages qui y font référence (actif et brouillon) ; 30 fragments au maximum par message |
| Contenu intégré | Message ponctuel sans éléments partagés sur les autres campagnes | Plus simple pour le contenu à usage unique ; aucun risque de propagation |

#### Navigation dans l’interface utilisateur

Campagnes > Sélectionner une campagne > Modifier le contenu > Designer d’e-mail (ou éditeur de SMS/Push)

#### Détails de configuration clés

- Concevez la disposition du message à l’aide des composants de contenu glissés-déposés (texte, image, bouton, séparateur, colonnes).
- Définissez les propriétés d’en-tête des e-mails : objet, texte pré-en-tête et surface expéditeur
- Insérer des expressions de personnalisation à l’aide de la syntaxe Handlebars (par exemple, `{{profile.person.name.firstName}}`)
- Configuration des fonctions d&#39;assistance pour le formatage (date, nombre, manipulation de chaîne)
- Ajoutez des règles de contenu conditionnel pour afficher un contenu différent en fonction des attributs de profil ou de l’appartenance à un segment
- Configurer le contenu de secours par défaut lorsqu’aucune condition n’est remplie
- Pour les SMS, composer le corps du message en respectant les considérations relatives aux limites de caractères
- Pour les notifications push, configurez le titre, le corps, l’image et l’action (lien profond ou URL).
- Prévisualiser le message avec des profils types pour vérifier le rendu de la personnalisation
- Envoyer des BAT aux parties prenantes internes pour révision
- Test du rendu sur les clients de messagerie à l&#39;aide de la fonctionnalité de rendu des e-mails

#### Documentation Experience League

- [Créer un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utiliser les composants de contenu Designer d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Envoyer des BAT par e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendu des emails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [Créer un SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Concevoir une notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Phase 4 : création de la campagne ou du parcours

**Fonction applicative :** AJO : Exécution de la campagne (options A et C) ou AJO : Journey Orchestration (option B)

Cette phase crée la campagne ou le parcours qui lie l’audience, le message et le mécanisme d’exécution en une unité livrable. C’est là que les trois options de mise en œuvre divergent le plus.

#### Décision : expérimentation de contenu

La campagne doit-elle inclure un test A/B ou une expérience multivariée pour optimiser les performances des messages ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Aucune expérience | Variante de message unique avec un degré élevé de confiance dans l’efficacité du contenu | Configuration la plus simple ; activation la plus rapide |
| Test A/B (2 variantes) | Test des objets, des CTA ou des mises en page de contenu avec une hypothèse claire | Fractionner le trafic 50/50 ou avec une attribution pondérée ; nécessite une taille d’audience suffisante pour la signification statistique |
| Test multivarié (3+ variantes) | Test simultané de plusieurs éléments de contenu | Nécessite de plus grandes audiences, une durée plus longue pour atteindre le seuil de confiance et un maximum de 10 traitements par expérience |

#### Décision : capping de la fréquence

Cette campagne doit-elle respecter les règles de limitation de la fréquence globale pour éviter le sur-message ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Application de règles de fréquence | Campaign fait partie d&#39;un programme de messagerie plus large avec plusieurs envois simultanés | Évite la fatigue des clients ; les profils qui dépassent la limite sont supprimés de la diffusion |
| Exemption de la limitation | La campagne est urgente ou transactionnelle et doit atteindre tous les profils qualifiés, quel que soit l’historique des messages récents | Utilisez avec parcimonie ; exempter des campagnes des règles de fréquence risque d’envoyer trop de messages |

#### Décision : score de priorité

Quel niveau de priorité cette campagne doit-elle avoir par rapport aux autres campagnes actives ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Haute priorité (75-100) | Campagnes critiques : lancements de produits majeurs, offres à durée limitée, notifications réglementaires | Est prioritaire sur les campagnes à priorité inférieure en cas de conflit |
| Priorité de Medium (25-74) | Campagnes marketing standard : newsletters, campagnes d’engagement, promotions générales | Équilibré par rapport aux autres campagnes ; peut être supprimé en cas de conflit entre des campagnes de priorité supérieure |
| Priorité faible (0-24) | Envois attrayants : mises à jour informatives, promotions secondaires | Sera supprimé en faveur des campagnes de priorité supérieure |

#### Là où les options divergent

**Pour L’Option A (Campagne Planifiée) :**

**Navigation dans l’interface utilisateur :** Campagnes > Créer une campagne > Planifié > Marketing

1. Créer une campagne marketing planifiée
2. Sélectionner l’audience cible à partir du sélecteur d’audience
3. Sélectionnez la surface de canal et liez le contenu du message créé
4. Configurez le planning d’exécution : immédiat, à une date/heure spécifique ou récurrent
5. Activez éventuellement l’expérimentation de contenu et définissez des variantes de traitement
6. Configurez éventuellement le capping de la fréquence et le score de priorité
7. Vérifier la configuration complète de la campagne
8. Activer la campagne

**Pour L’Option B (Parcours Déclenché Par L’Audience) :**

**Navigation dans l’interface utilisateur :** Parcours > Créer un Parcours

1. Création d’un parcours avec un événement d’entrée « Lecture d’audience »
2. Sélectionner l’audience cible comme source d’entrée
3. Configurer des règles de rentrée (autoriser une rentrée, une entrée unique ou une rentrée après la période d’attente)
4. Vous pouvez éventuellement ajouter des nœuds d’attente (par exemple, attendre 24 heures après la qualification)
5. Vous pouvez éventuellement ajouter des nœuds de condition (par exemple, vérifier si le profil répond à des critères supplémentaires)
6. Ajoutez le nœud d’action du message et sélectionnez la surface de canal et le contenu créé
7. Configurer des critères de sortie (par exemple, conversions de profils, désabonnements de profils)
8. Vous pouvez éventuellement activer l’expérimentation de contenu sur l’action de message
9. Révision et publication du parcours

**Pour l’option C (campagne déclenchée par l’API) :**

**Navigation dans l’interface utilisateur :** Campagnes > Créer une campagne > Déclenché par l’API

1. Créer une campagne déclenchée par API
2. Sélectionnez la surface de canal et liez le contenu du message créé
3. Configurez les jetons de personnalisation contextuelle pour les données qui seront transmises dans la payload du déclencheur d’API
4. Vérification et activation de la campagne
5. Notez l’identifiant de campagne à utiliser dans l’intégration du déclencheur d’API du système externe
6. Le système appelant envoie des requêtes de déclenchement au point d’entrée de la campagne avec les profils des destinataires et les données contextuelles

#### Documentation Experience League

- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Campagnes déclenchées par API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Lecture du parcours d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 5 : analyse des rapports et des performances

**Fonction d’application :** AJO : Rapports et analyse des performances

Cette phase surveille les mesures de diffusion pendant l’exécution via des rapports dynamiques et analyse les performances des campagnes une fois l’opération terminée à l’aide de rapports historiques. Vous pouvez éventuellement configurer l’intégration de CJA pour une analyse cross-canal plus approfondie.

#### Décision : méthode de création de rapports

Quel niveau de reporting est nécessaire pour cette campagne ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rapports natifs AJO uniquement | Les mesures de diffusion et d’engagement standard sont suffisantes (envoi, diffusion, ouvertures, clics, bounces). | Aucune configuration supplémentaire ; les rapports sont intégrés dans l’interface utilisateur de campagne/de parcours |
| Rapports natifs AJO + analyse CJA | Une analyse de l’impact cross-canal, une modélisation d’attribution ou une analyse funnel sont nécessaires au-delà des mesures de diffusion | Nécessite une connexion CJA et une vue de données liées aux jeux de données AJO ; fournit une fonctionnalité d’analyse plus approfondie |
| Rapports programmatiques de CJA | Des tableaux de bord automatisés ou une diffusion de rapports planifiée sont nécessaires pour les parties prenantes | Nécessite l’intégration de l’API de création de rapports de CJA ; utile pour les tableaux de bord exécutifs et les résumés récurrents des performances |

#### Décision : suivi des conversions

Comment le succès de la campagne sera-t-il mesuré au-delà des mesures de diffusion et d’engagement ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Aucun suivi des conversions | L’objectif de la campagne est la sensibilisation ou l’engagement (ouvertures, clics) sans action en aval spécifique | Plus simple : aucun suivi d’événement supplémentaire requis |
| Tracking des conversions web | Campaign CTA fournit des liens vers une page web sur laquelle sont suivis les événements de conversion (achat, enregistrement, envoi de formulaire) | Nécessite le balisage Web SDK ou Analytics sur la page de destination ; les événements doivent être capturés dans les jeux de données AEP |
| Événement de conversion personnalisé | Le succès d’une campagne est mesuré par un événement spécifique à l’entreprise qui n’est pas capturé sur le web (par exemple, un achat en magasin, une interaction avec un centre d’appels) | Nécessite que l’événement personnalisé soit ingéré dans AEP et inclus dans les jeux de données de rapports |

#### Navigation dans l’interface utilisateur

- Rapports dynamiques : Campagnes > Sélectionner une campagne > Rapport dynamique (ou Parcours > Sélectionner un parcours > Rapport dynamique)
- Rapports historiques : Campagnes > Sélectionner une campagne > Rapport à toute heure (ou Parcours > Sélectionner un parcours > Rapport à toute heure)

#### Détails de configuration clés

- Accéder aux rapports dynamiques pendant l’exécution de la campagne pour surveiller la diffusion et l’engagement en temps réel
- Vérifier les mesures clés : Envoyé, Diffusé, Bounces, Ouvertures, Clics, Désabonnements (e-mail); Envoyé, Diffusé, Clics, Erreurs (SMS); Envoyé, Diffusé, Ouvertures, Actions (push)
- Une fois la campagne terminée, accédez aux rapports historiques (à toute heure) pour une analyse complète
- Analysez le funnel de diffusion : Ciblé > Envoyé > Diffusé > Ouvertures > Clics
- Examinez les raisons des erreurs et des exclusions pour identifier les problèmes de diffusion
- Si l’expérimentation de contenu a été activée, passez en revue les résultats de l’expérience et attendez le degré de confiance statistique avant de désigner une expérience gagnante
- Pour l’intégration de CJA, vérifiez que la vue de données AJO inclut les jeux de données AJO appropriés (jeu de données d’événement de retour de message, jeu de données d’événement d’expérience de suivi d’e-mail)

#### Documentation Experience League

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage.

### Mécanismes de sécurisation et limites

- Maximum de 500 campagnes actives en direct par sandbox — [Mécanismes de sécurisation ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum de 10 surfaces de canal par type de canal par sandbox
- Les campagnes déclenchées par API prennent en charge jusqu’à 20 destinataires de profil par requête de déclencheur
- Les campagnes ne peuvent pas être modifiées une fois activées. Dupliquez et modifiez à la place
- Les rapports dynamiques sont actualisés toutes les 60 secondes et affichent les dernières 24 heures de données
- Le remplissage complet des rapports historiques peut prendre jusqu’à 2 heures après la fin de la campagne
- Maximum de 10 traitements (variantes) par expérience de contenu
- Maximum de 10 configurations de limitation par sandbox
- Maximum de 30 fragments de contenu par message
- Une taille d’e-mail maximale de 100 Ko est recommandée pour une délivrabilité optimale
- Les plans de préchauffage des adresses IP doivent augmenter progressivement le volume sur 2 à 4 semaines pour les nouvelles adresses IP
- Les entrées de la liste de suppression sont conservées pendant une période configurable (14 jours par défaut pour les soft bounces)

### Pièges courants

- **Envoi avant la fin du préchauffage des adresses IP :** les nouvelles adresses IP qui envoient immédiatement des volumes élevés seront marquées par les FAI, ce qui entraînera une mauvaise délivrabilité et un éventuel blacklistage. Exécutez toujours un plan de préchauffage d’adresses IP avant que la production n’envoie de nouvelles adresses IP.

- **Ne pas tester la personnalisation sur plusieurs profils :** les jetons Personalization qui fonctionnent pour un profil de test peuvent échouer pour d’autres si le chemin XDM référencé n’existe pas ou est nul sur certains profils. Prévisualisez toujours avec plusieurs profils de test qui représentent différents niveaux de complétion des données.

- **Révision de la liste de suppression ignorée :** les entrées de la liste de suppression obsolètes peuvent bloquer la diffusion vers des adresses valides, tandis que les entrées manquantes peuvent entraîner une diffusion vers des adresses non valides qui génèrent des bounces. Consultez et nettoyez la liste de suppression avant les campagnes majeures.

- **Ignorer le capping de la fréquence pour les campagnes promotionnelles :** l’envoi d’une campagne promotionnelle sans capping de la fréquence pendant que d’autres campagnes sont également actives peut entraîner la réception de plusieurs messages en peu de temps, des désabonnements et des plaintes pour spam.

- **Planification de campagnes sans vérification de la population de l’audience :** l’activation d’une campagne avant de confirmer que l’audience cible a une population évaluée différente de zéro n’entraîne la diffusion d’aucun message. Vérifiez toujours la taille de l’audience avant l’activation.

- **Utilisation de l’évaluation par lots pour les parcours déclenchés par une audience :** si le parcours utilise une entrée Lecture d’audience avec l’évaluation par lots, les profils ne seront pas intégrés en temps quasi réel. Utilisez l’évaluation en flux continu pour l’audience lorsqu’une entrée de parcours en temps quasi réel est requise.

- **Ne pas configurer l’application du consentement :** l’envoi de messages à des profils sans consentement marketing valide enfreint les réglementations et endommage la réputation de délivrabilité. Assurez-vous que les champs de consentement sont renseignés et appliqués au niveau de la surface de canal.

### Bonnes pratiques

- Commencez avec l’option A (Campagne planifiée) pour les cas d’utilisation de diffusion simples et passez à l’option B (Parcours déclenché par l’audience) uniquement lorsque la logique de prédiffusion ou le minutage basé sur le comportement est nécessaire
- Pour une conformité maximale, incluez toujours un en-tête list-unsubscribe en un clic et un lien de désabonnement dans le corps de l’e-mail
- Créez des fragments de contenu réutilisables pour les en-têtes, pieds de page et clauses légales afin d’assurer la cohérence entre les campagnes
- Définissez des règles de limitation de la fréquence avant d’activer les campagnes pour éviter la surmessagerie pour les envois simultanés
- Utilisez l’expérimentation de contenu pour optimiser les objets et les CTA, en commençant par les tests A/B avant de passer à des expériences multivariées
- Attribuez des scores de priorité à toutes les campagnes actives pour garantir une résolution cohérente des conflits
- Planifiez l’évaluation des audiences par lots à terminer avant l’heure d’exécution de la campagne pour vous assurer de disposer de nouvelles données d’audience
- Envoyez des e-mails de BAT et utilisez la fonctionnalité de rendu des e-mails pour vérifier que le message s’affiche correctement sur les clients de messagerie avant activation
- Surveillez le rapport dynamique immédiatement après l’activation de la campagne pour détecter rapidement les problèmes de diffusion
- Archivez les configurations de campagne et les résultats des expériences pour une référence et une optimisation continue futures

### Décisions de compromis

Les compromis suivants doivent être évalués lors des choix de mise en œuvre.

#### Simplicité et flexibilité

Les campagnes planifiées (option A) offrent la configuration la plus simple, mais aucune logique de pré-diffusion. Les parcours déclenchés par l’audience (option B) fournissent une logique de pré-diffusion, mais ajoutent une complexité de configuration.

- **L’option A est privilégiée :** vitesse de lancement, simplicité opérationnelle, libre-service du spécialiste marketing.
- **L’option B privilégie :** ciblage comportemental, suppression conditionnelle, extensibilité aux parcours à plusieurs étapes.
- **Recommandation :** commencez par l’option A pour les envois simples. Passez à l’option B uniquement lorsque le cas d’utilisation nécessite réellement une logique d’attente, de condition ou de branchement avant la diffusion. Évitez d’utiliser la zone de travail de parcours pour les envois par lots simples qui ne bénéficient pas des fonctionnalités d’orchestration.

#### Actualisation de l’audience par rapport au coût d’évaluation

L’évaluation par flux fournit des mises à jour d’audience en temps quasi réel, mais présente des restrictions de règles de segment. L’évaluation par lots prend en charge toutes les fonctions de règle de segment, mais effectue une évaluation selon un calendrier quotidien.

- **Favoris de la diffusion en continu :** ponctualité, précision basée sur le comportement, entrée de parcours déclenchée par l’audience.
- **Favoris par lot :** logique d’audience complexe, populations importantes, frais d’évaluation inférieurs
- **Recommandation :** utilisez l’évaluation par lots pour les campagnes planifiées (option A) où la fraîcheur quotidienne est suffisante. Utilisez l’évaluation par flux pour les parcours déclenchés par une audience (option B) où les profils doivent entrer car ils remplissent les critères. Si l’expression de la règle de segment d’audience n’est pas éligible à la diffusion en continu, restructurez les règles ou acceptez la latence au niveau du lot.

#### Profondeur de Personalization par rapport à la complexité de création

Une personnalisation plus approfondie (blocs de contenu conditionnel, sections dynamiques) améliore l’engagement, mais augmente les efforts de création et de test.

- **Favoris de la personnalisation profonde :** taux d’engagement plus élevés, expérience client plus pertinente, meilleure conversion
- **Favoris de la personnalisation simple :** délai de lancement plus rapide, charge de test plus faible, risque d’erreur de rendu réduit
- **Recommandation :** commencez par une personnalisation de base (prénom, catégorie de produits appropriée) et créez un calque dans des blocs de contenu conditionnel en fonction des gains de performances mesurés. Testez toujours toutes les variations de contenu sur plusieurs profils de test avant l’activation.

#### Contrôle de la fréquence par rapport à la portée des messages

Le capping de la fréquence stricte empêche le sur-message, mais peut supprimer la diffusion de la campagne vers les profils qui ont reçu récemment d’autres messages.

- **Favoris de limitation stricte :** qualité de l’expérience client, taux de désabonnement plus faibles, réputation de la marque
- **Favoris de limitation assouplis :** portée maximale des messages, nombre total d’impressions plus élevé, couverture de la campagne
- **Recommandation :** toujours activer le capping de la fréquence pour les campagnes marketing. Définissez des limites spécifiques au canal (par exemple, 3 à 5 e-mails par semaine, 1 à 2 SMS par semaine). N’exemptez que les messages réellement critiques ou transactionnels des règles de limitation.

## Documentation connexe

Cette section fournit des liens complets vers [!DNL Experience League] documentation organisée par rubrique.

### Campagnes

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Campagnes déclenchées par API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Parcours

- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Lecture du parcours d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Utiliser les composants de contenu Designer d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Importer ou coder du contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Gestion de contenu

- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Envoyer des BAT par e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Rendu des emails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Gestion des fréquences et des conflits

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Création de rapports

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Modélisation des données et identité

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutoriels et prise en main

- [Prise en main de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Créer votre première campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Créer votre premier parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
