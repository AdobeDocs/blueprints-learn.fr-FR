---
title: Messagerie déclenchée par événement
description: Découvrez comment diffuser des messages contextuels en temps réel en réponse à des événements comportementaux ou système.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '9039'
ht-degree: 1%

---


# Messages déclenchés par un événement

Ce guide fournit un plan directeur complet d’implémentation pour la messagerie déclenchée par un événement utilisant [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de diffuser des messages contextuels en temps réel en réponse à des événements comportementaux ou système.

Utilisez ce guide pour comprendre ce qu’il faut configurer, où se trouvent les choix d’implémentation et quels compromis motivent chaque décision.

Le guide couvre le cycle de vie complet, de l’ingestion d’événements et de la création de parcours à la diffusion de messages et au compte rendu des performances, avec des conseils de décision détaillés pour trois options d’implémentation distinctes.

## Présentation du cas d’utilisation

Les messages déclenchés par un événement diffusent un message contextuel en réponse à un événement comportemental ou système en temps réel. Contrairement à l’activation des messages sortants par lots, qui envoie à une audience pré-évaluée selon un planning, ce modèle écoute un événement qualifiant, tel qu’un abandon de panier, une session de navigation, un envoi de formulaire ou un changement d’état du système, et entre immédiatement le profil de déclenchement dans un parcours qui évalue les conditions et diffuse un message.

Le modèle repose sur la diffusion en continu d’événements en temps réel dans AEP (via Web SDK, Mobile SDK ou une API côté serveur), un parcours avec une entrée d’événement unitaire dans AJO et une logique d’évaluation des conditions qui détermine si et quoi envoyer. Le message est généralement envoyé dans les minutes qui suivent l’événement de déclenchement, ce qui rend ce modèle idéal pour les communications sensibles au temps et pertinentes au contexte.

Les entreprises utilisent ce modèle pour répondre en temps réel aux actions des clients, ce qui accroît la pertinence et entraîne des taux d’engagement et de conversion plus élevés par rapport aux communications par lots planifiées. Les scénarios courants incluent la récupération de panier abandonné, le suivi après achat, les messages de bienvenue après enregistrement et les notifications sensibles au facteur temps comme les échecs de paiement ou les alertes de chute de prix.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Récupérer les paniers et parcours abandonnés](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Réengagez les utilisateurs qui ont abandonné lors des flux d’achat, de demande ou d’inscription avec des suivis personnalisés et opportuns.

| KPI |
| --- |
| Taux De Conversion, Chiffre D’Affaires Incrémentiel, Engagement |

**[Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

| KPI |
| --- |
| Taux De Conversion, Conversion De Lead, Coût Par Lead |

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

| KPI |
| --- |
| Engagement, taux de conversion, satisfaction des clients (CSAT) |

**[Améliorer l’intégration des clients](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Accélérez la rentabilité pour les nouveaux clients grâce à des expériences de bienvenue et des parcours d’activation rationalisés et personnalisés.

| KPI |
| --- |
| Engagement, rétention, taux de conversion |

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont la messagerie déclenchée par un événement peut être appliquée à différents contextes d’entreprise.

- **E-mail ou SMS d’abandon de panier** — Envoyez un message de rappel lorsqu’un client ajoute des articles à son panier, mais ne procède pas à l’achat dans un délai défini
- **Suivi de l’abandon de la navigation** — Réengagez les visiteurs qui ont consulté des produits ou du contenu, mais n’ont pas effectué d’action de conversion
- **Remerciements après achat ou vente croisée** — Donnez une confirmation et une recommandation de vente croisée immédiatement après un achat
- **Rappel d’expiration de la version d’essai** — Avertissez les utilisateurs approchant de la fin d’un essai gratuit avec des messages de renouvellement ou de conversion
- **Message de bienvenue après l’enregistrement** — Envoyez un message d’intégration immédiat lorsqu’un nouvel utilisateur s’enregistre ou crée un compte
- **Confirmation d’envoi du formulaire** — Acceptez les envois de formulaire (demandes de contact, demandes, inscriptions) avec une confirmation contextuelle
- **Notification d&#39;échec de paiement** — Avertissez les clients lorsqu&#39;un paiement récurrent échoue, les invitant à mettre à jour les informations de paiement
- **Notification push de désinstallation de reconquête de l&#39;application** — Déclenchez un message de reconquête lorsqu&#39;un utilisateur désinstalle une application mobile
- **Confirmation de réservation ou de rendez-vous** — Envoyez une confirmation immédiate après la planification d&#39;une réservation, d&#39;une réservation ou d&#39;un rendez-vous
- **Alerte de chute de prix pour les articles mis en vente** — Avertissez les clients lorsqu&#39;un produit de leur liste de souhaits baisse de prix

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer l’efficacité des implémentations de messagerie déclenchée par un événement.

| KPI | Description | Mesure |
| --- | --- | --- |
| Taux de conversion | Pourcentage de destinataires de messages déclenchés qui effectuent l’action souhaitée (achat, inscription, renouvellement) | Conversions/Messages Diffusés * 100 |
| Revenu incrémentiel | Chiffre d’affaires supplémentaire attribuable aux messages déclenchés par un événement par rapport aux populations témoins sans envoi | Chiffre d’affaires d’envois déclenchés - Ligne de base de la population témoin |
| Taux d’ouvertures | Pourcentage de messages diffusés ouverts par les destinataires | Ouvertures / Diffusés * 100 |
| Taux de clic publicitaire (CTR) | Pourcentage de messages diffusés qui génèrent au moins un clic | Clics / Diffusés * 100 |
| Délai jusqu’à la conversion | Temps moyen écoulé entre la diffusion du message et l&#39;événement de conversion | Avg(date et heure de conversion - date et heure de diffusion) |
| Taux d’achèvement du parcours | Pourcentage de profils qui entrent dans le parcours et atteignent l’étape de diffusion du message (non ignorés par les conditions ou les sorties) | Profils atteignant la diffusion / Profils entrant dans le parcours * 100 |
| Taux De Suppression Des Messages | Pourcentage de profils admissibles supprimés en raison des limitations de fréquence, du consentement ou de l’évaluation de la condition | Profils supprimés / Nombre total de profils qualifiés * 100 |
| Taux de rebond | Pourcentage de messages qui n’ont pas pu être délivrés en raison de hard ou soft bounces | Rebonds / Envoyés * 100 |

## Modèle de cas d’utilisation

Cette section décrit le modèle de base et la chaîne de fonction qui génère la messagerie déclenchée par un événement.

**Messagerie déclenchée par un événement**

Détectez un événement système ou comportemental en temps réel, puis envoyez un message contextuel au profil de déclenchement.

**Chaîne de fonction :** Ingestion d’événement > Entrée de Parcours > Évaluation de condition > Diffusion de message > Rapports

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** orchestration des Parcours avec entrée unitaire d’événement, évaluation de condition, étapes d’attente, création de messages, configuration des canaux, gouvernance des fréquences et création de rapports de diffusion
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Évaluation de l’audience pour le filtrage basé sur les conditions dans les parcours, l’application du consentement et de la gouvernance, l’enrichissement des profils
- **[!DNL Adobe Experience Platform] (AEP)** — Ingestion d’événements en temps réel via Web SDK, Mobile SDK ou une API côté serveur ; modélisation des données ; résolution d’identité ; Edge Network

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction Fondamentale | Etat | Éléments devant être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | sandbox AJO configuré avec la configuration de canal active. Autorisations de création et de publication de parcours attribuées à l’équipe d’implémentation. Rôles utilisateur configurés pour la gestion de parcours, la création de contenu et l’administration des canaux. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Un schéma XDM ExperienceEvent doit capturer l’événement déclencheur avec tous les champs contextuels nécessaires à l’évaluation des conditions et à la personnalisation des messages (par exemple, `commerce.productListAdds` pour les événements de panier, les détails de produit, la valeur du panier). Le schéma doit être activé pour le profil client en temps réel. Un jeu de données correspondant doit être créé et activé pour Profil. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Obligatoire | La diffusion en continu d’événements en temps réel doit être configurée : Web SDK pour les événements web, Mobile SDK pour les événements d’application ou l’API Edge Network Server pour les événements système. Un flux de données doit être configuré avec les services AEP et AJO activés, et les événements de routage doivent être acheminés vers le jeu de données approprié. Il s’agit d’une dépendance critique, car le modèle dépend de l’ingestion d’événements en temps réel. | [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configuration des identités et des profils | Obligatoire | L’événement déclencheur doit être associé à une identité connue (e-mail, ID CRM ou session authentifiée) afin que le parcours puisse résoudre le profil et diffuser le message. Des espaces de noms d’identité doivent exister pour les identifiants utilisés par l’événement déclencheur. Les événements anonymes nécessitent un regroupement des identités via le graphique d’identités avant qu’un message puisse être diffusé. Une politique de fusion doit être configurée. | [présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Recommandé | Bien que cela ne soit pas strictement nécessaire pour les parcours déclenchés par un événement (l’entrée est basée sur un événement, et non sur une audience), les segments d’audience peuvent être utilisés pour l’évaluation de la condition dans le parcours (par exemple, envoyer uniquement si le profil se trouve dans un segment « client à forte valeur » ou supprimer si le profil se trouve dans un segment « contacté récemment »). L’évaluation en flux continu est recommandée pour les contrôles d’appartenance à un segment en temps réel dans les parcours. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Importance de la résolution | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que le nombre d’abandons de panier, les jours depuis le dernier achat, la valeur de commande moyenne et le total d’achat de la durée de vie améliorent l’évaluation de la condition et la personnalisation dans les parcours déclenchés. Ces agrégats comportementaux permettent de prendre des décisions de ciblage plus précises (p. ex., distinguer les personnes qui abandonnent pour la première fois de celles qui abandonnent à répétition). | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | L’expiration des données d’événement doit être configurée pour les événements comportementaux transitoires (pages vues, recherches, clics) afin de gérer les coûts de stockage et la conformité. Les champs de schéma de consentement doivent être présents pour l’application d’opt-in/opt-out spécifique au canal pendant la diffusion du message. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Expiration des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les libellés de gouvernance des champs d’événement et de profil garantissent une personnalisation conforme. Si les messages déclenchés incluent du contenu personnalisé à l’aide d’informations d’identification personnelles ou de données comportementales, les libellés d’utilisation des données et les politiques de gouvernance doivent être examinés afin d’empêcher l’utilisation non autorisée des données dans le contenu des messages. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Inclus | La surveillance de l’exécution des parcours fait partie de la phase de création de rapports. En outre, configurez des alertes pour les échecs d’ingestion d’événement ou les retards de traitement des parcours afin de détecter les problèmes de pipeline qui empêcheraient l’envoi des messages déclenchés. | [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Les rapports sur la performance des parcours sont traités dans la phase de reporting. Pour une analyse plus approfondie de l’efficacité des messages déclenchés sur plusieurs canaux et au fil du temps, configurez les connexions et espaces de travail CJA pour analyser l’attribution de la conversion, le délai de conversion et les performances du canal. | [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Journey Orchestration | Création et configuration de parcours | Créez un parcours avec une entrée d’événement unitaire, configurez l’événement de qualification, ajoutez des nœuds de condition, des étapes d’attente, des actions de message, des critères de sortie et des règles de rentrée |
| Configuration de canal | Configuration de la surface de canal | Configurer ou valider des surfaces de canal (e-mail, SMS, notification push), y compris la délégation de sous-domaines, les pools d&#39;adresses IP, les paramètres d&#39;expéditeur et la gestion des listes de suppression |
| Création de messages | Création de contenu de message | Créez du contenu de message contextuel avec une personnalisation basée sur les événements, des blocs de contenu conditionnel et des fragments réutilisables |
| Fréquence et règles métier | Création Et Configuration De parcours (Option C) | Configurez les limites de fréquence et les règles de déduplication pour empêcher la surmessagerie provenant de sources d&#39;événements à haute fréquence |
| Gestion des conflits et des priorités | Création et configuration de parcours | Attribuez des scores de priorité et configurez la détection des conflits pour les parcours en concurrence pour les mêmes profils |
| Rapports et analyse des performances | Rapports et surveillance | Surveiller les mesures de diffusion par parcours au moyen de rapports dynamiques et historiques ; accéder aux données de performances des programmes via CJA |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Configuration de base (F5) | Évaluez les segments d’audience utilisés pour le filtrage basé sur des conditions dans le parcours (par exemple, les segments de clients à forte valeur ajoutée, les segments de suppression). |
| Application du consentement et de la gouvernance | Configuration De Base (S2/S3) | Appliquez les préférences de consentement et les politiques de gouvernance d’utilisation des données lors de la diffusion des messages pour garantir des communications conformes |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] sandbox AJO configuré avec les autorisations de création et de publication de parcours (F1)
- [ ] schéma XDM ExperienceEvent capturant l’événement déclencheur avec des champs contextuels, activés pour le profil client en temps réel (F2)
- [ ] la diffusion en continu d’événements en temps réel configurée via Web SDK, Mobile SDK ou l’API du serveur Edge Network avec un flux de données acheminant les événements vers le jeu de données AEP approprié (F3)
- [ ] Espaces de noms d’identité configurés pour les identifiants sur l’événement déclencheur ; règles de liaison d’identité en place (F4)
- [ ] Surface de canal (e-mail, SMS ou notification push) configurée et validée avec un envoi de test réussi
- [ ] de contenu de message créé, révisé et testé avec des profils types
- [ ] champs de consentement renseignés sur les profils pour le canal cible (par exemple, `consents.marketing.email.val`).
- [ ] Si vous utilisez le filtrage d’audience basé sur des conditions (option B/C), les segments d’audience évalués par flux sont définis et évalués activement

## Options de mise en œuvre

Cette section décrit trois options d’implémentation pour la messagerie déclenchée par un événement. Chaque option s’appuie sur la précédente, ajoutant des fonctionnalités supplémentaires.

### Option A : message simple déclenché par un événement

**Idéal pour :** réponses immédiates d’un seul message lorsqu’aucun délai ou logique conditionnelle n’est nécessaire - confirmation de commande, e-mail de bienvenue, accusé de réception d’envoi de formulaire, confirmation de réservation.

**Fonctionnement :**

Le parcours écoute un événement de qualification via un nœud d&#39;entrée d&#39;événement unitaire. Lorsque l’événement est reçu, le profil entre dans le parcours, passe l’évaluation de condition minimale (vérification du consentement, vérification de l’existence du profil) et reçoit immédiatement un message unique via le nœud d’action de canal configuré.

Il s’agit de la variante d’implémentation la plus simple. La zone de travail de parcours contient un nœud d’entrée d’événement, un nœud de condition facultatif pour les contrôles d’éligibilité de base, un nœud d’action de message unique et un nœud de fin. Il n’existe aucune étape d’attente, aucun embranchement complexe et aucune vérification de conversion. Le message est généralement diffusé dans les secondes à minutes suivant l’événement de déclenchement.

Les données d’événement de l’événement déclencheur (nom du produit, total de la commande, détails du formulaire) peuvent être utilisées pour la personnalisation des messages au moyen d’attributs contextuels dans l’éditeur de personnalisation. Cette approche optimise la vitesse de diffusion et réduit la complexité du parcours.

**Considérations principales :**

- Le message est envoyé que le client effectue ou non une autoconversion après l’événement (aucune vérification de conversion)
- Idéal pour les événements qui nécessitent intrinsèquement une réponse immédiate (confirmations, confirmations)
- Les règles de rentrée doivent être configurées avec soin : pour les messages de type confirmation, autorisez la rentrée afin que chaque événement génère un message ; pour les messages de type bienvenue, empêchez la rentrée

**Avantages :**

- Délai de diffusion le plus rapide (secondes à minutes après l’événement)
- Configuration de parcours la plus simple avec un minimum de pièces mobiles
- Risque le plus faible de défaillances de parcours ou de profils bloqués
- Facilité de test et de maintenance

**Limitations :**

- Impossible de vérifier si le client s’est converti avant l’envoi
- Impossible d’incorporer une logique conditionnelle différée
- Peuvent générer des messages inutiles si l’événement se produit fréquemment sans gouvernance des fréquences

**Experience League:**

- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### Option B : message conditionnel déclenché par un événement avec attente

**Idéal pour** réponses conditionnelles différées dans lesquelles le client doit avoir le temps de procéder à une auto-conversion avant de recevoir le message : abandon de panier (patientez 1 à 4 heures, puis vérifiez si le panier est toujours abandonné), abandon de navigation (patientez 24 heures, vérifiez si l’achat a été effectué), expiration de la version d’essai (patientez jusqu’à l’approche de la date d’expiration).

**Fonctionnement :**

Le parcours écoute un événement de qualification, entre dans le profil et introduit une période d’attente avant l’évaluation des conditions. Après l’attente, un nœud de condition vérifie si le client s’est converti lui-même (par exemple, a terminé l’achat, renouvelé l’abonnement) ou si le contexte d’origine est toujours valide. Ce n’est que si la condition est remplie (par exemple, le panier est toujours abandonné) que le parcours passe à la diffusion des messages.

La zone de travail de parcours contient un nœud d’entrée d’événement, un nœud d’attente (durée configurable ou date/heure spécifique), un nœud de condition qui vérifie un événement de conversion ou un changement d’état de profil, des chemins d’embranchement (envoi du message ou sortie sans envoi), un nœud d’action de message sur le chemin de qualification et un nœud de fin sur chaque branche. Les critères de sortie peuvent être configurés pour supprimer automatiquement les profils du parcours si l’événement de conversion se produit pendant la période d’attente, rendant ainsi inutile la vérification explicite des conditions.

Cette approche réduit les messages inutiles en donnant aux clients le temps de s’auto-convertir, ce qui améliore l’expérience client et accroît la pertinence perçue des messages envoyés.

**Considérations principales :**

- La durée d’attente a un impact significatif sur les taux de conversion. Des attentes plus courtes (1-2 heures) entraînent une urgence plus élevée, mais plus d’envois inutiles. Des attentes plus longues (24-48 heures) réduisent le volume, mais peuvent ne pas respecter la fenêtre de pertinence
- L’évaluation de la condition nécessite que l’événement de conversion soit capturé dans AEP et associé à la même identité de profil
- Les critères de sortie offrent une alternative plus propre aux nœuds de condition explicites pour la vérification des conversions
- Les règles de rentrée doivent tenir compte de la période d’attente. Un profil ne doit pas entrer à nouveau dans le parcours alors qu’il est déjà en attente

**Avantages :**

- Réduit les messages inutiles en vérifiant l’autoconversion
- Produit des communications plus pertinentes et de meilleure qualité
- Prend en charge les cas d’utilisation urgents avec des fenêtres de délai configurables
- Les critères de sortie permettent la suppression automatique du parcours lors de la conversion.

**Limitations :**

- Complexité accrue du parcours avec les nœuds d’attente et de condition
- Les profils occupent des emplacements de parcours pendant les périodes d’attente (soumises à un délai d’expiration de parcours de 91 jours)
- Nécessite que l’événement de conversion soit ingéré dans AEP dans la fenêtre d’attente pour une évaluation de condition précise
- Délai de livraison plus long par rapport à l’option A

**Experience League:**

- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Option C : Déclenché par un événement avec gouvernance des fréquences

**Idéal pour :** sources d’événements à haute fréquence pour lesquelles la fatigue des messages est un problème (pages vues, consultations de produits, requêtes de recherche, ajouts au panier renouvelés). Peut être appliqué en tant que superposition sur l’option A ou l’option B.

**Fonctionnement :**

Cette option ajoute la gouvernance de fréquence à l’option A ou à l’option B pour éviter le sur-message. Les événements comportementaux haute fréquence (tels que les consultations de produits ou les ajouts répétés au panier) peuvent déclencher le parcours plusieurs fois en une courte période. Sans gouvernance des fréquences, un profil peut recevoir des messages en double ou en excès.

La gouvernance des fréquences est mise en œuvre par le biais de deux mécanismes complémentaires : les règles métier d’AJO (limitations de fréquence) qui limitent le nombre de messages reçus par canal et par période temporelle, ainsi que les règles de rentrée au niveau du parcours qui définissent une période de réflexion avant qu’un profil puisse rejoindre à nouveau le même parcours. Les règles métier s’appliquent au niveau de l’organisation et imposent des limites à toutes les campagnes et tous les parcours (par exemple, 3 e-mails maximum par semaine), tandis que le rechargement des entrées s’applique au niveau de chaque parcours (par exemple, un profil ne peut pas rejoindre à nouveau ce parcours spécifique dans les 72 heures suivant la dernière entrée).

En outre, la gestion des conflits et des priorités peut être configurée pour attribuer des scores de priorité au parcours déclenché, de sorte que lorsque plusieurs parcours ou campagnes se disputent le même profil, la communication la plus prioritaire l’emporte.

**Considérations principales :**

- Les limites de fréquence doivent trouver l’équilibre entre la prévention de la fatigue et la diffusion de messages déclenchés importants
- Des limitations spécifiques aux canaux sont recommandées (les e-mails, SMS et notifications push ont des seuils de fatigue différents).
- Le refroidissement de rentrée du parcours et les limitations de fréquence au niveau de l’organisation fonctionnent ensemble ; les deux doivent être configurés
- Les scores de priorité déterminent quelle communication gagne lorsque les limites sont atteintes ; les parcours de priorité supérieure doivent recevoir des scores plus élevés

**Avantages :**

- Empêche la fatigue des messages provenant de sources d’événements à haute fréquence
- Maintient la réputation de la marque et la satisfaction des abonnés
- Les plafonds au niveau de l’organisation fournissent un filet de sécurité dans toutes les campagnes et tous les parcours
- La notation de priorité garantit que les messages les plus importants sont diffusés lorsque les limites sont atteintes

**Limitations :**

- Certains profils qualifiés seront supprimés, avec éventuellement des messages pertinents manquants
- La configuration de la limitation de fréquence ajoute une complexité administrative
- Les limitations peuvent interagir de manière inattendue avec d’autres campagnes et parcours actifs partageant le même canal
- Nécessite une surveillance et des ajustements continus à mesure que le portefeuille de messages change

**Experience League:**

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : Déclenché Par Un Événement Simple | Option B : Conditionnel avec attente | Option C : Gouvernance Des Fréquences |
| --- | --- | --- | --- |
| Idéal pour | Confirmations, confirmations et confirmations immédiates | Abandon, rétablissement, réponses conditionnelles retardées | Sources d’événements à haute fréquence, environnements à parcours multiples |
| Complexité | Faible | Moyenne | Medium-Grand (ajoute à A ou B) |
| Latence des messages | Secondes à minutes | Minutes à heures/jours (attente configurable) | Identique à l&#39;option sous-jacente (A ou B) |
| Vérification de l’auto-conversion | Non | Oui (via la condition ou les critères de sortie) | Dépend de l’option sous-jacente |
| Protection De La Fréquence | Aucune (sauf si combiné avec C) | Aucune (sauf si combiné avec C) | Oui — limites de canal et refroidissement de reprise |
| Nœuds de la zone de travail de parcours | 3-4 (événement, condition facultative, action, fin) | 5-7 (événement, attente, condition, branches, action, fins) | Identique à A ou B, plus configuration des règles métier |
| Requiert | Schéma d’événement, surface de canal, contenu du message | Toutes les options A + ingestion des événements de conversion | Toutes les options A ou B + configuration des règles de fréquence |

### Choisir la bonne option

Utilisez les conseils de décision suivants pour sélectionner l’option d’implémentation appropriée.

1. **Le message doit-il être envoyé immédiatement et sans délai ?** Si oui, commencez par **Option A**. Les messages de confirmation, les e-mails de bienvenue et les accusés de réception ne nécessitent généralement pas de période d’attente.

2. **Le client doit-il avoir le temps de s’auto-convertir avant de recevoir le message ?** Si oui, choisissez **Option B**. Les cas d’utilisation d’abandon de panier, d’abandon de navigation et d’expiration d’essai bénéficient d’une période d’attente qui permet aux clients de terminer eux-mêmes l’action.

3. **L’événement de déclenchement est-il haute fréquence (il se produit plusieurs fois par session ou par jour pour le même profil) ?** Si oui, ajoutez **Option C** en tant que recouvrement sur l’option A ou B. Les consultations de produits, les pages vues et les événements de recherche peuvent générer un grand nombre de déclencheurs qui nécessitent une protection par fréquence.

4. **Plusieurs parcours et campagnes déclenchés sont-ils actifs dans le sandbox ?** Si oui, ajoutez l’**option C** quelle que soit la fréquence des événements pour gérer la charge de communication entre parcours et éviter la fatigue du canal.

En pratique, la plupart des implémentations de production utilisent les options B + C pour les cas d’utilisation de style abandon (attente conditionnelle avec gouvernance des fréquences) et les options A + C pour les cas d’utilisation de style confirmation (envoi immédiat avec gouvernance des fréquences comme filet de sécurité).

## Phases de mise en œuvre

Les phases suivantes décrivent l’implémentation de bout en bout de la messagerie déclenchée par un événement.

### Phase 1 : configuration du schéma d’événement et de la collecte de données

**Fonction d’application :** AEP : modélisation des données (F2), AEP : sources et collecte de données (F3)

**Ce que vous allez configurer :** le schéma XDM ExperienceEvent qui capture l’événement déclencheur, le jeu de données qui stocke ces événements et le pipeline de collecte de données en temps réel (Web SDK, Mobile SDK ou API du serveur) qui diffuse les événements dans AEP. Cette phase établit la base de données que le parcours écoutera.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : déclenchement du type d&#39;événement**
>
>Quel événement déclenche le message ? Le type d’événement détermine les champs de schéma requis et la méthode de collecte.
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Événement Commerce (ajout au panier, achat, passage en caisse) | Cas d’utilisation d’e-commerce : abandon de panier, post-achat | Nécessite un groupe de champs Commerce avec des champs `productListItems`, `cart` et `order` |
>| Événement d’interaction web (page vue, vue du produit) | Abandon de la navigation, déclencheurs d’engagement de contenu | Nécessite un groupe de champs Détails web avec des champs `webPageDetails`, `webInteraction` |
>| Événement d’application (installation de l’application, désinstallation, action in-app) | Déclencheurs d’engagement mobile | Nécessite l’implémentation de Mobile SDK et le groupe de champs Application |
>| Evénement système (echec de paiement, changement d&#39;abonnement, mise à jour du statut) | Notifications opérationnelles | Nécessite une API côté serveur ou un connecteur source pour ingérer les événements système |
>| Événement d’envoi de formulaire | Génération de leads, confirmation d’inscription | Nécessite un groupe de champs personnalisés capturant les champs de données de formulaire |

>[!NOTE]
>
>**Décision : méthode de collecte**
>
>Comment l’événement déclencheur sera-t-il capturé et diffusé en continu dans AEP ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| SDK web | Événements comportementaux basés sur le web (ajouts au panier, pages vues, envois de formulaire) | Nécessite une installation de Web SDK sur le site web ; les événements sont diffusés en temps réel via Edge Network |
>| SDK Mobile | Événements sur application mobile (ouvertures d’application, actions in-app, enregistrement du jeton push) | Nécessite l’intégration de Mobile SDK dans l’application native ou le wrapper React Native |
>| API du serveur Edge Network | Événements système côté serveur (traitement des paiements, gestion des abonnements, déclencheurs principaux) | Aucune dépendance côté client ; événements envoyés à partir des systèmes principaux de l’entreprise. |
>| Connecteur Source | Événements provenant de systèmes externes (CRM, automatisation marketing, plateformes héritées) | En règle générale, la diffusion en lots peut ne pas prendre en charge le déclenchement en temps réel, sauf si elle est compatible avec le streaming |

**Navigation dans l’interface utilisateur :** Collecte de données > Flux de données > Nouveau flux de données (pour la configuration du flux de données) ; Schémas > Créer un schéma (pour le schéma d’événement) ; Jeux de données > Créer un jeu de données à partir d’un schéma (pour la création d’un jeu de données)

**Détails de configuration clés :**

- Le schéma d&#39;événement doit inclure tous les champs nécessaires à l&#39;évaluation des conditions du parcours et à la personnalisation des messages
- Les services [!DNL Adobe Experience Platform] et [!DNL Adobe Journey Optimizer] doivent être activés pour le flux de données
- Le jeu de données doit être activé pour le profil client en temps réel afin que les événements soient associés aux profils unifiés
- Les données d’événement doivent inclure un champ d’identité (e-mail, identifiant CRM, ECID) qui peut être résolu sur un profil connu

**Documentation Experience League :**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Présentation de l’ingestion par flux](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Phase 2 : configuration de l’identité et du profil

**Fonction D’Application :** AEP : Configuration D’Identité Et De Profil (F4)

**Éléments à configurer :** espaces de noms d’identité pour les identifiants sur l’événement déclencheur, désignation de l’identité principale sur le schéma d’événement, règles de liaison d’identité pour la résolution sur l’ensemble des appareils et une politique de fusion pour l’unification des profils. Cela permet de s’assurer que l’événement de déclenchement est associé à un profil client unifié afin que le parcours puisse résoudre les informations de contact et diffuser le message.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : identité du Principal pour le schéma d’événement**
>
>Quel champ d’identité de l’événement déclencheur doit servir d’identité principale pour la résolution des profils ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Adresse e-mail | Événements des sessions web authentifiées ou des formulaires où l’e-mail est capturé | Résolution directe vers une identité contactable ; chemin le plus simple vers la diffusion e-mail |
>| ID CRM | Evénements des systèmes authentifiés dont l&#39;identifiant CRM est l&#39;identifiant principal | Nécessite la création d’un espace de noms d’identifiant CRM ; le profil doit avoir un e-mail ou un téléphone lié pour la diffusion des messages |
>| ECID (Experience Cloud ID) | Événements web ou d’application anonymes où aucune identité authentifiée n’est disponible | Nécessite un assemblage d’identités pour lier l’ECID à une identité connue ; les messages ne peuvent pas être envoyés à l’ECID seul |
>| Numéro de téléphone | Événements provenant des interactions des appareils mobiles ou des centres d’appels | Prend en charge la diffusion par SMS ; nécessite l’espace de noms Téléphone |

**Navigation dans l’interface utilisateur :** Identités > Créer un espace de noms d’identité ; Schémas > Sélectionner le schéma > Sélectionner le champ > Identité > Définir comme identité principale ; Profils > Politiques de fusion

**Détails de configuration clés :**

- Les événements anonymes (ECID uniquement) ne peuvent pas déclencher la diffusion du message tant que l’ECID n’est pas lié à une identité contactable connue (e-mail, téléphone) via le graphique d’identité
- La politique de fusion utilisée par AJO doit être cohérente avec celle utilisée pour l’évaluation des audiences
- Pour les messages déclenchés sur le web, assurez-vous que le graphique d’identités lie l’ECID aux identités authentifiées par le biais d’événements de connexion

**Documentation Experience League :**

- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 3 : configuration des surfaces de canal

**Fonction d’application :** AJO : configuration de canal

**Ce que vous allez configurer :** la surface de canal (préréglage) qui définit l&#39;infrastructure d&#39;envoi pour le message déclenché (délégation de sous-domaine, groupe d&#39;adresses IP, identité de l&#39;expéditeur, adresse de réponse, gestion des désabonnements et informations d&#39;identification spécifiques au canal (fournisseur de SMS, certificats push). Une surface de canal valide doit exister avant que le contenu du message puisse être créé ou que les parcours puissent être publiés.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : canal du message**
>
>Quel canal le message déclenché utilisera-t-il ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| E-mail | La plupart des cas d’utilisation de messagerie déclenchés : récupération de l’abandon, confirmations, intégration | Nécessite la délégation de sous-domaine, le pool d’adresses IP, la configuration de l’expéditeur ; prend en charge le contenu HTML riche et la personnalisation |
>| SMS | Notifications sensibles à l’heure, alertes concises, audiences avec un engagement élevé des SMS | Nécessite l’intégration d’un fournisseur de SMS (Sinch, Twilio, Infobip) ; soumis à des limites de caractères et à des exigences de consentement plus strictes |
>| Notification push | Engagement des applications mobiles, réengagement des utilisateurs de l’application | Nécessite une configuration des informations d’identification push (APNs pour iOS, FCM pour Android) ; l’utilisateur doit disposer de l’application installée avec push activé. |
>| Plusieurs canaux | Stratégie d’engagement complète utilisant la préférence de canal ou la logique de secours | Nécessite plusieurs surfaces de canal. La sélection de canal peut être gérée via des nœuds de condition de parcours. |

>[!NOTE]
>
>**Décision : méthode de délégation de sous-domaine (e-mail)**
>
>Comment le sous-domaine d’envoi d’e-mail doit-il être délégué à Adobe ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Délégation complète | L’entreprise souhaite qu’Adobe gère tous les enregistrements DNS pour le sous-domaine d’envoi | Configuration la plus simple : Adobe gère automatiquement les enregistrements SPF, DKIM et DMARC |
>| Délégation CNAME | L’entreprise souhaite conserver le contrôle du DNS en pointant vers l’infrastructure Adobe | Nécessite une gestion manuelle des enregistrements DNS ; offre un meilleur contrôle organisationnel sur le DNS |

**Navigation dans l’interface utilisateur :** Administration > Canaux > Sous-domaines (pour la configuration des sous-domaines) ; Administration > Canaux > Groupes d’adresses IP (pour la configuration des groupes d’adresses IP) ; Administration > Canaux > Surfaces de canal > Créer une surface (pour la création de surface)

**Détails de configuration clés :**

- La vérification des sous-domaines et la propagation DNS peuvent prendre jusqu’à 48 heures
- Les nouveaux groupes d’adresses IP nécessitent un plan de préchauffage (augmentation progressive du volume sur 2 à 4 semaines)
- Configurer des en-têtes list-unsubscribe en un clic pour la conformité des e-mails
- Pour les SMS, configurez les informations d’identification du fournisseur avant de créer la surface du canal SMS
- Pour les notifications push, configurez les informations d’identification APNs et FCM avant de créer la surface de canal push

**Documentation Experience League :**

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Configurer des surfaces de canal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 4 : création du contenu du message

**Fonction d’application :** AJO : création de messages

**Ce que vous allez configurer :** le contenu du message qui sera diffusé par le parcours, notamment la conception de la disposition, les jetons de personnalisation à l’aide d’attributs de profil et d’événement, les blocs de contenu conditionnel, les fragments réutilisables (en-têtes, pieds de page, clauses de non-responsabilité), ainsi que l’aperçu et le test du contenu.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : approche du contenu**
>
>Comment le contenu du message doit-il être créé ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Démarrer à partir d’un modèle existant | Il existe des modèles d’organisation et la cohérence de la marque est requise. | Chemin le plus rapide vers la création de contenu ; assure la conformité de la marque ; les modifications du modèle se propagent aux nouveaux messages |
>| Concevoir en partant de zéro dans Email Designer | Mise en page personnalisée nécessaire pour ce message spécifique déclenché | Contrôle créatif complet ; éditeur visuel par glisser-déposer ; plus lent mais plus flexible |
>| Importer HTML | Le contenu est conçu par une équipe ou une agence externe et fourni sous la forme d’HTML | Nécessite une expertise en codage HTML ; peut ne pas prendre entièrement en charge toutes les fonctionnalités de Designer d’email |

>[!NOTE]
>
>**Décision : personnalisation des événements**
>
>Quelles données d’événement doivent être utilisées dans le contenu du message ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Attributs contextuels d’événement | Le message doit inclure des détails de l’événement déclencheur (nom du produit, valeur du panier, champs du formulaire) | Utilisez des attributs d’événement contextuels dans l’éditeur de personnalisation ; les données proviennent de la payload de l’événement déclencheur |
>| Attributs de profil | Le message doit inclure des données au niveau du profil (prénom, niveau de fidélité, emplacement) | Utilisez des attributs de profil via des chemins XDM (par exemple, `profile.person.name.firstName`) ; les données proviennent du profil unifié |
>| Attributs d’événement et de profil | Le message doit combiner le contexte d’événement et la personnalisation de profil | Approche la plus courante pour les messages déclenchés : garantit à la fois la pertinence (événement) et la personnalisation (profil) |

**Navigation dans l’interface utilisateur :** Gestion de contenu > Modèles de contenu > Parcourir (pour la sélection des modèles) ; Action de campagne ou de Parcours > Modifier le contenu > Designer d’e-mail (pour la conception de contenu) ; Sélectionner le composant de texte > Icône de Personalization (pour ajouter la personnalisation)

**Détails de configuration clés :**

- Utilisez des attributs contextuels à personnaliser avec les données de l’événement déclencheur (par exemple, nom du produit, valeur du panier)
- Utilisez des attributs de profil pour le nom, les préférences et les données de fidélité
- Configurez des blocs de contenu conditionnel pour faire varier le contenu par segment ou attribut de profil (par exemple, un CTA différent pour les membres du programme de fidélité).
- Créer des fragments réutilisables pour les en-têtes, pieds de page et clauses de non-responsabilité partagées entre les messages déclenchés
- Aperçu avec plusieurs profils de test pour vérifier que les rendus de personnalisation sont corrects
- Envoyer des BAT aux parties prenantes internes avant de publier le parcours

**Documentation Experience League :**

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 5 : création et configuration du parcours

**Fonction de l’application :** AJO : Journey Orchestration, AJO : Fréquence et règles métier (option C), AJO : gestion des conflits et des priorités

**Ce que vous allez configurer :** le parcours qui écoute l’événement déclencheur et orchestre la diffusion des messages. Il s’agit de la phase d’implémentation principale au cours de laquelle la zone de travail du parcours est conçue avec le nœud d’entrée d’événement, les nœuds de condition, les étapes d’attente (pour l’option B), les nœuds d’action de message et les critères de sortie. Cette phase couvre également la gouvernance des fréquences (option C) et la configuration des conflits/priorités.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : règles de rentrée**
>
>Un profil peut-il rejoindre à nouveau ce parcours si l’événement déclencheur se produit à nouveau ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Autoriser la rentrée (avec rechargement) | L’événement peut légitimement se reproduire et chaque occurrence nécessite un message (par exemple, chaque abandon de panier doit déclencher un message de récupération) | Définir une période de recharge (minimum 5 minutes) pour éviter une reprise rapide des événements en double ; la période de recharge type va de 1 heure à 72 heures |
>| Pas de rentrée | Le message ne doit être envoyé qu’une seule fois par profil, quelle que soit la périodicité de l’événement (par exemple, message de bienvenue après le premier enregistrement) | Le profil est définitivement exclu après l’achèvement du premier parcours ; approprié pour les messages à durée de vie unique |

>[!NOTE]
>
>**Décision : durée d’attente (option B uniquement)**
>
>Combien de temps le parcours doit-il attendre avant d’évaluer les conditions et d’envoyer le message ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Attente courte (1-4 heures) | Cas d’utilisation urgents tels que l’abandon de panier pour lesquels un suivi immédiat est efficace | Volume de messages plus élevé ; peut intercepter certains autoconvertisseurs ; idéal pour la récupération de panier à forte valeur ajoutée |
>| Attente de Medium (12-24 heures) | Cas d’utilisation d’urgence modérée tels que l’abandon de navigation ou l’engagement de contenu | Approche équilibrée ; réduit les envois inutiles tout en conservant leur pertinence |
>| Attente longue (2-7 jours) | Cas d’utilisation de faible urgence, tels que des rappels d’expiration d’essai ou des bilans périodiques | Réduction du volume des messages ; risque accru de perdre leur pertinence contextuelle |
>| Date/heure personnalisées | Cas d’utilisation liés à une date spécifique (par exemple, envoyer 3 jours avant la date d’expiration de l’essai) | Attendre une date/heure calculée ; utilise l’éditeur d’expression personnalisé |

>[!NOTE]
>
>**Décision : critères de sortie**
>
>Dans quelles conditions un profil doit-il être supprimé du parcours avant d’atteindre l’action du message ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Événement de conversion (par exemple, achat terminé) | Abandon de panier ou de navigation lorsque l’objectif est la conversion | Le profil se ferme automatiquement lorsque l’événement de conversion est détecté ; approche la plus épurée pour l’option B |
>| Modification de l’appartenance à l’audience | Le profil doit se fermer s’il quitte un segment qualifié | Nécessite une audience évaluée par flux qui se met à jour en temps quasi réel |
>| Délai d’expiration du parcours (91 jours max.) | Comportement par défaut : le profil se ferme après la durée de parcours maximale | Le filet de sécurité ne devrait pas être le principal mécanisme de sortie pour les parcours déclenchés de courte durée |
>| Aucun critère de sortie explicite | Des confirmations simples (option A) où chaque profil qualifié doit recevoir le message | Le profil se ferme naturellement après l’action de message et le nœud de fin |

>[!NOTE]
>
>**Décision : gouvernance des fréquences (option C)**
>
>Combien de messages déclenchés un profil doit-il recevoir par période ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Limites spécifiques au canal (par exemple, 3 e-mails/semaine, 1 SMS/jour) | Les différents canaux ont des seuils de fatigue différents | Approche recommandée ; respecte le niveau d’intrusion de chaque canal |
>| Limite globale (par exemple, 5 messages/semaine sur tous les canaux) | Gouvernance simplifiée pour tous les types de communication | Plus facile à gérer mais moins nuancé ; peut limiter de manière excessive les canaux moins intrusifs. |
>| Refroidissement de rentrée de parcours niveau uniquement | Gouvernance des fréquences nécessaire pour ce parcours spécifique, mais pas à l’échelle de l’organisation. | Implémentation la plus simple ; ne protège pas contre la fatigue entre les parcours |

**Navigation dans l’interface utilisateur :** Parcours > Créer un Parcours (pour la création de parcours) ; Zone de travail de Parcours > Faire glisser l’activité d’événement (pour l’entrée d’événement) ; Zone de travail de Parcours > Faire glisser l’activité « Attente » (pour la configuration d’attente) ; Zone de travail de Parcours > Faire glisser l’activité « Condition » (pour l’embranchement de condition) ; Propriétés du Parcours > Critères de sortie (pour la configuration de sortie) ; Administration > Règles métier > Créer une règle (pour les limitations de fréquence)

**Détails de configuration clés :**

- Configurez l&#39;événement de parcours en sélectionnant le schéma d&#39;événement et en définissant les conditions de qualification
- Pour l’option B, ajoutez le nœud d’attente immédiatement après l’entrée de l’événement et avant toute évaluation de condition
- Configurez les nœuds de condition à l’aide des attributs de profil, des données d’événement ou des contrôles d’appartenance d’audience
- Liez le nœud d’action du message à la surface de canal et au contenu créé lors des phases 3 et 4.
- Définissez le délai d’expiration du parcours sur une durée appropriée (inférieure à 91 jours pour les parcours déclenchés).
- Pour l’option C, créez des règles de fréquence via Administration > Règles métier avant de publier le parcours
- Attribuez un score de priorité au parcours si d’autres campagnes ou parcours ciblent des audiences qui se chevauchent

**Là où les options divergent :**

**Pour L’Option A (Déclenchement Simple D’Un Événement) :**
La zone de travail de parcours est minimale : entrée d’événement > condition de consentement/éligibilité facultative > action du message > fin. Aucune étape d’attente ni vérification de conversion. Définissez des règles de rentrée selon si l’événement doit générer un message à chaque fois qu’il se produit.

**Pour l’option B (conditionnelle avec attente) :**
Ajoutez un nœud d’attente après l’entrée d’événement. Après l’attente, ajoutez un nœud de condition pour vérifier la conversion (par exemple, vérifier si `commerce.purchases` événement s’est produit après l’entrée dans le parcours) ou utilisez des critères de sortie pour supprimer automatiquement les profils convertis. Branche vers l’action du message sur le chemin « non converti » et vers un nœud d’extrémité sur le chemin « converti ».

**Pour L’Option C (Gouvernance Des Fréquences) :**
Configurez les limites de fréquence au niveau de l’organisation via Administration > Règles métier avant publication. Définissez le refroidissement de rentrée au niveau du parcours dans les propriétés du parcours. Vous pouvez éventuellement attribuer un score de priorité via les propriétés du parcours afin de contrôler quelle communication gagne lorsque des limites sont atteintes. Cette option peut être appliquée en plus de l’option A ou de l’option B.

**Documentation Experience League :**

- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 6 : test et déploiement du parcours

**Fonction d’application :** AJO : Journey Orchestration

**Ce que vous allez configurer :** validation du mode test pour vérifier que le parcours se comporte comme prévu avec les profils de test, suivie de la publication du parcours pour le rendre actif.

**Navigation dans l’interface utilisateur :** de la zone de travail du Parcours > Basculement du mode Test (pour les tests) ; zone de travail du Parcours > Publier (pour le déploiement)

**Détails de configuration clés :**

- Activez le mode test sur la zone de travail de parcours pour simuler des déclencheurs d’événement avec des profils de test
- Sélectionnez des profils de test qui disposent d’informations de contact de canal valides (adresse e-mail, numéro de téléphone)
- Déclenchez l’événement de test et vérifiez que le profil de test traverse le chemin d’accès prévu
- Pour l’option B, vérifiez que l’étape d’attente se comporte correctement et que l’évaluation de la condition produit l’embranchement attendu
- Vérifiez que les jetons de personnalisation s’affichent correctement dans le message de test
- Une fois les tests réussis, publiez le parcours pour le rendre actif
- Surveiller le statut du parcours et les mesures d’entrée de profil initiales après publication

**Documentation Experience League :**

- [Tester votre parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Phase 7 : Surveillance et rapports sur le rendement

**Fonction d’application :** AJO : Rapports et analyse des performances, S4 : surveillance et observabilité, S5 : rapports et analyses

**Ce que vous allez configurer :** des rapports de parcours dynamiques et historiques pour le suivi de la diffusion et de l’engagement, des alertes de plateforme pour les échecs d’ingestion d’événements et de traitement des parcours et, éventuellement, des espaces de travail CJA pour une analyse cross-canal plus approfondie de l’efficacité des messages déclenchés.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : Profondeur des rapports**
>
>Quelle quantité d’analyse des rapports est nécessaire pour ce cas d’utilisation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Rapports natifs AJO uniquement | La surveillance opérationnelle des mesures de diffusion est suffisante | Disponible immédiatement ; couvertures envoyées, diffusées, rejetées, ouvertes, sur lesquelles l’utilisateur a cliqué ; aucune configuration supplémentaire n’est nécessaire |
>| AJO natif + intégration à CJA | Une analyse cross-canal, une attribution de conversion et une analyse des tendances sont nécessaires | Nécessite une connexion CJA et une vue de données liées aux jeux de données AJO ; fournit des fonctionnalités d’analyse plus approfondies |

**Navigation dans l’interface utilisateur :** Parcours > Sélectionner le parcours > Rapport dynamique (pour la surveillance dynamique) ; Parcours > Sélectionner le parcours > Rapport à toute heure (pour l’analyse historique) ; Alertes > Règles d’alerte > S’abonner (pour la configuration des alertes)

**Détails de configuration clés :**

- Accédez au rapport dynamique de parcours pendant l’exécution en cours pour surveiller les entrées de profil, les sorties et les mesures de diffusion
- Consultez le rapport historique une fois que le parcours a été actif pendant suffisamment de temps pour accumuler des données significatives
- Configuration d’alertes pour les échecs d’exécution du flux source (ingestion d’événement) et les retards de traitement des parcours
- Pour l’intégration de CJA, assurez-vous que la connexion CJA inclut les jeux de données d’événement d’expérience AJO (jeu de données d’événement de retour de message, jeu de données d’événement d’expérience de suivi d’e-mail)

**Documentation Experience League :**

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage pour les implémentations de messagerie déclenchée par un événement.

### Mécanismes de sécurisation et limites

Les limites et mécanismes de sécurisation de plateforme suivants s’appliquent aux implémentations de messagerie déclenchées par un événement.

- **Débit d’événement unitaire :** 5 000 événements au maximum par seconde et par sandbox pour les parcours d’événement unitaire - [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Limite de parcours dynamique :** 500 parcours dynamiques au maximum par sandbox — [Mécanismes de sécurisation Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Parcours canvas limit:** 50 activités maximum par parcours canvas
- **Délai d’expiration du Parcours :** la durée maximale du parcours est de 91 jours (délai d’expiration global)
- **Refroidissement de rentrée :** le refroidissement de rentrée minimal est de 5 minutes
- **Configurations de limitation de la fréquence :** 10 configurations de limitation maximum par sandbox
- **Surfaces de canal :** 10 surfaces de canal au maximum par type de canal et par sandbox
- **Ingestion par flux :** 20 000 enregistrements au maximum par seconde par connexion HTTP — [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **Attributs calculés :** 25 attributs calculés au maximum par sandbox — [Mécanismes de sécurisation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Fragments de contenu :** 30 fragments de contenu au maximum par message
- **Actualisation des rapports dynamiques :** les rapports dynamiques sont actualisés toutes les 60 secondes et affichent les dernières 24 heures de données
- **Latence des rapports historiques :** le remplissage complet des rapports historiques (à toute heure) peut prendre jusqu’à 2 heures après la fin de l’exécution

### Pièges courants

Tenez compte des problèmes courants suivants lors de l’implémentation de la messagerie déclenchée par un événement.

- **Événements anonymes sans résolution d’identité :** le déclenchement d’événements qui ne transportent qu’un ECID (identifiant de cookie anonyme) ne peut pas être résolu en un profil contactable pour la diffusion des messages. Assurez-vous que l’événement de déclenchement comprend une identité authentifiée ou que le graphique d’identité lie l’ECID à un contact connu. Sans résolution d’identité, les profils entrent dans le parcours, mais échouent à l’étape de diffusion du message.

- **Événement de conversion manquant pour les contrôles de condition d’option B :** si l’événement de conversion (par exemple, achat) n’est pas ingéré dans AEP ou n’est pas associé à la même identité de profil que l’événement de déclenchement, la vérification de condition s’évaluera incorrectement comme « non converti » et enverra des messages inutiles. Vérifiez que les événements de conversion se propagent dans AEP en temps réel et partagent une identité avec l’événement de déclenchement.

- **Règles de rentrée trop permissives :** autoriser une rentrée sans période de recharge sur des sources d’événements à haute fréquence peut entraîner la réception de plusieurs messages par le même profil en quelques minutes. Définissez toujours un temps de recharge de reprise qui correspond au contexte commercial (par exemple, un temps de recharge de 4 heures pour l’abandon de panier, un temps de recharge de 24 heures pour l’abandon de navigation).

- **Désalignement du fuseau horaire de l’étape d’attente :** processus Étapes d’attente en UTC par défaut. Si le parcours cible des profils sur plusieurs fuseaux horaires et que l’attente doit s’aligner sur l’heure locale du destinataire, configurez les paramètres de fuseau horaire sur le parcours en conséquence.

- **Conflits entre les limites de fréquence et d’autres campagnes :** les limites de fréquence au niveau de l’organisation s’appliquent à toutes les campagnes et tous les parcours. Un nouveau parcours déclenché peut être supprimé si les profils ont déjà atteint leur limite d’autres campagnes actives. Surveillez le taux de suppression et ajustez les scores de priorité pour vous assurer que les messages déclenchés importants sont prioritaires.

- **Échec de la publication du Parcours en raison de dépendances manquantes :** Chaque branche de la zone de travail du parcours doit se terminer par une activité de fin. Tous les nœuds d’action doivent référencer des surfaces de canal valides avec le contenu du message actif. Vérifiez toutes les dépendances avant de publier.

### Bonnes pratiques

Suivez ces recommandations pour réussir l’implémentation de la messagerie déclenchée par un événement.

- **Démarrer simple, puis itérer :** Commencer par l’option A pour les nouveaux cas d’utilisation de messagerie déclenchée. Ajoutez une logique d’attente et de condition (option B) uniquement après la validation du pipeline d’événement et de la diffusion du message. Ajoutez la gouvernance de fréquence (option C) lorsque plusieurs parcours déclenchés sont actifs.

- **Utilisez des critères de sortie au lieu des nœuds de condition pour les contrôles de conversion :** les critères de sortie suppriment automatiquement les profils du parcours lorsqu’un événement de qualification (un achat, par exemple) se produit, éliminant ainsi la nécessité d’un nœud de condition explicite après l’étape d’attente. Vous obtenez ainsi une zone de travail de parcours plus propre et une détection de conversion plus réactive.

- **Tester avec des données d’événement réelles dans un sandbox de développement :** utilisez le mode test avec des payloads d’événement réelles (et pas seulement des profils de test) pour vérifier que les champs de schéma d’événement, les jetons de personnalisation et les expressions de condition fonctionnent correctement avec des données de type production.

- **Définir des périodes de refonte de rentrée spécifiques à un événement :** faites correspondre la période de refonte au contexte commercial de l’événement déclencheur. Les parcours d’abandon de panier utilisent généralement un temps de recharge de 4 à 24 heures ; les parcours de confirmation peuvent permettre une rentrée immédiate ; les parcours d’intégration doivent empêcher complètement la rentrée.

- **Surveillez le taux de suppression en tant que mesure d’intégrité :** si le taux de suppression (profils admissibles mais ne recevant pas de messages en raison de limitations de fréquence ou de conditions) dépasse 30 à 40 %, vérifiez si les limitations sont trop restrictives ou si l’événement déclencheur est trop largement défini.

- **parcours de version au lieu de modifier les parcours dynamiques :** un modèle dynamique ne peut pas être modifié directement. Créez une nouvelle version en dupliquant le parcours, en y apportant des modifications, puis en arrêtant l’ancienne version et en publiant la nouvelle. Cela évite de perturber les profils actuellement dans le parcours.

- **Inclure un chemin de secours/par défaut dans les nœuds de condition :** toujours configurer un chemin par défaut (else) dans les nœuds de condition pour gérer les états de profil inattendus. Les profils qui ne correspondent à aucune branche de condition doivent quitter correctement plutôt que de rester bloqués.

### Décisions de compromis

Tenez compte des compromis suivants lors de la conception de votre implémentation de messagerie déclenchée par un événement.

>[!NOTE]
>
>**Compromis : vitesse des messages et pertinence des messages**
>
>La diffusion immédiate des messages (option A) optimise la vitesse, mais peut envoyer des messages à des clients qui se seraient convertis eux-mêmes. La diffusion conditionnelle différée (option B) améliore la pertinence en filtrant les autoconvertisseurs, mais introduit une latence qui peut réduire l’urgence.
>
>- **L’option A privilégie :** la vitesse, la simplicité et les cas d’utilisation de type confirmation où chaque événement justifie un message.
>- **L’option B privilégie :** la pertinence, une fatigue des messages réduite, des cas d’utilisation de type abandon dans lesquels l’autoconversion est courante
>- **Recommandation :** utilisez l’option A pour les messages transactionnels et de confirmation où la vitesse est la valeur principale. Utilisez l’option B pour les messages de récupération et de réengagement lorsque la pertinence l’emporte sur la vitesse. Testez les durées d’attente pour trouver l’équilibre optimal pour chaque cas d’utilisation.

>[!NOTE]
>
>**Compromis : protection de la fréquence par rapport à la couverture des messages**
>
>Des limites de fréquence strictes (option C) empêchent la fatigue, mais peuvent supprimer les messages déclenchés importants lorsque les profils sont proches de leur limite. Les limitations permissives ou absentes optimisent la couverture, mais risquent de surcharger les messages et de fatigue du canal.
>
>- **Les limites strictes favorisent :** expérience client, réputation de la marque, délivrabilité (moins de plaintes contre le spam)
>- **Les limites permissives favorisent :** la couverture des messages, les opportunités de conversion, en évitant les déclencheurs manqués.
>- **Recommandation :** commencez par les limitations standard du secteur (3 à 5 e-mails/semaine, 1 à 2 SMS/semaine, 2 à 3 notifications push/jour) et ajustez-les en fonction des mesures d’engagement et des taux de désabonnement. Attribuez des scores de priorité plus élevés aux messages déclenchés afin qu’ils gagnent des campagnes par lots lorsque les limites sont atteintes.

>[!NOTE]
>
>**Compromis : simplicité du Parcours contre sophistication du parcours**
>
>Les parcours simples (peu de nœuds, pas d’embranchement) sont plus faciles à créer, tester et gérer, mais offrent une adaptation contextuelle limitée. Les parcours sophistiqués (conditions multiples, chemins d’embranchement, vérifications de segment) permettent des réponses plus nuancées, mais augmentent la complexité et le risque d’erreurs.
>
>- **Les parcours simples favorisent :** mise en œuvre plus rapide, débogage plus facile, maintenance moins lourde
>- **Les parcours sophistiqués favorisent :** ciblage plus précis, meilleure personnalisation, réduction des envois inutiles.
>- **Recommandation** commencez par le parcours le plus simple qui répond aux besoins de l’entreprise. Ajoutez une complexité de manière incrémentielle en fonction des données de performances. Un parcours simple qui fonctionne de manière fiable est plus utile qu’un parcours complexe avec des erreurs non détectées.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les fonctionnalités utilisées dans cette implémentation.

### Orchestration des parcours

- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Événements généraux](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Créer un SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Concevoir une notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Fréquence et règles métier

- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Règles métier - Aperçu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [API de limitation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Gestion des conflits et des priorités

- [Prise en main de la gestion des conflits et des priorités](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Scores de priorité](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Rapports et performances

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Collecte et ingestion de données

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation de l’ingestion par flux](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Modélisation des données et schémas

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentation et audiences

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Attributs calculés

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Surveillance et observabilité

- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutoriels et guides

- [Tutoriel sur la création de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
