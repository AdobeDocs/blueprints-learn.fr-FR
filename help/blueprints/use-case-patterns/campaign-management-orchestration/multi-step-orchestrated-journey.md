---
title: Parcours Orchestré À Plusieurs Étapes
description: Découvrez comment guider un profil à travers un parcours d’embranchement multipoint avec des attentes, des conditions et plusieurs actions de message au fil du temps.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8211'
ht-degree: 1%

---

# Parcours orchestré à plusieurs étapes

Ce guide fournit un plan d’implémentation complet pour la création de parcours orchestrés à plusieurs étapes à l’aide de [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Real-Time Customer Data Platform] (RT-CDP). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin d’orchestrer des parcours clients multi-touch et avec embranchement qui diffusent plusieurs messages au fil du temps.

Il présente toutes les options d’implémentation viables, les considérations relatives aux décisions à chaque point de configuration et des liens vers la documentation [!DNL Adobe Experience League]. Utilisez ce guide pour planifier, configurer et valider la mise en œuvre de votre parcours à plusieurs étapes.

## Présentation du cas d’utilisation

Les parcours orchestrés en plusieurs étapes traitent des scénarios commerciaux où un seul message est insuffisant pour atteindre le résultat souhaité par le client. Au lieu d’un envoi unique, le parcours guide chaque profil à travers une séquence de points de contact (e-mails, SMS, notifications push ou messages in-app) espacés sur plusieurs jours ou semaines, avec une logique d’embranchement qui adapte le chemin en fonction des attributs de profil, des signaux comportementaux ou des données d’événement.

Ces parcours constituent le modèle de campagne le plus complexe d’AJO. Ils combinent une entrée basée sur une audience ou sur un événement avec une zone de travail de nœuds d’action (messages), de nœuds de condition (logique de branchement), de nœuds d’attente (retards) et de critères de sortie (événements de conversion ou délais). Chaque profil progresse dans le parcours indépendamment, à son propre rythme, recevant du contenu contextuellement pertinent à chaque étape.

Ce modèle intègre les modèles plus simples : activation des messages sortants par lots pour les campagnes à envoi unique et messagerie déclenchée par événement pour les réponses à événement unique. Utilisez ce modèle lorsque le cas d’utilisation nécessite d’entretenir un profil par le biais de plusieurs interactions au fil du temps.

>[!NOTE]
>Si votre parcours nécessite une sélection dynamique de l’offre, du contenu ou du canal optimal à des points de décision individuels, consultez la section [parcours cross-canal avec prise de décision](cross-channel-journey-with-decisioning.md). Ce modèle l’étend à l’intégration d’AJO Decisioning.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Amélioration de la fidélisation client

Maintenez l’engagement et le renouvellement des clients existants grâce à des expériences axées sur la valeur et à l’entretien continu des relations.

**KPI : rétention** valeur client sur toute la durée de vie, engagement

[En savoir plus sur l’amélioration de la fidélisation des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Améliorer l’intégration des clients

Accélérez la rentabilité pour les nouveaux clients grâce à des expériences de bienvenue et des parcours d’activation rationalisés et personnalisés.

**KPI : engagement** rétention et taux de conversion

[En savoir plus sur l’amélioration de l’intégration des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Réengager les clients inactifs

Récupérez les clients inactifs ou obsolètes avec des campagnes de réactivation ciblées basées sur des signaux comportementaux.

**KPI : engagement** rétention et taux de conversion

[En savoir plus sur l’amélioration de la fidélisation des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Récupérer les paniers et les parcours abandonnés

Réengagez les utilisateurs qui ont abandonné lors des flux d’achat, de demande ou d’inscription avec des suivis personnalisés et opportuns.

**KPI :** taux de conversion, revenu incrémentiel, engagement

[En savoir plus sur la récupération des paniers et des parcours abandonnés](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent les applications courantes du modèle de parcours orchestré à plusieurs étapes.

- **Série d’intégration des clients** — E-mail de bienvenue, suivi d’une formation sur les fonctionnalités, puis d’une invite d’activation au cours des 14 premiers jours suivant l’enregistrement
- **Campagne de réengagement au goutte-à-goutte** — Un e-mail de rappel, puis une offre incitative, puis un avis final pour les clients non engagés depuis plus de 3 semaines
- parcours jalon de fidélité&#x200B;**— Notification de mise à niveau du niveau, suivie d’une offre exclusive, puis d’un rappel de renouvellement à l’approche de l’anniversaire de l’abonnement**
- **Séquence de reconquête** : e-mail « Vous nous manquez », puis offre de remise par e-mail, puis dernier rappel par SMS pour les acheteurs obsolètes
- parcours d’adoption du produit **— Bienvenue d’essai, conseils d’utilisation, puis une invite de mise à niveau au fur et à mesure de la période d’essai**
- **Séquence de renouvellement d’abonnement** — Avis de 30 jours, rappel de 7 jours, puis message de jour d’expiration pour les renouvellements d’abonnement à venir
- **Formation après achat** - e-mail de remerciement, guide d’utilisation, recommandation de vente croisée, puis demande de révision 30 jours après l’achat

## Indicateurs clés de performance

Utilisez les KPI suivants pour mesurer l’efficacité de votre mise en œuvre de parcours orchestré à plusieurs étapes.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’achèvement du parcours | Pourcentage de profils qui terminent le parcours complet sans sortie anticipée | Rapport de parcours : sorti (terminé) / Entré |
| Taux de conversion de l’étape | Pourcentage de profils qui passent d’une étape à l’autre | Mesures par nœud dans le rapport de parcours |
| Taux d’engagement du canal | Taux d’ouverture, taux de clics publicitaires et taux de réponse à chaque point de contact | Mesures de diffusion et d’engagement par message |
| Taux de conversion des critères de sortie | Pourcentage de profils qui déclenchent l’événement de sortie (par exemple, achat, inscription) avant la temporisation du parcours | Nombre d’accès aux critères de sortie / Total saisi |
| Délai jusqu’à la conversion | Durée moyenne entre l’entrée sur le parcours et l’événement correspondant au critère de sortie | Parcours analytics : horodatage d’entrée en date et heure de l’événement de conversion |
| Taux de restitution des parcours | Pourcentage de profils qui cessent de s’engager à chaque étape (analyse des abandons) | Visualisation des abandons CJA à travers les étapes de parcours |
| Taux de rétention/réengagement | Pourcentage de profils ciblés qui reviennent au statut actif | Analyse comportementale post-parcours dans CJA |

## Modèle de cas d’utilisation

**Parcours orchestré en plusieurs étapes**

Guidez un profil à travers un parcours multi-touch d’embranchement avec des attentes, des conditions et plusieurs actions de message au fil du temps.

**Chaîne de fonctions :** Évaluation d’audience > Exécution de Parcours (multi-nœud) > Branchement de condition > Diffusion de message (xN) > Critères de sortie > Rapports

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer](AJO)** : moteur d’orchestration des Parcours, création de messages, configuration des canaux, expérimentation de contenu, gestion des fréquences et des conflits, et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Évaluation et définition de l’audience pour les audiences d’entrée de parcours, les données de profil pour la personnalisation et l’embranchement des conditions
- **[!DNL Adobe Experience Platform](AEP)** — Banque de profils, service d’identités, ingestion des données d’événement et infrastructure de données de base

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Sandbox AJO avec autorisations de création et de publication de parcours. Les surfaces de tous les canaux utilisés dans le parcours doivent être configurées. Les utilisateurs doivent disposer des rôles appropriés (marketeur, responsable de Parcours) avec des autorisations de parcours et de campagne. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schéma de profil XDM avec les attributs utilisés pour l’embranchement et la personnalisation des conditions sur plusieurs messages (par exemple, le niveau de fidélité, l’intérêt du produit, le score d’engagement). Les schémas d’événement d’expérience pour les événements de conversion qui génèrent les critères de sortie et l’évaluation des conditions (par exemple, les événements d’achat, les envois de formulaire). | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Supposé en place | La diffusion en continu d’événements doit être active si les critères ou conditions de sortie dépendent d’événements en temps réel (par exemple, un événement d’achat pour quitter le parcours). Ingestion par lots pour les attributs de profil utilisés dans l’embranchement. Web SDK ou API côté serveur pour la collecte d’événements comportementaux. | [Présentation de l’ingestion par flux](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview), [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configuration des identités et des profils | Supposé en place | Les profils doivent pouvoir être résolus sur tous les canaux utilisés dans le parcours (e-mail, SMS, notification push). Les identités entre appareils doivent être configurées si le parcours s’étend sur des points de contact web et mobiles. La politique de fusion doit être configurée pour le sandbox. | [présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | L’audience d’entrée doit être définie pour les parcours lus par l’audience. Les segments peuvent également être utilisés dans les nœuds de condition pour l’embranchement. La méthode d’évaluation (par lots ou par flux) doit correspondre aux exigences d’entrée du parcours. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que les scores d’engagement, les jours depuis la dernière activité ou la valeur d’achat de durée de vie améliorent la logique d’embranchement des conditions, permettant des décisions de chemin de parcours plus intelligentes. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | La conservation des données des événements de parcours doit être configurée avec des politiques d’expiration des jeux de données pour gérer le stockage et respecter les réglementations de conservation des données. L’application du consentement garantit que seuls les profils inscrits reçoivent des messages à chaque point de contact de canal. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Expiration des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les étiquettes de gouvernance assurent une personnalisation conforme sur plusieurs points de contact de message, ce qui est particulièrement important lorsque les parcours utilisent des informations d’identification personnelles ou des données sensibles pour la personnalisation sur plusieurs canaux. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Inclus | Alertes de surveillance de l’exécution des parcours sur les échecs de traitement, les goulets d’étranglement des entrées de profil et les problèmes de diffusion. Essentiel pour les parcours de production où les retards ou les échecs ont une incidence sur l’expérience client. | [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Le funnel CJA et l’analyse des abandons sur l’ensemble du parcours fournissent des rapports insight plus détaillés que les rapports natifs AJO seuls. Permet l’analyse de conversion étape par étape, la comparaison de cohortes et l’optimisation des parcours. | [Présentation de ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de canal | Phase 1 : configuration du canal | Configurer des surfaces de canal (e-mail, SMS, notification push) pour chaque point de contact de messagerie du parcours |
| Création de messages | Phase 2 : création de contenu de message | Créez du contenu de message avec de la personnalisation, du contenu dynamique et des modèles pour chaque nœud d’action de parcours |
| Journey Orchestration | Phase 3 : conception et activation du Parcours | Concevoir la zone de travail de parcours à plusieurs étapes avec des nœuds d’entrée, d’action, de condition, d’attente et de sortie ; tester et publier |
| Fréquence et règles métier | Phase 4 : gouvernance et optimisation | Configurez les limites de fréquence pour éviter la surmessagerie entre les points de contact de parcours et d’autres campagnes simultanées |
| Gestion des conflits et des priorités | Phase 4 : gouvernance et optimisation | Attribuez des scores de priorité et configurez la détection des conflits pour les parcours en concurrence avec d’autres communications actives |
| Expérimentation de contenu | Phase 4 : gouvernance et optimisation | Exécutez des tests A/B sur le contenu des messages dans les nœuds d’action de parcours pour optimiser les performances. |
| Rapports et analyse des performances | Phase 5 : Rapports et surveillance | Surveiller l’exécution des parcours, les mesures de diffusion par étape et les performances de l’engagement |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 1 : configuration du canal (prérequis) | Définir et évaluer l’audience d’entrée pour les parcours lus par l’audience ; définir des audiences sous condition pour l’embranchement |
| Application du consentement et de la gouvernance | Phase 4 : gouvernance et optimisation | Application des préférences de consentement et des politiques d’utilisation des données aux actions de message de parcours |

## Conditions préalables

Remplissez les conditions préalables suivantes avant de commencer l’implémentation.

- [ ] sandbox AJO est configuré avec des autorisations de création et de publication de parcours
- [ ] Au moins une surface de canal (e-mail, SMS ou notification push) est configurée et active
- [ ] schéma de profil comprend les attributs nécessaires à l’embranchement et à la personnalisation des conditions
- [ ] schéma d’événement d’expérience est configuré pour les événements de conversion utilisés dans les critères de sortie
- [ La diffusion en continu d’événements ] est active pour les événements en temps réel utilisés dans les critères de sortie ou les entrées déclenchées par un événement
- [ ] Les espaces de noms d’identité et les politiques de fusion sont configurés pour la résolution de profils cross-canal
- [ ] Les ressources de contenu (images, copie, CTA) sont préparées pour chaque point de contact de message
- [ ]’audience d’entrée est définie et évaluée (pour les parcours lus par l’audience)
- [ ] schéma d’événement de déclenchement est configuré (pour les parcours déclenchés par un événement)
- [ ] profils de test sont disponibles pour la validation du mode test de parcours
- [ ] Liste de suppression est examinée et mise à jour pour tous les canaux utilisés

## Options de mise en œuvre

Examinez les options suivantes pour déterminer la meilleure approche pour votre parcours orchestré à plusieurs étapes.

### Option A : parcours orchestré lu par l’audience

**Idéal pour** séquences de maturation temporelles au cours desquelles une audience connue entre dans le parcours et progresse par points de contact planifiés (séries d’intégration, séquences de renouvellement, gouttes-à-goutte de réengagement, parcours jalonnés de fidélité).

**Fonctionnement :**

Une audience est lue à l’entrée du parcours, soit comme une lecture unique, soit selon un planning récurrent. Tous les profils admissibles accèdent au parcours simultanément, puis progressent dans la zone de travail à leur propre rythme, selon les durées d’attente et les évaluations de condition. Le chemin de chaque profil à travers le parcours est indépendant : certains peuvent utiliser la branche « engagée » tandis que d’autres utilisent la branche « non engagée » en fonction de leur comportement ou de leurs attributs.

L’audience est évaluée au moment de l’exécution de l’activité Lecture d’audience . Pour les parcours récurrents, l’audience est réévaluée à chaque périodicité et de nouveaux profils admissibles entrent dans le parcours tandis que les profils déjà dans le parcours continuent leur chemin. Cette approche fournit un calendrier d’entrée prévisible et est bien adaptée aux programmes de cycle de vie planifiés.

**Considérations principales :**

- L’audience doit être définie et évaluée avant l’activation du parcours
- La lecture récurrente permet à de nouveaux qualificateurs d’entrer sur chaque cycle
- Les profils du parcours ne sont pas relus ; seuls de nouveaux qualificateurs sont saisis lors des lectures suivantes
- Les étapes d’attente ont une durée minimale d’une heure pour les parcours lus par l’audience

**Avantages :**

- Calendrier d&#39;entrée prévisible aligné sur les calendriers d&#39;activité
- Prend en charge les grands volumes d’audience (jusqu’à 20 000 profils par seconde avec ralentissement par défaut)
- Simplicité de test et de surveillance avec des populations d’audiences connues
- Peut être planifié pour une entrée récurrente (quotidienne, hebdomadaire, mensuelle)

**Limitations :**

- L’entrée est basée sur des lots et non en temps réel - les profils entrent au moment de la lecture planifiée, et non lorsqu’ils remplissent les critères
- Ne convient pas aux séquences déclenchées par un comportement qui nécessitent une réponse immédiate
- Les modifications d’audience entre les lectures ne sont pas reflétées pour les profils déjà dans le parcours

**Experience League:**

- [Activité Lecture d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option B : parcours orchestré déclenché par un événement

**Idéal pour :** séquences déclenchées par le comportement lorsqu’un événement en temps réel commence le parcours ; escalade de l’abandon de panier, suivi après achat, parcours de fidélité déclenché par un jalon, séquences d’activation d’essai.

**Fonctionnement :**

Un événement unitaire (par exemple, un achat, un abandon de panier, un envoi de formulaire ou une installation d’application) déclenche la saisie du parcours pour des profils individuels en temps réel. Lorsque l’événement est reçu, le profil entre dans le parcours, puis progresse dans la séquence de points de contact avec des conditions, des attentes et des embranchements. Cette approche associe l’immédiateté de la messagerie déclenchée par un événement à l’orchestration en plusieurs étapes d’un parcours complet.

L’événement déclencheur doit être configuré en tant qu’événement de parcours avec son schéma et ses conditions définis. Le parcours écoute l’événement en continu et saisit les profils un par un à mesure que les événements arrivent. Les nœuds de parcours suivants peuvent évaluer la réponse du profil afin de déterminer la branche à suivre.

**Considérations principales :**

- Nécessite la diffusion en continu d’événements en temps réel pour être actif
- Le schéma et les conditions des événements doivent être configurés précisément pour éviter les déclencheurs erronés
- Les règles de rentrée sont essentielles. Elles déterminent si un profil peut entrer à nouveau en cas de déclenchement de l’événement
- Prend en charge jusqu’à 5 000 événements par seconde par sandbox

**Avantages :**

- Entrée en temps réel basée sur le comportement du client — hautement contextuelle
- Chaque profil entre indépendamment lorsque l’événement se produit, et non selon un planning
- Ajustement naturel aux séquences de réponse comportementale (abandon de panier, post-achat)
- Peut être combiné avec les données de profil pour un embranchement personnalisé après l’entrée

**Limitations :**

- Nécessite la mise en place d’une infrastructure d’événements de streaming
- Complexité accrue de la configuration et du test des schémas d’événements
- Chaque événement entre dans un profil ; il n’est pas adapté à l’activation d’audiences en bloc
- Le débogage nécessite le suivi des parcours de profils individuels

**Experience League:**

- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### Option C : parcours orchestré multicanal

**Idéal pour** séquences cross-canal qui utilisent différents canaux à chaque point de contact (e-mail, SMS, escalade des notifications push) ou e-mail et messagerie complémentaire in-app. Peut utiliser une entrée lue par l’audience ou déclenchée par un événement.

**Fonctionnement :**

Cette option étend l’option A ou l’option B en incorporant plusieurs canaux de messagerie dans le même parcours. Chaque nœud d’action du parcours peut cibler un canal différent (e-mail, SMS, notification push, in-app ou web), ce qui nécessite une surface de canal distincte pour chacun. Le concepteur de parcours sélectionne le canal approprié à chaque étape et active des modèles d’escalade (par exemple, d’abord les e-mails, puis les SMS si aucun engagement) ou des modèles complémentaires (par exemple, les e-mails avec renforcement in-app).

Les parcours cross-canal nécessitent des surfaces de canal pour chaque canal utilisé et doivent tenir compte de la personnalisation spécifique au canal, des limites de caractères et des exigences d’accord préalable. Les nœuds de condition peuvent vérifier l’engagement avec les messages précédents (par exemple, « e-mail ouvert ? ») comme condition de branche) pour déterminer le canal suivant.

**Considérations principales :**

- Nécessite des surfaces de canal actives pour chaque canal utilisé dans le parcours
- Chaque canal possède différentes fonctionnalités de personnalisation et contraintes de contenu
- Le consentement doit être vérifié par canal - un profil peut être inscrit aux e-mails, mais pas aux SMS.
- Les limitations de fréquence spécifiques au canal doivent être configurées pour éviter la surmessagerie sur plusieurs canaux

**Avantages :**

- Optimise la portée en engageant les profils sur leurs canaux préférés
- Active les stratégies d’escalade pour les profils non réactifs
- Prise en charge de la messagerie complémentaire sur plusieurs canaux à des fins de renforcement
- Expérience client la plus sophistiquée possible

**Limitations :**

- Complexité d’implémentation maximale : configuration requise pour chaque canal
- Le contenu doit être créé pour chaque canal à chaque point de contact
- La gestion du consentement et des fréquences devient plus complexe sur l’ensemble des canaux
- Les tests nécessitent une validation sur toutes les surfaces de canal

**Experience League:**

- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : lecture de l’audience | Option B : Déclenché par un événement | Option C : multicanal |
| --- | --- | --- | --- |
| Idéal pour | Programmes de cycle de vie planifiés, série de cours | Séquences de réponse comportementale, abandon de panier | Escalade cross-canal, messagerie complémentaire |
| Planning d’entrée | Planifié (par lots) | Temps réel (piloté par les événements) | Planifié ou en temps réel |
| Complexité | Moyenne | Medium-Grand | Élevée |
| Volume d’entrée | Jusqu’à 20 000 profils/s | Jusqu’à 5 000 événements/s | Identique à la méthode de saisie sous-jacente |
| Portée du canal | Un ou plusieurs canaux | Un ou plusieurs canaux | Plusieurs canaux requis |
| Requiert | Audience définie, planning d’évaluation | Infrastructure d’événement de streaming | Surfaces de canal pour chaque canal |
| Réponse en temps réel | Non — saisie par lots | Oui - immédiat en cas d’événement | Dépend de la méthode d’entrée |

### Choisir la bonne option

Utilisez le flux de décision suivant pour sélectionner l’approche d’implémentation appropriée :

1. **Le parcours est-il initié par un comportement ou un événement client ?** Si oui, choisissez **Option B** (Déclenché par l’événement). Si le parcours est initié par une lecture d’audience planifiée, choisissez **Option A** (Lecture d’audience).

2. **Le parcours utilise-t-il plusieurs canaux de messagerie (e-mail ET SMS, par exemple) ?** Si oui, appliquez **Option C** (multicanal) en plus de votre choix de méthode d’entrée (A ou B). Si le parcours utilise un seul canal dans l’ensemble, les options A ou B seules sont suffisantes.

3. **Devez-vous passer à un autre canal en fonction de l’engagement ?** Si oui, choisissez **Option C** avec des nœuds de condition qui vérifient l’engagement avec les messages précédents et se connectent à des canaux alternatifs.

4. **L’audience est-elle connue à l’avance et traitée selon un planning ?** Si oui, choisissez **Option A**. Si les profils doivent entrer dans le parcours au moment où ils effectuent une action, choisissez **Option B**.

## Phases de mise en œuvre

Les phases suivantes décrivent l’implémentation de bout en bout d’un parcours orchestré à plusieurs étapes.

### Phase 1 : configurer des canaux et préparer les audiences

**Fonctions d’application :** AJO : Configuration de canal, RT-CDP : Évaluation d’audience

Avant de concevoir le parcours, toutes les surfaces de canal doivent être actives et l’audience d’entrée (pour l’option A) doit être définie et évaluée. Cette phase permet de s’assurer que l’infrastructure est prête pour la diffusion des messages.

#### Choix du type de canal pour chaque point de contact

Quels canaux de messagerie le parcours utilisera-t-il à chaque point de contact ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail uniquement | Le parcours communique exclusivement par e-mail (intégration, éducation) | Configuration la plus simple ; nécessite un sous-domaine de messagerie et un groupe d’adresses IP ; sujet à l’emplacement de la boîte de réception |
| SMS uniquement | Alertes sensibles à l’heure, rappels de rendez-vous | Nécessite des informations d&#39;identification de fournisseur SMS (Sinch, Twilio, Infobip) ; coût plus élevé par message ; règles d&#39;opt-out plus strictes |
| Notification push uniquement | Séquences d’engagement in-app pour les utilisateurs et utilisatrices mobiles | Nécessite des informations d’identification APNs/FCM ; l’application doit être installée pour les utilisateurs |
| Multicanal | Escalade ou messagerie complémentaire sur plusieurs canaux | Nécessite une surface de canal par canal ; plus complexe, mais portée la plus élevée |

#### Choix de la méthode d’évaluation de l’audience (option A)

À quelle vitesse les profils doivent-ils se qualifier pour l’audience d’entrée ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Évaluation par lots | L’audience est lue selon un calendrier (quotidien, hebdomadaire) ; aucune entrée en temps réel n’est nécessaire | Configuration simple ; audience évaluée avant lecture du parcours ; prend en charge des règles de segment complexes |
| Évaluation en flux continu | Les profils doivent être qualifiés en temps quasi réel à mesure que les attributs changent | L’expression de la règle de segment doit être éligible à la diffusion en continu ; qualification en temps quasi réel |

#### Choix de la méthode de délégation de sous-domaine (canal e-mail)

Comment le sous-domaine d’envoi d’e-mail doit-il être délégué à Adobe ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Délégation complète | Adobe gère les enregistrements DNS ; configuration la plus simple | Configuration la plus rapide : Adobe gère SPF, DKIM et DMARC. |
| Délégation CNAME | L’organisation conserve le contrôle du DNS | Nécessite l’implication de l’administrateur DNS ; les enregistrements CNAME doivent être configurés |

#### Navigation dans l’interface utilisateur

- Surfaces de canal : Administration > Canaux > Surfaces de canal > Créer une surface
- Sous-Domaines : Administration > Canaux > Sous-Domaines
- Configuration SMS : Administration > Canaux > Configuration SMS
- Configuration push : Administration > Canaux > Paramètres des notifications push
- Audiences : Client > Audiences > Créer une audience > Créer une règle

#### Détails de configuration clés

- Vérification du statut de préchauffage du groupe d’adresses IP pour les e-mails : les nouveaux groupes d’adresses IP nécessitent un plan de préchauffage progressif sur 2 à 4 semaines
- Pour les SMS, configurez les informations d’identification du fournisseur et vérifiez l’enregistrement du numéro expéditeur
- Pour les notifications push, chargez les certificats APNS et les clés de serveur FCM
- Définissez l’audience d’entrée à l’aide du créateur de segments avec des règles de segment couvrant la population cible
- Inclure les règles de suppression dans la définition de l’audience (exclure les personnes récemment converties et globalement désabonnées)

#### Là où les options divergent

**Pour L’Option A (Lecture D’Audience) :**
Définissez et évaluez l’audience de l’entrée. Vérifiez que l’audience a une population différente de zéro. Déterminez si le parcours utilisera un planning de lecture d’audience unique ou récurrente.

**Pour L’Option B (Déclenchée Par Un Événement) :**
Vérifiez que le schéma d’événement de déclenchement est configuré et que les événements sont diffusés en continu dans la plateforme. Aucune audience prédéfinie n’est requise ; les profils la saisissent individuellement à la réception de l’événement.

**Pour L’Option C (Multicanal) :**
Configurez les surfaces des canaux pour CHAQUE canal utilisé dans le parcours (e-mail, SMS, notification push, in-app). Vérifiez le statut du consentement par canal pour la population cible.

#### Documentation Experience League

- [Configurer des surfaces de canal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### Phase 2 : création du contenu du message

**Fonction d’application :** AJO : création de messages

Créez le contenu du message pour chaque point de contact du parcours. Chaque message peut avoir un contenu, une profondeur de personnalisation et un canal différents. Cette phase crée tout le contenu livrable que les nœuds d’action de parcours référenceront.

#### Choix de l’approche du contenu

Chaque message doit-il partir d’un modèle, être entièrement conçu ou importer HTML ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Modèle de contenu existant | Messages cohérents avec la marque et les dispositions établies | Plus rapide ; assure la conformité de la marque ; le modèle doit exister et correspondre au type de canal. |
| Créer en partant de zéro | Dispositions uniques et personnalisées pour chaque point de contact | Plus flexible ; durée de création plus longue ; utilisez le glisser-déposer Email Designer. |
| Importer HTML | HTML préconfiguré à partir d’outils de conception externes | Nécessite un HTML propre ; peut nécessiter un ajustement pour la réactivité |

#### Choix de la profondeur de personnalisation

Quel niveau de personnalisation chaque message doit-il inclure ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Insertion de jeton de base | Prénom, ville, attributs de profil simples | Faible complexité ; utilise la syntaxe Handlebars avec les chemins XDM |
| Blocs de contenu conditionnel | Contenu différent affiché en fonction du segment ou de l’attribut | Complexité de Medium ; nécessite des règles de contenu dynamique |
| Personnalisation parcours-contextuelle | Le contenu varie en fonction du chemin du parcours et des interactions précédentes | Complexité accrue ; utilise les variables contextuelles de parcours et les données d’événement |

#### Choix de la stratégie de fragment

Les blocs de contenu partagés (en-têtes, pieds de page, texte juridique) doivent-ils être créés en tant que fragments réutilisables ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Fragments réutilisables | Plusieurs messages partagent des éléments communs ; cohérence de la marque requise | Les modifications se propagent à tous les messages utilisant le fragment ; 30 fragments au maximum par message |
| Contenu intégré | Messages ponctuels avec mises en page uniques | Plus rapide pour le contenu à usage unique ; aucun avantage de cohérence entre les messages |

#### Navigation dans l’interface utilisateur

- Gestion de contenu > Modèles de contenu > Parcourir
- Designer d’e-mail (dans la campagne ou l’action de parcours)
- Gestion de contenu > Fragments > Créer un fragment

#### Détails de configuration clés

- Créer du contenu pour CHAQUE action de message du parcours : un parcours en 4 étapes peut nécessiter 4 conceptions de message distinctes
- Utilisez des expressions de personnalisation faisant référence à des chemins de profil XDM (par exemple, `{{profile.person.name.firstName}}`).
- Configurer des blocs de contenu dynamique pour les variations spécifiques au segment
- Prévisualiser chaque message avec des profils de test pour vérifier le rendu de la personnalisation
- Envoyer des BAT aux parties prenantes internes pour la révision du contenu
- Pour les SMS, respectez les limites de caractères (160 caractères pour l’encodage GSM standard)
- Pour les notifications push, configurez le titre, le corps, l’image et l’action de lien profond/URL

#### Documentation Experience League

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Créer un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Créer un SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Concevoir une notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### Phase 3 : conception et activation du parcours

**Fonction d’application :** AJO : Journey Orchestration

Concevez la zone de travail de parcours à plusieurs étapes, y compris le nœud d’entrée, les nœuds d’action (messages), les nœuds de condition (embranchement), les nœuds d’attente (retards) et les critères de sortie. Ensuite, effectuez des tests avec les profils de test et publiez.

#### Choisir le type d’entrée

Comment les profils doivent-ils entrer dans le parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Lecture d’audience | Séquences de maturation planifiées ; audience connue traitée par lots | Audience évaluée au moment de la lecture ; prend en charge les lectures uniques ou récurrentes ; jusqu’à 20 000 profils/s |
| Événement unitaire | Déclencheurs comportementaux en temps réel (achat, abandon de panier) | Entrée en temps réel ; nécessite la diffusion en continu d’événements ; jusqu’à 5 000 événements/s |
| Qualification De L’Audience | Entrée lorsqu’un profil entre ou quitte une audience en temps quasi réel | Évaluation en flux continu ; déclenchée par un changement d’appartenance à un segment |
| Événement métier | Événement à l’échelle de l’organisation qui déclenche le parcours pour une audience | Utile pour les lancements de produits, les événements météorologiques et les alertes système |

#### Décider de la politique de rentrée

Un profil peut-il rejoindre à nouveau le parcours une fois qu’il a terminé ou quitté ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Autoriser la rentrée (avec le temps de recharge) | Les profils peuvent avoir besoin de répéter le parcours (achats récurrents, réengagement saisonnier) | Recharge minimale de 5 minutes ; empêche les entrées en double dans la fenêtre de recharge |
| Pas de rentrée | Parcours ponctuels (intégration, événement de cycle de vie unique) | Le profil termine ou quitte le parcours et ne peut pas y revenir |

#### Déterminer les durées d’attente entre les points de contact

Combien de temps le parcours doit-il attendre entre chaque message ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Durée fixe (par exemple, 3 jours) | Fréquence cohérente, quel que soit le comportement du profil | Durée simple et prévisible ; 1 heure minimum pour les parcours lus par l’audience |
| Date/heure spécifique | Le message doit arriver à une heure précise (par exemple, la date de renouvellement) | Utilise l’attribut ou l’expression de profil pour déterminer la date/l’heure exacte |
| Expression personnalisée | Attente dynamique en fonction des données de profil ou du contexte du parcours | Plus flexible ; nécessite la création d’expressions. |

#### Choix des conditions d’embranchement

Quelles conditions déterminent le chemin d’accès d’un profil ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Vérification de l’attribut de profil | Branche basée sur le niveau de fidélité, l’intérêt du produit et la zone géographique | Utilise les données de profil disponibles au moment de l’évaluation |
| Vérification de l’appartenance à un segment | Branche selon que le profil appartient ou non à une audience spécifique | Nécessite de définir et d’évaluer l’audience |
| Vérification des données d’événement | Branche selon que le profil a effectué une action (e-mail ouvert, lien cliqué) | Évalue les données d’événement de portée parcours ; utile pour l’embranchement basé sur l’engagement |
| Partage en pourcentage | Répartition aléatoire des profils sur plusieurs chemins (pour les tests A/B ou les déploiements contrôlés) | N’utilise pas les données de profil ; affectation purement aléatoire |

#### Choix des critères de sortie

Quel événement ou condition entraîne la sortie anticipée d’un profil du parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Événement de conversion | Le profil effectue l’action souhaitée (achat, inscription, envoi de formulaire) | Nécessite la diffusion en continu d’événements ; critères de sortie les plus courants |
| Sortie de l’appartenance à une audience | Le profil quitte l’audience d’entrée ou rejoint une audience d’exclusion | Évalue en temps quasi réel les audiences en flux continu |
| Timeout | Parcours maximum atteint (91 jours maximum) | Filet de sécurité par défaut ; configurable dans les propriétés du parcours |
| Aucun critère de sortie | Profile complète naturellement l’ensemble du chemin du parcours | Plus simple : tous les profils traversent le parcours complet, sauf s’ils ont été supprimés manuellement |

#### Définir le délai d’expiration du parcours

Quelle est la durée maximale pendant laquelle un profil peut rester dans le parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| 91 jours (maximum) | Parcours de longue durée (renouvellement trimestriel, intégration étendue) | Maximum autorisé ; les profils toujours dans le parcours au moment de la temporisation sont automatiquement quittés. |
| Durée raccourcie personnalisée | Le parcours doit être effectué dans une fenêtre définie (7 jours, 14 jours, 30 jours) | Défini en fonction du cycle de vie naturel du cas d’utilisation |

#### Navigation dans l’interface utilisateur

- Créer un parcours : Parcours > Créer un Parcours
- Propriétés du parcours : canevas de Parcours > panneau Propriétés
- Nœud d’entrée : Zone de travail de Parcours > Faire glisser « Lecture d’audience » ou activité d’événement
- Nœuds d’action : zone de travail de Parcours > Action de canal de glisser (e-mail, SMS, notification push)
- Nœuds de condition : Parcours de la zone de travail > Faire glisser l’activité « Condition »
- Nœuds d’attente : Parcours de la zone de travail > Faire glisser l’activité « Attente »
- Critères de sortie : Propriétés du Parcours > Critères de sortie > Configurer
- Mode test : canevas de Parcours > Bouton bascule Mode test .
- Publication : zone de travail de Parcours > Publication

#### Détails de configuration clés

- Nommez le parcours avec une convention claire et descriptive (par exemple, « Onboarding_Series_Email_v1 »).
- Définir le fuseau horaire du parcours pour le traitement cohérent des étapes d’attente
- Configurez chaque nœud d’action avec la surface de canal appropriée et le lien vers le contenu du message créé
- Chaque branche doit se terminer par une activité Fin .
- Configurez les règles de rentrée appropriées au cas d’utilisation
- Utilisez le mode test avec des profils de test pour simuler le chemin de parcours complet avant la publication
- Vérifiez que les profils de test traversent les chemins prévus et reçoivent les messages corrects

#### Là où les options divergent

**Pour L’Option A (Lecture D’Audience) :**

- Faites glisser l’activité « Lecture d’audience » comme nœud d’entrée
- Sélection de l’audience cible définie à la phase 1
- Vous pouvez éventuellement configurer un planning de lecture récurrente (quotidien, hebdomadaire)
- Configurez le ralentissement du taux de lecture si la charge du système en aval pose problème.

**Pour L’Option B (Déclenchée Par Un Événement) :**

- Faites glisser l’événement déclencheur en tant que nœud d’entrée
- Configuration du schéma d&#39;événement et des conditions d&#39;entrée
- Définissez les règles de rentrée avec soin pour éviter les entrées en double d’événements répétés

**Pour L’Option C (Multicanal) :**

- Utiliser la méthode d’entrée des options A ou B
- À chaque nœud d’action, sélectionnez la surface de canal appropriée pour ce point de contact
- Ajoutez des nœuds de condition entre les canaux pour vérifier l’engagement (par exemple, « Le profil a-t-il ouvert l’e-mail ? ») et acheminer vers d’autres canaux

#### Documentation Experience League

- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Activité Lecture d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Activité de fin](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### Phase 4 : configuration de la gouvernance et de l’optimisation

**Fonctions d’application :** AJO : Fréquence et règles métier, AJO : Gestion des conflits et des priorités, AJO : Expérimentation de contenu, RT-CDP : Application du consentement et de la gouvernance

Appliquez des limites de fréquence pour éviter les messages excessifs, attribuez des scores de priorité pour la résolution de conflits avec d’autres communications actives, configurez éventuellement des tests A/B dans les messages de parcours et vérifiez l’application du consentement.

#### Choix de la configuration de la limitation de fréquence

Les messages de parcours doivent-ils respecter les limites de fréquence globales ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Application de règles de fréquence | Parcours fonctionne avec d’autres campagnes et parcours ; les profils ne doivent pas recevoir trop de messages | Les messages peuvent être supprimés si le profil a déjà atteint la limite d’autres communications |
| Exemption de la limitation | Les messages de parcours sont essentiels et doivent toujours être diffusés (transactionnel, réglementaire) | Utilisez avec parcimonie ; peut contribuer à la fatigue des messages en cas de surutilisation |

#### Déterminer l’attribution du score de priorité

Quel devrait être le rang de ce parcours par rapport aux autres campagnes et parcours actifs ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Haute priorité (70-100) | Les messages de parcours sont des communications relatives au cycle de vie critique (intégration, renouvellement) | Une priorité plus élevée gagne en cas de conflit avec d’autres communications |
| Priorité de Medium (30-69) | Les messages parcours sont importants, mais pas urgents (éducation) | Peuvent être supprimées par des communications de priorité supérieure |
| Priorité faible (0-29) | Les messages de parcours sont complémentaires ou promotionnels | Sera supprimé lors de la concurrence avec des messages de priorité supérieure |

#### Choix de l’expérimentation de contenu

Un message de parcours doit-il inclure un test A/B ou multivarié ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Oui — Test A/B | Optimisez les lignes d’objet, les CTA ou les mises en page de contenu à un point de contact spécifique | Nécessite un volume suffisant par variante pour une signification statistique ; 2 à 10 traitements pris en charge |
| Aucune expérimentation | Le contenu est finalisé ou le volume est trop faible pour des tests significatifs | Configuration plus simple ; aucun suivi de variante nécessaire |

#### Navigation dans l’interface utilisateur

- Règles de fréquence : Administration > Règles métier > Créer une règle
- Scores de priorité : propriétés du Parcours > Score de priorité
- Détection des conflits : Administration > Règles métier > Conflit et priorité
- Expérience de contenu : Zone de travail de Parcours > Activer/désactiver l’action de message > Expérience de contenu
- Politiques de consentement : Confidentialité > Politiques > Politiques de consentement

#### Détails de configuration clés

- Définissez des limitations de fréquence spécifiques au canal (par exemple, 3 e-mails max./semaine, 1 SMS max./jour, 2 notifications push max./jour).
- Attribuez une note de priorité au parcours (0-100) qui reflète son importance commerciale par rapport aux autres communications actives
- Examinez le panneau de détection des conflits pour identifier les campagnes ou les parcours qui se chevauchent
- Si vous exécutez une expérience de contenu, définissez des variantes de traitement, définissez l’affectation du trafic, choisissez la mesure de succès (ouvertures, clics ou conversions) et définissez le seuil de confiance (généralement 95 %)
- Vérifiez que l’application du consentement est active pour chaque canal utilisé dans le parcours

#### Documentation Experience League

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### Phase 5 : configuration des rapports et de la surveillance

**Fonctions d’application :** AJO : Rapports et analyse des performances, surveillance et observabilité, Rapports et analyses

Surveillez l’exécution du parcours pendant et après l’activation, examinez les mesures de diffusion et d’engagement par étape, configurez des alertes pour les échecs de traitement de parcours et, éventuellement, créez une analyse de l’espace de travail CJA pour une visualisation approfondie de la funnel et des abandons.

#### Choix de la méthode de création de rapports

Quels outils de création de rapports sont nécessaires pour ce parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rapports natifs AJO uniquement | La surveillance de base de la diffusion et de l’engagement est suffisante | Rapport dynamique (pendant l’exécution) et rapport à toute heure (après exécution) ; s’actualise toutes les 60 secondes pour le rapport dynamique |
| AJO + analyse CJA | Une analyse approfondie de funnel, des taux de conversion par étapes, une visualisation des abandons ou une comparaison entre parcours est nécessaire | Nécessite une connexion CJA et une vue de données liées aux jeux de données AJO ; la plus complète |
| CJA uniquement | L’entreprise utilise CJA comme principale plateforme d’analyse | Nécessite une configuration CJA ; les rapports natifs d’AJO restent disponibles en tant que sauvegarde. |

#### Choix de la configuration des alertes

Quelles défaillances de parcours devraient déclencher des alertes ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Parcours des alertes de traitement | Toujours recommandé pour les parcours de production | Alertes sur les échecs d’entrée de profil, les erreurs de nœud d’action et les blocages de parcours |
| Alertes d’échec de diffusion | Critique pour les parcours disposant de communications à forte valeur ajoutée | Alertes sur taux de rebond dépassant les seuils, diffusions en échec |

#### Navigation dans l’interface utilisateur

- Rapport dynamique sur les parcours : Parcours > Sélectionner un parcours > Rapport dynamique
- Rapport parcours à toute heure : Parcours > Sélectionner un parcours > Rapport À toute heure
- Alertes : Alertes > Règles d’alerte > Abonnement
- Espace de travail CJA : Projets > Créer un projet

#### Détails de configuration clés

- Accédez au rapport dynamique lors de l’exécution du parcours pour surveiller les entrées de profil, les sorties et les mesures de diffusion par étape en temps réel
- Une fois le parcours terminé (ou lorsqu’un nombre suffisant de données a été accumulé), consultez le rapport Toute l’heure pour une analyse complète
- Configurer des alertes de plateforme pour les échecs de traitement des parcours et les problèmes de diffusion
- Pour l’analyse CJA, assurez-vous que la connexion CJA inclut les jeux de données d’événement d’expérience AJO (commentaires des messages, suivi des e-mails, événements d’étape de Parcours)
- Créez un Workspace CJA avec :
   - Visualisation funnel affichant le nombre de profils à chaque étape du parcours
   - Visualisation des abandons pour identifier les points de dépôt
   - Calculs du taux de conversion des étapes
   - Analyse du délai de conversion
   - Répartition de l’engagement au niveau du canal (pour les parcours multicanaux)

#### Documentation Experience League

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considérations relatives à la mise en œuvre

Examinez les mécanismes de sécurisation, les pièges à éviter, les bonnes pratiques et les compromis suivants avant et pendant votre mise en œuvre.

### Mécanismes de sécurisation et limites

- Maximum de **500 parcours actifs** par sandbox — [Mécanismes de sécurisation Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- La durée maximale de **parcours est de 91 jours** (délai d’expiration global) : les profils toujours dans le parcours au moment de la temporisation sont automatiquement fermés
- Maximum de **50 activités** par zone de travail de parcours
- Lire les parcours d’audience traitant jusqu’à 20 000 profils **par seconde** (ralentissement par défaut)
- Les parcours d’événement unitaire prennent en charge jusqu’à 5 000 événements **par seconde** par sandbox
- Les étapes d’attente ont une **durée minimale de 1 heure** pour les parcours lus par l’audience
- Parcours **le minimum de refroidissement de rentrée est de 5 minutes**
- Maximum de **10 surfaces de canal par type de canal** par sandbox
- Taille maximale de l&#39;e-mail **100 Ko** recommandée pour une délivrabilité optimale
- Maximum de **30 fragments de contenu** par message
- Nombre maximal de traitements d’expérience de contenu **10** (variantes) par expérience
- Maximum de configurations de limitation **10** par sandbox
- Maximum de 4 000 définitions de segment **par sandbox**

### Pièges courants

- **Publication sans test :** utilisez toujours le mode test avec des profils de test pour valider le chemin d’accès complet au parcours avant la publication. Vérifiez que les profils traversent correctement les branches attendues, que les étapes d’attente avancent correctement et que les messages s’affichent correctement.
- **Activités de fin manquantes sur les branches :** chaque branche de parcours doit se terminer par une activité Fin . La publication du parcours échoue si une branche est laissée sans nœud de terminaison.
- **Conditions d’entrée trop générales :** une audience d’entrée ou une condition d’événement mal définie peut inonder le parcours de profils inattendus. Affinez les critères d’entrée avec des contrôles d’attributs et des règles de suppression spécifiques.
- **Règles de rentrée ignorées :** pour les parcours déclenchés par un événement, les profils peuvent déclencher l’événement de rentrée plusieurs fois. Sans une configuration de rentrée appropriée (refuser la rentrée ou temps mort), les profils peuvent s’accumuler dans le parcours, provoquant des messages en double.
- **Confusion du fuseau horaire de l’étape d’attente :** les durées d’attente sont traitées en UTC. Définissez explicitement le fuseau horaire du parcours dans les propriétés du parcours pour vous assurer que les étapes d’attente avancent à l’heure locale prévue.
- **Modification d’un parcours dynamique :** les parcours dynamiques ne peuvent pas être modifiés directement. Pour apporter des modifications, dupliquez le parcours, modifiez la copie, arrêtez l’original et publiez la nouvelle version. Planifiez le contrôle de version du parcours avant sa mise en ligne.
- **Aucun critère de sortie défini :** sans critère de sortie, les profils qui convertissent du mid-parcours continueront à recevoir les messages suivants, potentiellement non pertinents ou contradictoires. Configurez toujours des critères de sortie pour les événements de conversion.
- **Non-alignement du consentement du canal :** un profil peut être inscrit aux e-mails, mais pas aux SMS. Les parcours multicanaux doivent respecter le consentement par canal. Vérifiez que les champs de consentement sont renseignés et appliqués à chaque surface de canal.

### Bonnes pratiques

- **Démarrer simple, itérer :** commencez par un parcours linéaire en 2 à 3 étapes avant d’ajouter des embranchements complexes. Validez le fonctionnement du flux principal avant de superposer des conditions et des canaux.
- **Utilisez des conventions de nommage descriptives :** nommez clairement les nœuds de parcours, les conditions et les étapes d’attente (par exemple, « Wait_3_Days_After_Welcome » plutôt que « Wait 1 »). Cela facilite considérablement le débogage du mode test et l’interprétation des rapports.
- **Configurer les critères de sortie au plus tôt :** définissez l’événement de conversion en tant que critère de sortie avant de concevoir les chemins de parcours. Cela permet de s’assurer que les profils qui effectuent la conversion sont supprimés du parcours, quelle que soit l’étape à laquelle ils se trouvent.
- **Définir des durées d’attente significatives :** basez les durées d’attente sur les données de comportement des clients : temps entre les interactions standard, les fenêtres de réponse attendues et la cadence appropriée pour le canal (par exemple, 2 à 3 jours entre les e-mails, 1 semaine entre les SMS).
- **Utilisez les nœuds de condition pour vérifier l’engagement :** après une action de message, ajoutez une condition pour vérifier si le profil s’est engagé (ouvert, a cliqué). Acheminer les profils engagés vers un chemin et les profils non engagés vers un chemin de canal de remontée ou alternatif.
- **Utiliser les attributs calculés pour le branchement :** utilisez des attributs calculés tels que les scores d’engagement, la fréquence d’achat ou les jours depuis la dernière activité pour que les décisions de branchement soient pilotées par les données plutôt qu’arbitraires.
- **Surveiller et optimiser de manière itérative :** consulter les rapports de parcours une fois par semaine pendant l’exécution initiale. Identifiez les points de dépôt, ajustez les durées d’attente, affinez les conditions et optimisez le contenu du message en fonction des données de performances par étape.
- **Mettre à jour vos parcours :** lorsque vous apportez des modifications, dupliquez le parcours pour créer une nouvelle version. Conservez un journal des modifications de version pour le suivi de l’audit et de l’optimisation.

### Décisions de compromis

Les compromis suivants doivent être évalués en fonction des besoins spécifiques de votre entreprise.

#### Entrée lue par l’audience ou entrée déclenchée par un événement

L’entrée lue par l’audience offre un traitement par lots prévisible, plus facile à gérer et à tester. L’entrée déclenchée par un événement offre une réactivité en temps réel qui est plus pertinente du point de vue contextuel, mais qui nécessite une infrastructure de diffusion en continu et une gestion plus prudente des rentrées.

- **Favoris de la lecture d’audience :** prévisibilité, traitement de gros volumes, programmes de cycle de vie planifiés, tests plus simples
- **Favoris déclenchés par un événement :** pertinence en temps réel, contexte comportemental, fréquence des profils individuels, réponse immédiate aux actions des clients.
- **Recommandation :** utilisez la lecture par l’audience pour les programmes de cycle de vie planifiés (intégration, renouvellement) où le timing est axé sur l’entreprise. Utilisez des événements déclenchés pour les séquences de réponse comportementale (abandon de panier, post-achat) où le minutage est déterminé par le client ou la cliente.

#### Parcours à canal unique ou multicanal

Les parcours à canal unique sont plus simples à implémenter, tester et gérer. Les parcours multicanaux offrent des fonctionnalités de portée et d’escalade plus larges, mais augmentent la complexité de la création de contenu, de la gestion du consentement et de la gouvernance des fréquences.

- **Avantages du canal unique :** implémentation plus rapide, gestion du consentement plus simple, effort de production de contenu réduit, débogage plus facile
- **Avantages multicanaux :** potentiel d’engagement plus élevé, remontée des canaux pour les profils non réactifs, expérience client plus complète.
- **Recommandation :** commencez par un parcours à canal unique et validez l’impact sur le flux et l’entreprise avant de passer au multicanal. Ajoutez des canaux de manière incrémentielle lorsque les données d’engagement montrent que le canal principal n’atteint pas efficacement l’audience.

#### Complexité du parcours et facilité de gestion

Un parcours hautement branché avec de nombreuses conditions et de nombreux chemins d’accès peut répondre à davantage de scénarios, mais il devient plus difficile de tester, de déboguer et d’optimiser. Un parcours plus simple avec moins de branches est plus facile à gérer, mais peut offrir une expérience moins personnalisée.

- **Les parcours complexes privilégient :** personnalisation granulaire, chemins spécifiques à un segment, couverture complète des scénarios.
- **Des parcours simplifiés sont privilégiés :** déploiement plus rapide, tests plus faciles, reporting plus clair, charge de maintenance réduite
- **Recommandation** Limiter les parcours à 3 à 5 grandes succursales et à 15 à 25 activités. Si la logique nécessite plus de complexité, envisagez de diviser en plusieurs parcours avec une coordination entre les parcours plutôt qu&#39;un seul parcours monolithique.

#### Rigueur de la limite de fréquence par rapport à l’achèvement du parcours

Des limitations de fréquence strictes protègent contre le sur-message, mais peuvent supprimer les messages de parcours, ce qui entraîne l’omission d’étapes par les profils et la réduction des taux de parcours terminé. Les capuchons flexibles assurent la diffusion des messages de parcours, mais risquent la fatigue du canal.

- **Les limites strictes favorisent :** protection de l’expérience client, taux de désabonnement réduits, confiance dans la marque.
- **Les limites clémentes favorisent :** taux d’achèvement des Parcours, diffusion complète de la séquence de messages, efficacité du programme marketing
- **Recommandation :** attribuez des scores de priorité plus élevés aux messages de parcours critiques (intégration, renouvellement) afin qu’ils soient prioritaires sur les campagnes promotionnelles lorsque les limites sont atteintes. Réservez la mention « exempté du plafonnement » aux seules communications réellement essentielles.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les fonctionnalités utilisées dans cette implémentation.

### Parcours

- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Tester votre parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Activités de parcours

- [Activité Lecture d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Activité de fin](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Configurer une action personnalisée](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Gestion des entrées et des sorties

- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer des surfaces de canal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Création et personnalisation de messages

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

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Fréquence, conflit et priorité

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Rapports et analyses

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Consentement et gouvernance

- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Base des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
