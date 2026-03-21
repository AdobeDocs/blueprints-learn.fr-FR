---
title: Parcours cross-canal avec prise de décision
description: Découvrez comment orchestrer un parcours à plusieurs étapes incorporant la prise de décision en temps réel pour sélectionner un canal, un contenu ou une offre optimal.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8992'
ht-degree: 2%

---


# Parcours cross-canal avec prise de décision

Ce guide fournit une référence complète d’implémentation pour le parcours cross-canal avec la prise de décision. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin d’orchestrer des parcours à plusieurs étapes et multicanaux qui intègrent la prise de décision en temps réel à un ou plusieurs nœuds de parcours.

Utilisez ce guide pour comprendre l’ensemble des choix d’implémentation, évaluer les compromis et accéder à la documentation Experience League appropriée pour obtenir des instructions de configuration détaillées.

Le parcours cross-canal avec prise de décision est le modèle d’orchestration de campagne le plus sophistiqué de l’écosystème [!DNL Adobe Experience Platform]. Il étend les parcours orchestrés à plusieurs étapes en incorporant la prise de décision en temps réel, à l’aide de [!DNL AJO] Decisioning pour évaluer le contexte actuel d’un profil et sélectionner de manière dynamique le canal, le contenu ou l’offre optimal à un ou plusieurs points de décision dans la zone de travail du parcours.

## Présentation du cas d’utilisation

Les entreprises ont de plus en plus besoin de fournir des parcours clients adaptatifs et personnalisés qui répondent dynamiquement au contexte en temps réel de chaque individu plutôt que de suivre une séquence fixe et prédéterminée. Le canal préféré d’un client, son historique d’engagement, son niveau de fidélité, sa valeur de durée de vie prévue et ses intérêts actuels en matière de produits sont autant d’éléments qui déterminent la meilleure action à entreprendre à chaque point de contact.

Le parcours cross-canal avec prise de décision répond à ce besoin en combinant deux puissantes fonctionnalités de [!DNL AJO] : l&#39;orchestration des parcours (qui gère le flux à plusieurs étapes, le timing, les conditions et la diffusion de canal) et la prise de décision (qui évalue les règles d&#39;éligibilité, applique des stratégies de classement et sélectionne l&#39;offre ou la variante de contenu optimale à chaque point de décision).

Ce modèle est approprié dans les cas suivants :

- Le parcours doit s’adapter dynamiquement au statut en temps réel de chaque profil plutôt que de suivre un canal fixe ou une séquence de contenu
- Plusieurs offres, variantes de contenu ou canaux sont candidats au niveau d’un ou de plusieurs nœuds de parcours. La meilleure option doit être sélectionnée en fonction du contexte du profil
- Le classement assisté par l’IA ou basé sur des formules est nécessaire pour optimiser la sélection des offres sur le parcours
- L’entreprise souhaite consolider la logique de sélection des canaux et la gestion des offres dans un cadre de décision centralisé plutôt que de maintenir une logique d’embranchement complexe

Le public cible comprend des spécialistes du marketing qui gèrent des programmes de cycle de vie, des parcours de fidélité, des séquences de reconquête et des flux d’intégration pour lesquels la personnalisation à grande échelle nécessite une prise de décision automatisée à chaque point de contact.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont atteints par ce modèle d’utilisation.

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.
**KPI : engagement**, taux de conversion, satisfaction de la clientèle (CSAT)

**[Augmenter la fidélité du client et la valeur de durée de vie](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondissez les relations client et optimisez la valeur à long terme par le biais de programmes de fidélité, de récompenses et d’un engagement personnalisé.
**KPI :** valeur de durée de vie du client, conservation, pourcentage de ventes incitatives/croisées

**[Améliorez la fidélisation client](../../business-objectives/customer-experience/improve-customer-retention.md)**
Maintenez l’engagement et le renouvellement des clients existants grâce à des expériences axées sur la valeur et à l’entretien continu des relations.
**KPI** rétention, valeur pour la durée de vie du client, engagement

**[Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.
**KPI :** % de ventes incitatives/croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont le parcours cross-canal avec la prise de décision peut être appliqué dans la pratique.

- **parcours de reconquête adaptative** : parcours à plusieurs étapes dans lequel la prise de décision sélectionne le canal (e-mail, notification push ou SMS) en fonction de l’historique d’engagement de chaque profil, et sélectionne de manière dynamique la meilleure offre d’incitation en fonction de la valeur de durée de vie prévue
- **parcours du cycle de vie de la meilleure action à venir** — La prise de décision détermine les éléments à communiquer à chaque étape du cycle de vie du client, en effectuant une sélection parmi le contenu d’intégration, les offres de vente croisée, les récompenses de fidélité ou les incentives de fidélisation
- **Intégration personnalisée avec sélection dynamique de contenu** — Nouveau parcours d’intégration des clients où chaque point de contact utilise la prise de décision pour sélectionner le contenu de formation au produit, les conseils ou les offres d’activation les plus pertinents
- **parcours de programme de fidélité cross-canal avec récompenses personnalisées** — Les membres du programme de fidélité progressent dans un parcours où Decisioning sélectionne des offres de récompense personnalisées en fonction du niveau, de l&#39;historique d&#39;achat et de l&#39;affinité catégorielle
- **Réengagement dynamique avec optimisation du canal et de l’incitation** — Réengagement client dormant où le canal d’approche et l’incitation sont sélectionnés de manière dynamique pour maximiser la probabilité de réponse
- **Développement du cycle de vie du client avec des recommandations de contenu classées par l’IA** — parcours de développement continu dans lequel la prise de décision classée par l’IA sélectionne le contenu ou les recommandations de produit les plus pertinents à chaque point de contact

## Indicateurs clés de performance

Utilisez les indicateurs de performance clés suivants pour mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’achèvement du parcours | Pourcentage de profils qui ont terminé le parcours complet | Rapport de parcours : terminé / saisi |
| Taux d’acceptation de l’offre | Pourcentage d&#39;offres sélectionnées pour la prise de décision qui sont engagées avec (ayant fait l&#39;objet d&#39;un clic, ayant été échangées) | Rapport Decisioning : clics sur les offres/impressions des offres |
| Taux d’engagement du canal | Taux d’ouvertures et de clics sur chaque canal utilisé dans le parcours | Mesures de diffusion par canal dans le rapport de parcours |
| Taux de conversion | Pourcentage d&#39;acteurs du parcours qui effectuent l&#39;action de conversion cible | Parcours du suivi des événements de sortie pour l’analyse de CJA funnel |
| Taux d’offres de secours | Pourcentage de requêtes de décision renvoyant l’offre de secours au lieu d’une offre personnalisée | Rapport Decisioning : sélections de secours/total de sélections |
| Impact sur la valeur de la durée de vie du client | Variation de la CLV des participants au parcours par rapport à la population témoin | Analyse des cohortes CJA avec comparaison des exclusions |
| Chiffre d’affaires de ventes croisées/incitatives | Chiffre d’affaires incrémentiel attribué aux offres sélectionnées pour la prise de décision | Analyse de l’attribution CJA sur les conversions pilotées par les offres |
| Efficacité du classement des décisions | Différence de performances entre les offres classées par l’IA et la sélection aléatoire/basée sur les priorités | Expérience A/B comparant les stratégies de classement |

## Modèle de cas d’utilisation

**parcours cross-canal avec prise de décision**

Orchestrez un parcours multicanal à plusieurs étapes qui incorpore la prise de décision en temps réel sur un ou plusieurs nœuds pour sélectionner le canal, le contenu ou l’offre optimal.

**Chaîne de fonctions :** évaluation d’audience > exécution de Parcours > nœud de décision > sélection de canal > diffusion de message > compte rendu des performances

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** : orchestration des Parcours (conception de zone de travail à plusieurs étapes, conditions d’entrée, attentes, conditions, critères de sortie), création de messages sur plusieurs canaux, configuration de la surface de canal, gestion des conflits et des priorités
- **[!DNL Adobe Journey Optimizer]Decisioning** — Gestion des offres et des éléments de contenu, règles d&#39;éligibilité, stratégies de classement (priorité, formule, IA), politiques de décision, emplacements, offres de secours
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — Évaluation des audiences pour les segments d’entrée sur le parcours et d’éligibilité des offres, enrichissement du profil avec des attributs calculés et des scores de propension, application du consentement et de la gouvernance
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Banque de profils client en temps réel, Service d’identités pour la résolution cross-canal, la modélisation des données et l’infrastructure d’ingestion

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | [!DNL AJO] sandbox avec des autorisations de parcours, de campagne et de prise de décision configurées. Surfaces de canal pour tous les canaux de diffusion possibles. Rôles utilisateur pour les concepteurs de parcours, les responsables de prise de décision et les auteurs de contenu. | [Présentation des sandbox](https://experienceleague.adobe.com/fr/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/fr/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Le schéma du profil doit inclure les attributs utilisés pour la prise de décision (par exemple, le niveau de fidélité, l’historique d’achats, les préférences de canal, les scores d’engagement). Les schémas Catalogue d&#39;offres et Élément de décision doivent être configurés. Les schémas ExperienceEvent doivent capturer des signaux comportementaux utilisés par les règles d’éligibilité et les formules de classement. | [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Supposé en place | Les attributs de profil et les signaux comportementaux utilisés par la prise de décision doivent être à jour. La diffusion en continu d’événements en temps réel est nécessaire si le parcours utilise des critères d’entrée ou de sortie déclenchés par un événement. Web SDK, Mobile SDK ou la collecte côté serveur doivent être actifs pour les canaux qui alimentent le contexte de prise de décision. | [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home), [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home) |
| Configuration des identités et des profils | Obligatoire | La résolution d’identité cross-canal est essentielle : le parcours doit résoudre les profils par e-mail, push, SMS et web. Les politiques de fusion doivent produire un profil unifié pour la prise de décision. Les espaces de noms d’identité de tous les identifiants client (identifiant CRM, e-mail, ECID, téléphone) doivent être configurés. | [présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | Définition de l&#39;audience d&#39;entrée pour le parcours. Segments supplémentaires utilisés pour les règles d’éligibilité des offres et l’embranchement des conditions dans le parcours. La méthode d’évaluation doit correspondre aux exigences de latence (diffusion en continu pour l’entrée en temps réel, traitement par lots pour le planning). | [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que les scores de propension de Customer AI, les scores d’engagement, les scores de préférence de canal et les calculs de valeur de durée de vie améliorent considérablement la qualité de la prise de décision. Ces attributs de profil enrichis permettent des règles d’éligibilité et des formules de classement plus sophistiquées. | [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview), [Présentation de l’IA dédiée aux clients](https://experienceleague.adobe.com/fr/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Gestion du cycle de vie des données | Recommandé | Les données d’historique des offres et d’événement de décision s’accumulent au fil du temps et doivent avoir des politiques de conservation. L’application du consentement sur plusieurs canaux est essentielle : les profils sans consentement valide pour un canal doivent être exclus du chemin de diffusion de ce canal. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home), [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Étiquetage et application de l’utilisation des données | Recommandé | L’application de la gouvernance sur plusieurs canaux et types d’offres est importante lorsque la prise de décision peut acheminer des profils vers différents canaux avec différentes restrictions d’utilisation des données. Garantit la conformité de la diffusion des offres sur tous les canaux. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home), [Application des politiques](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/enforcement/overview) |
| Surveillance et observabilité | Inclus | La surveillance du parcours et de la prise de décision est essentielle pour les opérations de production. Les alertes pour les échecs d’entrée de parcours, les pics de secours de prise de décision et les erreurs de diffusion permettent de résoudre rapidement les problèmes. | [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview), [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Les rapports de parcours et de prise de décision sont traités dans la phase de création de rapports. L’analyse CJA de l’efficacité de la prise de décision, de l’optimisation de la combinaison de canaux, des performances des offres et du retour sur investissement des parcours fournit les informations nécessaires pour affiner les stratégies de classement et optimiser le parcours au fil du temps. | [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview), [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] ([!DNL AJO])

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de canal | Phase 2 : configuration des canaux | Configurez des surfaces de canal pour tous les canaux que la prise de décision peut sélectionner ou que le parcours utilise (e-mail, SMS, notification push, in-app) |
| Création de messages | Phase 4 : création de messages | Créez le contenu des messages pour chaque canal et intégrez la sortie de décision : emplacements d’offres, blocs de contenu dynamiques, jetons de personnalisation des offres sélectionnées |
| Prise de décision. | Phase 3 : configuration de la prise de décision | Configurez les éléments d’offre, les règles d’éligibilité, les stratégies de classement, les politiques de décision et les offres de secours pour chaque point de décision du parcours |
| Journey Orchestration | Phase 5 : conception et activation du Parcours | Concevez la zone de travail de parcours à plusieurs étapes avec des conditions d’entrée, des nœuds de décision, le routage de canal, les étapes d’attente, les actions de message et les critères de sortie |
| Gestion des conflits et des priorités | Phase 5 : conception et activation du Parcours | Configurez les scores de priorité et la détection des conflits si plusieurs parcours peuvent cibler simultanément les mêmes profils |
| Fréquence et règles métier | Phase 5 : conception et activation du Parcours | Appliquez des limitations de fréquence des messages sur plusieurs canaux pour éviter la surmessagerie dans le parcours multicanal. |
| Rapports et analyse des performances | Phase 6 : Rapports et surveillance | Surveillez les mesures de diffusion par parcours et par nœud, les performances de prise de décision et l’engagement des canaux |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 1 : évaluation de l’audience | Définir et évaluer l’audience d’entrée ou l’événement d’entrée éligible ; créer des segments d’éligibilité utilisés par la prise de décision |
| Enrichissement de profil | Prérequis/Prise en charge | Enrichir les profils avec des attributs calculés et des scores de propension qui améliorent la qualité de la prise de décision |
| Application du consentement et de la gouvernance | Phase 2 : configuration des canaux | Appliquer les préférences de consentement sur tous les canaux ; assurer la diffusion d’offres conformes |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] sandbox [!DNL AJO] est configuré avec les fonctionnalités d’orchestration de parcours et de prise de décision activées
- [ ] Tous les canaux cibles (e-mail, SMS, notification push) ont des surfaces de canal actives et vérifiées
- [ ] schéma de profil comprend les attributs requis pour la prise de décision (niveau de fidélité, historique d’achat, préférences de canal, scores d’engagement)
- [ ] la résolution d’identité cross-canal est configurée : les profils peuvent être résolus sur plusieurs e-mails, jetons push, numéros de téléphone et identifiants web
- [ ] audience d’entrée est définie et évaluée avec une population différente de zéro
- [ ] Le contenu du catalogue d’offres (ressources de création, copie, clauses de non-responsabilité) est approuvé et prêt à être configuré
- [ ] données de consentement sont ingérées et l’application du consentement est active pour tous les canaux cibles
- [ ] Les modèles et fragments de contenu pour chaque canal sont conçus et approuvés
- [ ] règles de limitation de la fréquence sont définies et déployées si l’organisation dispose de politiques de fréquence sur plusieurs campagnes
- [ ] Si vous utilisez la prise de décision classée par l’IA, un minimum de 1 000 événements de conversion existent pour la formation des modèles

## Options de mise en œuvre

Examinez les options suivantes et sélectionnez l’approche qui correspond le mieux à vos besoins.

### Option A : Parcours avec Offer Decisioning (canal fixe, contenu dynamique)

**Idéal pour :** Parcours où la séquence du canal est prédéterminée, mais où le contenu ou l’offre à chaque point de contact doit être sélectionné de manière dynamique ; parcours de fidélité avec récompenses personnalisées, réengagement avec des incitations dynamiques, suivi du cycle de vie avec recommandations de contenu classées par l’IA.

#### Fonctionnement

La zone de travail de parcours définit la séquence fixe des canaux et la durée (par exemple, Jour 0 : e-mail, Jour 3 : notification push, Jour 7 : SMS). À chaque nœud d’action du message, une politique de décision sélectionne la meilleure offre ou le meilleur contenu à inclure dans le message à partir d’un catalogue configuré d’éléments éligibles. Les offres sont gérées dans le catalogue [!DNL AJO] Decisioning avec des règles d&#39;éligibilité qui filtrent les offres pour lesquelles un profil se qualifie, et des stratégies de classement qui déterminent quelle offre éligible est la plus adaptée.

Cette approche sépare le « quand et où » (orchestration des parcours) du « quoi » (prise de décision). Le concepteur de parcours contrôle le flux du canal, tandis que le gestionnaire de prise de décisions contrôle indépendamment le catalogue d&#39;offres, les règles d&#39;éligibilité et la logique de classement. Cette séparation des préoccupations rend l’implémentation plus gérable et permet au catalogue d’offres d’évoluer sans modifier la zone de travail de parcours.

Les emplacements des offres sont directement incorporés dans le contenu des messages à l’aide du Designer Email ou d’autres éditeurs de canal. Lorsque le message est rendu au moment de la diffusion, le moteur de décision évalue l’éligibilité et le classement du profil afin de sélectionner l’offre optimale pour chaque emplacement dans le message.

#### Considérations principales

- La séquence du canal est statique : tous les profils suivent le même chemin de canal, quelles que soient leurs préférences
- La complexité de la prise de décision est moindre, car elle sélectionne uniquement le contenu/les offres, et non les canaux
- Le catalogue d&#39;offres peut être géré indépendamment du parcours
- Les offres de secours doivent être configurées pour chaque emplacement afin de gérer les profils sans offres personnalisées éligibles

#### Avantages

- Canevas de parcours plus simple : pas de logique de branchement pour la sélection de canal
- Séparation claire des préoccupations entre la conception du parcours et la gestion des offres
- Test et validation plus faciles : chaque chemin de canal est déterministe
- Une implémentation moins complexe et un délai de mise sur le marché plus court
- Les modifications du catalogue d&#39;offres prennent effet immédiatement sans modifications de parcours

#### Restrictions

- Impossible d’adapter le canal en fonction du comportement ou des préférences des profils individuels
- Les profils qui préfèrent un canal à un autre reçoivent toujours des messages sur les canaux prédéterminés
- N’optimise pas les taux d’engagement au niveau du canal

#### Références Experience League

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### Option B : Parcours avec sélection de canal dynamique (contenu fixe, canal dynamique)

**Idéal pour :** Parcours où le contenu à chaque point de contact est similaire, mais où le canal doit être sélectionné dynamiquement en fonction du contexte du profil ; reconquête adaptative (e-mail ou notification push ou SMS en fonction de l’engagement), programmes d’action optimale suivante où l’optimisation du canal est l’objectif principal.

#### Fonctionnement

Le parcours utilise des nœuds de condition informés par les attributs de profil (tels que les scores de préférence de canal, le dernier canal d’engagement ou le statut de consentement) ou la sortie de prise de décision pour acheminer les profils vers différents chemins de canal. Chaque chemin diffuse du contenu spécifique au canal par le biais de son propre nœud d’action de message. La logique de prise de décision détermine le canal le plus susceptible de susciter l’engagement en fonction de l’historique comportemental du profil.

La sélection de canal peut être mise en œuvre à l’aide de nœuds de condition de parcours avec des évaluations d’attribut de profil (par exemple, si `channelPreference = "push"` acheminez vers le chemin push) ou en utilisant la prise de décision avec des éléments spécifiques au canal où chaque « offre » représente un canal et où la stratégie de classement détermine le meilleur canal.

Cette approche optimise le canal de diffusion tout en conservant une cohérence relative du contenu sur l’ensemble des canaux. Le contenu du message doit être créé pour chaque canal possible et les surfaces des canaux doivent être configurées pour tous les canaux candidats.

#### Considérations principales

- Nécessite des variantes de contenu de message pour chaque canal candidat
- Les surfaces de canal doivent être actives pour tous les canaux possibles
- La logique de condition ou la configuration de prise de décision doit tenir compte du consentement : les profils sans consentement SMS ne peuvent pas être acheminés vers le chemin SMS
- La zone de travail de parcours est plus complexe avec des chemins d’embranchement pour chaque canal

#### Avantages

- Optimise la sélection de canaux pour chaque profil individuel
- Augmente l’engagement global en atteignant les profils sur leur canal préféré
- Respecte automatiquement le consentement spécifique au canal par le biais du routage avec consentement
- Peut intégrer l’historique d’engagement et les scores de préférences de canal dans les décisions de routage

#### Restrictions

- Zone de travail de parcours plus complexe avec plusieurs branches de canal
- Le contenu doit être créé séparément pour chaque canal (bien que l’intention du message soit la même)
- Plus difficile à tester : doit valider tous les chemins de canal possibles
- La personnalisation du contenu au sein de chaque canal est statique (pas d’Offer Decisioning)

#### Références Experience League

- [Activité de condition](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option C : parcours adaptatif complet (canal dynamique + contenu dynamique)

**Idéal pour :** Personnalisation maximale : le canal et le contenu/l’offre sont sélectionnés de manière dynamique au niveau de chaque nœud. Convient aux segments de clientèle à forte valeur ajoutée, aux programmes de fidélité sophistiqués et aux organisations ayant des pratiques de prise de décision matures et des données de profil riches.

#### Fonctionnement

Cette option combine les options A et B. Le parcours utilise la prise de décision à deux niveaux : tout d’abord, pour déterminer le canal à utiliser pour chaque point de contact et, ensuite, pour déterminer le contenu ou l’offre à diffuser dans le canal sélectionné. Chaque point de décision du parcours évalue le contexte actuel du profil pour effectuer la sélection du canal et du contenu.

L’implémentation nécessite une configuration de prise de décision complète avec des politiques de décision pour la sélection de canal et la sélection de contenu/d’offres. La sélection de canal peut utiliser une politique de décision où chaque élément représente un canal avec des règles d’éligibilité basées sur le consentement et l’engagement, tandis que la sélection de contenu utilise une politique de décision distincte avec des éléments d’offre classés par pertinence.

Il s’agit de la variante la plus complexe qui nécessite l’intégration la plus profonde entre l’orchestration du parcours et la prise de décision. Il offre le plus haut degré de personnalisation, mais exige également le plus de configuration, de tests et de gestion continue.

#### Considérations principales

- Nécessite deux niveaux de prise de décision : sélection de canal et sélection de contenu
- La complexité de la zone de travail de parcours est maximale avec l’embranchement et la prise de décision imbriqués à chaque nœud
- Tests approfondis requis pour toutes les combinaisons de contenu de canal possibles
- Requiert des données de profil riches (historique d’engagement, préférences de canal, affinité de produit, scores de propension) pour une prise de décision efficace
- La prise de décision classée par l’IA bénéficie considérablement des attributs calculés

#### Avantages

- Personnalisation maximale : chaque point de contact est optimisé pour le canal et le contenu
- Meilleur potentiel d’engagement et de conversion pour des implémentations bien configurées
- Centralise toute la logique de personnalisation dans la prise de décision plutôt que les branches de parcours statiques
- Peut continuellement s’améliorer grâce à l’apprentissage des modèles de classement par l’IA

#### Restrictions

- Mise en œuvre la plus complexe et le plus long délai de mise sur le marché
- Nécessite la préparation la plus complète du catalogue d’offres et du contenu du canal
- Plus difficile à résoudre lorsque des problèmes de diffusion surviennent
- Nécessite une infrastructure de données mature avec des attributs de profil riches
- Le classement par l’IA nécessite un volume d’événement de conversion suffisant pour la formation des modèles

#### Références Experience League

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Comparaison des options

Utilisez le tableau suivant pour comparer les trois options d’implémentation en un coup d’œil.

| Critères | Option A : Offer Decisioning | Option B : canal dynamique | Option C : adaptatif complet |
| --- | --- | --- | --- |
| Idéal pour | Séquence de canal fixe, contenu dynamique | Optimisation des canaux, contenu cohérent | Personnalisation maximale dans les deux dimensions |
| Complexité | Moyenne | Medium-Grand | Élevée |
| Zone de travail des parcours | Simple (linéaire avec prise de décision au niveau des nœuds d’action) | Modéré (embranchement pour les chemins de canal) | Complexe (embranchement imbriqué avec prise de décision à plusieurs niveaux) |
| Portée de la prise de décision | Sélection de contenu/offre uniquement | Sélection de canal uniquement | Sélection de canal et de contenu |
| Exigences de contenu | Un ensemble de contenu par canal (avec des emplacements d’offre) | Contenu pour chaque canal candidat | Contenu avec emplacements d’offres pour chaque canal candidat |
| Besoins en données de profil | Modéré (attributs d’éligibilité de l’offre) | Modéré (préférence de canal, engagement) | Élevée (attributs de canal et d’offre) |
| Délai de commercialisation | Plus rapide | Modéré | Le plus long |
| Gestion continue | Gestion des catalogues d’offres | Gestion de la logique de routage des canaux | Le catalogue d’offres et le routage de canal |
| Profondeur de Personalization | Le contenu varie, canal fixe | Le canal varie, le contenu est similaire | Le canal et le contenu varient |

### Choisir la bonne option

Suivez les conseils suivants pour déterminer la meilleure option pour votre situation.

- **Commencez par l’option A** si votre stratégie de canal est déjà définie (par exemple, « Nous envoyons toujours d’abord un e-mail, puis une notification push et ensuite un SMS ») et que le principal besoin de personnalisation est de sélectionner la bonne offre ou le bon contenu à chaque point de contact. Il s’agit du point de départ le plus courant pour les organisations qui découvrent la prise de décision.

- **Choisissez l’option B** si l’optimisation du canal est votre objectif principal : vous souhaitez atteindre chaque client sur le canal avec lequel il est le plus susceptible d’interagir, mais le contenu du message est relativement cohérent sur l’ensemble des canaux. Cela nécessite des données de préférence de canal sur les profils.

- **Choisissez l’option C** uniquement lorsque vous disposez d’une infrastructure de prise de décision mature, de données de profil riches (y compris des attributs calculés et des scores de propension), d’un catalogue d’offres bien renseigné et de la capacité organisationnelle à gérer la complexité. De nombreuses entreprises commencent par l’option A ou B et évoluent vers l’option C à mesure que leur maturité décisionnelle augmente.

- **Si vous n’êtes pas sûr** commencez par l’option A. Il offre une personnalisation significative avec la complexité la plus faible et le catalogue d’offres que vous créez pour l’option A est directement réutilisable si vous passez ultérieurement à l’option C.

## Phases de mise en œuvre

Les phases suivantes décrivent l’implémentation de bout en bout de ce modèle de cas d’utilisation.

### Phase 1 : évaluation de l’audience

**Fonction d’application :** [!DNL RT-CDP] : évaluation de l’audience

Cette phase configure l’audience d’entrée qui détermine les profils qui rejoignent le parcours et les segments supplémentaires utilisés pour les règles d’éligibilité de l’offre ou l’embranchement des conditions dans le parcours. La définition de l’audience est la base de toute logique de parcours et de prise de décision en aval.

#### Décision : type d&#39;entrée

Comment les profils doivent-ils entrer sur le parcours par le biais d’une lecture d’audience planifiée ou d’un déclencheur d’événement en temps réel ?

>[!NOTE]
>Sélectionnez un type d’entrée en fonction du timing et des exigences de déclenchement de votre parcours.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Lecture d’audience (entrée par lots) | Programmes de cycle de vie, parcours de fidélité, campagnes de réengagement planifiées | Les profils entrent par lots à des heures planifiées ; l’audience est évaluée au moment de la lecture ; prend en charge de grandes tailles d’audience |
| Qualification de l’audience (streaming) | Parcours déclenchés par le comportement où l’entrée doit se produire lorsqu’un profil entre ou sort d’un segment | Entrée en temps quasi réel ; nécessite une définition de segment éligible à la diffusion en continu ; adapté aux parcours basés sur des jalons |
| Événement unitaire (déclencheur d’événement) | Un événement spécifique doit déclencher le parcours (par exemple, achat, abandon de panier, enregistrement). | Entrée en temps réel sur l’événement ; nécessite une configuration de schéma d’événement ; limitée à 5 000 événements/seconde |

#### Décision : méthode d’évaluation de l’audience

À quelle vitesse l’audience doit-elle qualifier les profils ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Lot | Des mises à jour quotidiennes ou périodiques de l’audience sont suffisantes ; des parcours planifiés de style campagne . | Traite jusqu’à 24 millions de profils par tâche ; basé sur un planning ; la plupart des expressions de règle de segment sont prises en charge. |
| Diffusion en continu | L’appartenance à une audience en temps réel est nécessaire pour une entrée déclenchée par un événement ou basée sur une qualification | Temps quasi réel ; jeu de fonctions de règles de segment limité ; aucune agrégation basée sur le temps |
| Edge | Qualification de la même session requise | Latence en millisecondes ; vérifications d’attribut simples uniquement ; limitées aux attributs de profil Edge |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle

- Définissez l’audience d’entrée à l’aide du créateur de segments avec des expressions de règle de segment ciblant les attributs de profil et les événements comportementaux pertinents
- Créez des segments d’éligibilité supplémentaires si les règles d’éligibilité des offres font référence à l’appartenance à un segment (par exemple, « Clients à valeur élevée », « Niveau or de fidélité »)
- Vérifiez que la population de l’audience est différente de zéro avant de passer à la configuration du parcours
- Sélectionnez la politique de fusion qui produit la vue de profil unifiée nécessaire à la prise de décision

#### Documentation Experience League

- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/pql/overview)

### Phase 2 : configuration des canaux

**Fonction d’application :** [!DNL AJO] : configuration de canal

Cette phase configure les surfaces des canaux pour chaque canal que le parcours peut utiliser pour la diffusion des messages. Tous les canaux candidats doivent avoir des surfaces actives vérifiées avant que les messages puissent être créés ou que le parcours puisse être publié. Pour ce modèle, vous configurez généralement des surfaces pour les e-mails, SMS et notifications push au minimum, et potentiellement in-app ou web si la prise de décision peut sélectionner ces canaux.

#### Décision : canaux à configurer

Quels canaux sont candidats pour le parcours, soit en tant qu’étapes de parcours fixes (options A/B), soit en tant que canaux sélectionnables pour la prise de décision (options B/C) ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail uniquement | Parcours à canal unique avec Offer Decisioning (option A, e-mail uniquement) | Configuration la plus simple : nécessite la délégation de sous-domaines et le préchauffage d’adresses IP |
| E-mail + Push | Parcours à deux canaux ; commun aux parcours axés sur l’engagement | La notification push nécessite des informations d’identification APNs/FCM ; SDK doit être intégré à l’application mobile |
| E-mail + SMS + Push | Parcours cross-canal complet ; le plus courant pour les options B et C | SMS nécessite les informations d’identification du fournisseur (Sinch, Twilio, Infobip) ; chaque canal a besoin de sa propre surface |
| E-mail + SMS + Push + In-App | Couverture de canal maximale, y compris les surfaces en session | In-app nécessite une configuration de SDK mobile et de surface d’application |

#### Décision : méthode de délégation de sous-domaine (e-mail)

Comment le sous-domaine d’envoi doit-il être délégué à Adobe ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Délégation complète | L’entreprise souhaite qu’Adobe gère tous les enregistrements DNS pour le sous-domaine d’envoi | Configuration la plus simple : Adobe gère SPF, DKIM et DMARC, ce qui réduit le contrôle sur le DNS |
| Délégation CNAME | L’entreprise doit conserver le contrôle des enregistrements DNS | Configuration plus complexe ; le client gère le DNS ; offre plus de flexibilité |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** Administration > Canaux > Surfaces des canaux > Créer une surface

- Pour les e-mails : configurer le sous-domaine, le groupe d’adresses IP, le nom de l’expéditeur, l’adresse de réponse et la gestion des désabonnements
- Pour les SMS : configurer les informations d’identification du fournisseur SMS et le numéro de l’expéditeur
- Pour les notifications push : configuration des identifiants APN et FCM pour iOS et Android
- Vérifiez que chaque surface a le statut Actif avant de continuer
- Confirmer que le préchauffage de l’adresse IP est terminé pour les adresses IP d’envoi d’e-mail

#### Documentation Experience League

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Configurer le canal SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 3 : configuration de la prise de décision

**Fonction d’application :** [!DNL AJO] : prise de décision

Cette phase configure l’ensemble du cadre de prise de décision, y compris les emplacements, les règles d’éligibilité, les offres personnalisées, les offres de secours, les qualificateurs de collection, les collections, les stratégies de classement et les politiques de décision. Cette phase permet de créer la logique de décision qui sera appelée aux points de décision du parcours.

#### Décision : portée de la prise de décision

Que doit sélectionner la prise de décision : offres/contenu (option A), canaux (option B) ou les deux (option C) ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Sélection d’offres/de contenus uniquement | La séquence de canal est fixe ; la personnalisation se trouve dans le contenu | Les politiques de décision ciblent les éléments d’offre avec des représentations de contenu par emplacement |
| Sélection de canal uniquement | Le contenu est cohérent ; l’optimisation se fait sur le canal de diffusion | Les éléments de décision représentent des canaux ; l’éligibilité inclut les contrôles de consentement ; le classement utilise les données d’engagement |
| Canal et contenu | Personnalisation adaptative complète sur le canal et le contenu | Nécessite deux niveaux de politiques de décision ; personnalisation la plus complexe, mais la plus élevée |

#### Décision : stratégie de classement

Comment les offres éligibles doivent-elles être classées pour sélectionner la meilleure ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Basé sur la priorité (manuel) | Classement simple où les règles métier déterminent l’importance de l’offre | Chaque offre obtient un score de priorité ; la priorité la plus élevée gagne ; déterministe et facile à comprendre. |
| Basé sur une formule (expression personnalisée) | Le classement doit prendre en compte les attributs de profil (par exemple, la valeur vie client, le niveau, le score d’affinité) | La formule de classement personnalisé évalue le contexte du profil ; plus dynamique que la priorité ; aucun ML requis |
| Classement par l’IA (optimisation automatique) | Le classement doit être optimisé automatiquement en fonction des données de conversion historiques | Le modèle d’IA tire les leçons des événements de conversion ; nécessite au minimum 1 000 événements pour la formation ; s’améliore en permanence |

#### Décision : limitation de l’offre

Doit-il y avoir des limites au nombre d’affichages d’une offre ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Limite par profil | Empêcher l’affichage répété de la même offre au même profil | Protège contre la fatigue des offres et le décalage possible en cas de débit élevé |
| Limite globale | Limiter le nombre total d’impressions sur tous les profils (par exemple, les promotions d’inventaire limitées) | Contrôle l’exposition totale ; utile pour les offres limitées par l’offre |
| Pas de limitation | Chaque impression éligible doit afficher l’offre | La plus simple ; adaptée au contenu évolutif ou aux offres illimitées |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** Composants > Gestion des décisions > Emplacements / Offres / Décisions

- Créez des emplacements pour chaque combinaison de canal et de type de contenu (par exemple, bannière HTML d’e-mail, JSON push, texte SMS).
- Définissez des règles d’éligibilité à l’aide d’expressions de règle de segment qui font référence aux attributs de profil ou à l’appartenance à une audience
- Créez des offres personnalisées avec des représentations pour chaque emplacement, attribuez des règles d’éligibilité et définissez une priorité
- Créer une offre de secours couvrant tous les emplacements : cette option est renvoyée lorsqu’aucune offre personnalisée ne se qualifie
- Organisez les offres en collections à l’aide de qualificateurs de collection (balises)
- Configurer la stratégie de classement : en fonction des priorités, des formules ou de l’IA
- Créez des politiques de décision qui lient les emplacements, les collections, la stratégie de classement et l&#39;offre de secours
- Valider toutes les offres avant leur sélection par la prise de décision

#### Là où les options divergent

**Pour L’Option A (Offer Decisioning) :**
Créez des emplacements et des offres axés sur la personnalisation du contenu dans chaque canal (par exemple, offre de bannière de héros d’e-mail, offre de pied de page d’e-mail, offre de corps de notification push). Les politiques de décision sélectionnent le meilleur contenu pour chaque emplacement dans le message.

**Pour L’Option B (Sélection Dynamique De Canaux) :**
Créez des éléments de décision qui représentent chaque canal. Les règles d’éligibilité incluent les contrôles de consentement (par exemple, un profil doit avoir un consentement par SMS pour être éligible à l’élément SMS). Le classement utilise les scores d’engagement du canal ou les expressions basées sur des formules.

**Pour L’Option C (Adaptatif Complet) :**
Configurez deux couches de prise de décision : un ensemble de politiques de décision pour la sélection de canal et un ensemble distinct pour la sélection de contenu/d’offres dans le canal sélectionné. Les deux couches nécessitent des emplacements, des offres, des règles d’éligibilité et des stratégies de classement.

#### Documentation Experience League

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4 : création de messages

**Fonction d’application :** [!DNL AJO] : création de messages

Cette phase configure le contenu du message pour chaque canal et point de contact du parcours, en intégrant la sortie de prise de décision (contenu d’offre sélectionné) dans les modèles de message. Chaque nœud d’action de message du parcours nécessite du contenu créé avec la surface de canal appropriée, des jetons de personnalisation et des intégrations d’emplacements d’offres.

#### Décision : approche du contenu

Comment le contenu du message doit-il être créé pour chaque canal ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Basé sur des modèles | L’entreprise a établi des modèles de marque ; la cohérence est importante | Création plus rapide ; garantit la cohérence de la marque ; peut limiter la flexibilité de conception |
| Créer en partant de zéro | Création unique pour ce parcours ; aucun modèle existant | Contrôle de conception complet ; temps de création plus long ; utilisation du glisser-déposer de Designer par e-mail. |
| Importer HTML | L’équipe Creative produit HTML en externe ; importe dans [!DNL AJO] | Préserve le workflow de conception externe ; nécessite la compatibilité d’HTML avec Email Designer. |

#### Décision : portée de Personalization

Quel niveau de personnalisation les messages doivent-ils inclure au-delà de la sortie de prise de décision ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Personnalisation de base (nom, salutations) | Besoins de personnalisation minimaux au-delà de la sélection d’offres | Expressions Handlebars simples ; faible complexité |
| Blocs de contenu conditionnel | Différentes sections de contenu pour différents segments ou attributs | Utilise des règles de contenu dynamique ; le contenu varie en fonction de l’attribut de profil ou de l’appartenance au segment |
| Personnalisation complète avec intégration de la prise de décision | Emplacements d’offres intégrés dans des messages, combinés à une personnalisation basée sur les profils | Combine la sortie Offer Decisioning avec les jetons de personnalisation Handlebars ; expérience la plus riche |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** sélectionnez l’action de campagne ou de parcours > Modifier le contenu > Designer d’e-mail / Éditeur de canal

- Créez le contenu des messages pour chaque canal utilisé dans le parcours (e-mail, SMS, notification push, in-app).
- Incorporer les emplacements de décision d’offre dans le contenu du message où les offres sélectionnées pour la prise de décision doivent apparaître
- Ajoutez des expressions de personnalisation à l’aide de la syntaxe Handlebars pour les attributs de profil (par exemple, `{{profile.person.name.firstName}}`).
- Configurer des blocs de contenu conditionnel pour la messagerie spécifique à un segment
- Créer des fragments de contenu réutilisables pour les éléments partagés (en-têtes, pieds de page, clauses de non-responsabilité)
- Prévisualiser et tester avec des profils types pour vérifier que les rendus de personnalisation sont corrects
- Envoyer des BAT aux parties prenantes pour révision

#### Là où les options divergent

**Pour L’Option A (Offer Decisioning) :**
Chaque message comprend des emplacements d’offre où apparaît le contenu sélectionné pour la prise de décision. La disposition des messages est cohérente, mais la zone d’offre affiche dynamiquement la meilleure offre pour chaque profil.

**Pour L’Option B (Sélection Dynamique De Canaux) :**
Chaque canal possède son propre contenu de message créé séparément. Le contenu est similaire sur l’ensemble des canaux, mais adapté aux contraintes des canaux (e-mail HTML ou texte SMS ou format de notification push).

**Pour L’Option C (Adaptatif Complet) :**
Chaque canal possède son propre contenu de message avec des emplacements d’offres incorporés. Le canal et le contenu de l’offre dans ce canal sont sélectionnés de manière dynamique.

#### Documentation Experience League

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Créer un SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/create-sms)
- [Concevoir une notification push](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/push/design-push)

### Phase 5 : conception et activation du Parcours

**Fonction d’application :** [!DNL AJO] : Journey Orchestration, [!DNL AJO] : Gestion des conflits et des priorités, [!DNL AJO] : Fréquence et règles métier.

Cette phase configure la zone de travail de parcours complète, y compris la configuration d’entrée, les nœuds de décision liés aux politiques de décision configurées, les divisions de condition pour le routage du canal (options B/C), les nœuds d’action de message pour chaque chemin de canal, les nœuds d’attente entre les points de contact, les critères de sortie, les paramètres de conflit/priorité et les règles de limitation de fréquence. Cette phase assemble tous les composants précédemment configurés dans le flux de parcours orchestré et l’active.

#### Décision : politique de rentrée

Les profils peuvent-ils rejoindre à nouveau le parcours après avoir terminé ou quitté ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Autoriser la rentrée (avec le temps de recharge) | Parcours récurrents où les profils peuvent être à nouveau qualifiés (par exemple, renouvellement de fidélité trimestriel) | Définir une période de recharge (minimum 5 minutes) pour empêcher une rentrée immédiate ; le profil redémarre depuis le début |
| Pas de rentrée | Parcours ponctuels où chaque profil ne doit parcourir qu’une seule fois (par exemple, intégration). | Le profil ne peut pas entrer à nouveau une fois terminé ou quitter ; comportement plus simple |

#### Décision : critères de sortie

Dans quelles conditions un profil doit-il être supprimé du parcours avant l’achèvement de l’opération ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Modification de l’appartenance à l’audience | Le profil doit quitter l’audience d’entrée ou entrer dans une audience de suppression | Sortie en temps réel lors d’une modification de segment ; utile pour les sorties « converties » ou « désactivées » |
| Occurrence de l’événement | Un événement spécifique (par exemple, achat, désabonnement) doit déclencher la sortie | Sortie en temps réel sur l’événement ; nécessite la configuration du schéma d’événement. |
| Timeout | La durée maximale dans le parcours a expiré | La valeur maximale par défaut est de 91 jours ; empêche les profils de rester indéfiniment |

#### Décision : délai d’expiration du Parcours

Quelle est la durée maximale pendant laquelle un profil peut rester dans le parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| 91 jours (maximum) | Parcours de cycle de vie à long terme avec séquences de maturation étendues | Durée maximale autorisée ; les profils se ferment après 91 jours, indépendamment de la situation |
| Durée raccourcie personnalisée | Campagnes limitées dans le temps ou parcours saisonniers | Défini en fonction de la logique commerciale du parcours ; une temporisation plus courte réduit les profils obsolètes |

#### Décision : paramètres de conflit et de priorité

Ce parcours doit-il avoir une notation prioritaire pour la résolution de conflit avec d’autres parcours/campagnes ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Haute priorité (70-100) | Les parcours client critiques (fidélisation, fidélisation) qui doivent avoir la priorité | Une priorité plus élevée gagne lorsque plusieurs communications sont en concurrence ; utilisez avec parcimonie. |
| Priorité de Medium (30-69) | Parcours de cycle de vie standard | Priorité équilibrée ; peut être supprimée par les communications de priorité plus élevée |
| Priorité faible (0-29) | Parcours supplémentaires ou d&#39;information | Sera supprimé lors de la concurrence avec des communications plus importantes |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** Parcours > Créer un Parcours

- Création du parcours et configuration des propriétés (nom, description, fuseau horaire, temporisation)
- Configurer l’entrée : Lecture d’audience (pour le lot) ou déclencheur d’événement (pour le temps réel)
- Ajouter des nœuds de décision liés aux politiques de décision configurées à partir de la phase 3
- Ajouter des divisions de condition pour le routage de canal en fonction de la sortie de décision ou des attributs de profil (options B/C)
- Ajoutez des nœuds d’action de message pour chaque chemin de canal, en établissant un lien vers le contenu créé à partir de la phase 4
- Ajouter des nœuds d’attente entre les points de contact (minimum 1 heure pour les parcours lus par l’audience)
- Définir les critères de sortie (changement d’audience, événement, délai d’expiration)
- Attribuer un score de priorité pour la résolution des conflits
- Configurer le capping de la fréquence si des limites de fréquence entre parcours s’appliquent
- Tester le parcours en mode test avec des profils de test avant la publication
- Publier le parcours pour le rendre actif

#### Là où les options divergent

**Pour L’Option A (Offer Decisioning) :**
Le canevas de parcours est linéaire avec les politiques de décision intégrées dans chaque nœud d’action de message. Aucun embranchement pour la sélection de canal. La décision d’offre est prise au moment du rendu du message dans le nœud d’action.

**Pour L’Option B (Sélection Dynamique De Canaux) :**
Après chaque étape d’attente, ajoutez un nœud de condition qui évalue les critères de sélection de canal (attributs de profil, sortie de prise de décision ou statut de consentement). Chaque branche de condition mène à un nœud d’action de message spécifique au canal. Incluez un chemin par défaut/else pour les profils qui ne correspondent à aucune condition.

**Pour L’Option C (Adaptatif Complet) :**
Combinez les nœuds de condition de sélection de canal avec les nœuds d’action de message incorporés à une politique de décision. À chaque point de contact : tout d’abord, une condition ou une décision détermine le canal ; ensuite, dans l’action de message du canal sélectionné, une politique de décision sélectionne l’offre/le contenu optimal.

#### Documentation Experience League

- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Activité Lecture d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Activité de condition](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Scores de priorité](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Gestion des conflits et des priorités - Aperçu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Phase 6 : Rapports et suivi

**Fonction d’application :** [!DNL AJO] : Rapports et analyse des performances

Cette phase configure le suivi des performances du parcours et de la prise de décision par le biais de rapports dynamiques (pendant l’exécution) et de rapports historiques (après l’achèvement). Mesures spécifiques à Decisioning, notamment la distribution de la sélection des offres, les taux de secours et l&#39;efficacité du classement. Facultativement, l’analyse de l’espace de travail CJA pour le parcours cross-canal profond et l’analyse du retour sur investissement des décisions.

#### Décision : Profondeur des rapports

Quel niveau d’analyse des rapports est nécessaire ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| [!DNL AJO] rapports natifs uniquement | Suivi opérationnel des mesures de diffusion et d’engagement | Rapports dynamiques et historiques intégrés ; aucune configuration supplémentaire ; limité à [!DNL AJO] mesures |
| [!DNL AJO] + analyse CJA | Analyse cross-canal approfondie, efficacité de la prise de décision, retour sur investissement du parcours, analyse des cohortes | Nécessite une connexion CJA et une vue de données ; fournit des fonctionnalités d’attribution, de funnel et d’analyse des cohortes |

#### Détails de configuration clés

**Navigation dans l’interface utilisateur :** Parcours > Sélectionner un parcours > Rapport dynamique / Rapport à toute heure

- Surveillez le rapport dynamique de parcours lors de l’exécution initiale pour les mesures d’entrée, de sortie et par nœud
- Examiner les performances de la prise de décision : distribution de la sélection d’offres, taux d’offres de secours, efficacité du classement
- Une fois le parcours terminé, consultez les rapports historiques pour une analyse funnel de bout en bout
- Pour l’analyse CJA : assurez-vous que la connexion CJA inclut des jeux de données [!DNL AJO] (événement de retour de message, événement de suivi des e-mails)
- Créez l’espace de travail CJA avec des panneaux pour l’analyse du mix de canaux, la comparaison des performances des offres et les entonnoirs de conversion de parcours
- Création d’annotations pour les dates de lancement du parcours et les modifications de configuration importantes

#### Documentation Experience League

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considérations relatives à la mise en œuvre

Examinez les mécanismes de sécurisation suivants, les écueils les plus courants, les bonnes pratiques et les décisions de compromis avant et pendant la mise en œuvre.

### Mécanismes de sécurisation et limites

- Maximum de 500 parcours en direct par sandbox — [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/get-started/guardrails)
- La durée de parcours maximale est de 91 jours (délai d’expiration global)
- 50 activités maximum par canevas de parcours
- Les parcours Lecture d’audience peuvent traiter jusqu’à 20 000 profils par seconde
- Les parcours d’événement unitaire prennent en charge jusqu’à 5 000 événements par seconde par sandbox
- Maximum de 10 000 offres personnalisées approuvées par sandbox
- Maximum de 30 emplacements par décision
- SLA du temps de réponse de diffusion des offres : moins de 500 ms à P95 pour les requêtes à portée unique
- Les modèles de classement par l’IA nécessitent au moins 1 000 événements de conversion pour la formation
- Maximum de 10 surfaces de canal par type de canal par sandbox
- Les étapes d’attente ont une durée minimale d’une heure pour les parcours lus par l’audience
- Le minimum de refroidissement de rentrée du parcours est de 5 minutes
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de Platform](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)

### Pièges courants

**La décision renvoie toujours une offre de secours :** vérifiez que les offres personnalisées sont approuvées (sans état de brouillon), dans leur période de validité, et que les règles d’éligibilité correspondent aux attributs des profils cibles. Vérifiez que les limites de limitation de l’offre n’ont pas été atteintes. Testez avec un profil qui doit clairement se qualifier pour une offre personnalisée.

**Le Parcours publie mais les profils n’entrent pas :** pour les parcours lus par l’audience, vérifiez que l’audience a une population évaluée supérieure à zéro. Pour les parcours déclenchés par un événement, vérifiez le schéma d’événement, les conditions de déclenchement et assurez-vous que les événements sont envoyés. Vérifiez que la politique de fusion de l’audience d’entrée correspond à la politique de fusion attendue du parcours.

**Formule de classement non appliquée correctement :** vérifiez que la syntaxe de la formule est valide et fait référence à des attributs de profil accessibles. Les erreurs de formule reviennent silencieusement au classement par priorité, sans avertissement. Le classement des tests avec des profils ayant des valeurs d’attribut différentes pour confirmer la formule produit l’ordre attendu.

**Le routage de canal ignore le consentement :** les nœuds de condition pour la sélection de canal doivent inclure des vérifications de consentement. Un profil sans consentement SMS ne doit pas être acheminé vers le chemin SMS. Intégrez le consentement dans les règles d’éligibilité lors de l’utilisation de la prise de décision pour la sélection de canal (option B/C).

**Les compteurs de limitation d’offre sont en retard par rapport à un débit élevé :** les compteurs de limitation d’offre peuvent avoir un retard de quelques secondes dans les scénarios à débit élevé. Si la limitation exacte est critique, utilisez des limitations globales avec une mémoire tampon ou combinez-les avec des règles de fréquence.

La zone de travail de **Parcours dépasse la limite de 50 activités :** les parcours complexes de l’option C avec de nombreuses branches de canal et des nœuds de décision peuvent approcher la limite de 50 activités. Simplifiez en consolidant la logique des conditions, en réduisant le nombre de points de contact ou en divisant plusieurs parcours séquentiels.

**Les décisions Edge renvoient une personnalisation vide :** si vous utilisez la prise de décision Edge pour les décisions en temps réel, assurez-vous que le service [!DNL Adobe Journey Optimizer] est activé pour le flux de données et que la portée de décision est correctement formatée. Les décisions Edge sont limitées aux attributs de profil disponibles dans le magasin de profils edge.

### Bonnes pratiques

**Commencez simplement et évoluez :** commencez par l’option A (canal fixe, offres dynamiques) pour valider le cadre de prise de décision, puis évoluez vers les options B ou C à mesure que la maturité des données et la capacité organisationnelle augmentent.

**Investir dans l’enrichissement des profils :** les attributs calculés tels que les scores d’engagement, les indices de préférence de canal et les scores de propension de l’IA dédiée aux clients améliorent considérablement la qualité de la prise de décision. Créez ces attributs d’enrichissement avant de configurer des stratégies de classement complexes.

**Toujours configurer les offres de secours :** chaque politique de décision doit avoir une offre de secours. Concevez des offres de secours en tant que contenu à valeur réelle (et non en tant qu’espaces réservés vides), car elles servent des profils qui ne remplissent les critères d’aucune offre personnalisée.

**Test avec des profils différents :** utilisez le mode test avec des profils qui représentent différents chemins d’éligibilité, préférences de canal et combinaisons d’attributs. Vérifiez que chaque chemin de parcours possible et le résultat de la prise de décision fonctionnent correctement avant la publication.

**Surveiller les taux de secours en tant que mesure d’intégrité :** un taux d’offres de secours élevé indique que les règles d’éligibilité sont trop restrictives ou que le catalogue d’offres ne couvre pas suffisamment de segments de profil. Visez un taux de secours inférieur à 20 % pour une prise de décision bien configurée.

**Utilisez les fragments de contenu pour la cohérence cross-canal :** créez des fragments de contenu partagés (en-têtes, pieds de page, clauses de non-responsabilité légale, blocs de désabonnement) pour maintenir la cohérence de la marque sur les e-mails, SMS et messages push du parcours.

**Configurer les critères de sortie de manière proactive :** définissez des critères de sortie pour les événements de conversion (par exemple, l’achat, l’enregistrement) afin que les profils qui effectuent l’action souhaitée soient immédiatement supprimés du parcours au lieu de continuer à recevoir des messages.

**Attribuez des scores de priorité significatifs :** lorsque vous exécutez plusieurs parcours et campagnes, attribuez des scores de priorité en fonction de l’impact sur l’entreprise. Les parcours de rétention de grande valeur doivent avoir une priorité supérieure à la communication informative.

### Décisions de compromis

Examinez les compromis suivants pour éclairer vos choix d’implémentation.

#### Complexité de la prise de décision par rapport au délai de mise sur le marché

Une prise de décision plus sophistiquée (option C avec classement IA) offre une personnalisation plus élevée, mais nécessite beaucoup plus de temps de configuration, de préparation des données et de test.

- **L’option A/B privilégie** déploiement plus rapide, des tests plus simples et une gestion continue moins lourde
- **L’option C privilégie** personnalisation maximale, optimisation continue pilotée par l’IA, potentiel d’engagement le plus élevé.
- **Recommandation :** commencez par l’option A ou B pour le lancement initial. Collectez en parallèle des données de performances et créez des attributs d’enrichissement de profil. Évoluez vers l’option C lorsque vous disposez d’au moins 1 000 événements de conversion pour la formation au classement par l’IA et d’un catalogue d’offres bien renseigné.

#### Branchement statique par rapport à la prise de décision pour la sélection de canal

La sélection de canal peut être implémentée par le biais de nœuds de condition de parcours simples (évaluation directe des attributs de profil) ou par le biais du framework de prise de décision (où les canaux sont modélisés en tant qu’éléments de décision avec l’éligibilité et le classement).

- **Les nœuds de condition statique favorisent :** simplicité, transparence et dépannage facile. Idéal lorsque la logique de sélection de canal est simple (par exemple, « si le jeton push existe et que la dernière notification push a été ouverte dans les 30 jours, utilisez une notification push, sinon un e-mail »).
- **La sélection de canal basée sur la prise de décision favorise :** la gestion centralisée, le potentiel d’optimisation de l’IA, la capacité à faire évoluer la logique de classement sans modifier la zone de travail du parcours. Idéal lorsque la sélection de canal est complexe et doit s’améliorer au fil du temps.
- **Recommandation :** utilisez des nœuds de condition statiques pour l’option B lorsque les critères de sélection de canal sont simples et bien définis. Utilisez la sélection de canal basée sur la prise de décision lorsque vous souhaitez que l’IA optimise la sélection de canal au fil du temps ou lorsque la logique de sélection de canal est suffisamment complexe pour bénéficier d’une gestion centralisée de l’éligibilité et du classement.

#### Granularité des offres et facilité de gestion des catalogues

Un catalogue d’offres volumineux et granulaire avec de nombreuses offres ciblées produit une personnalisation plus précise, mais nécessite davantage d’efforts de gestion. Un catalogue plus petit avec une éligibilité plus large est plus facile à gérer, mais moins personnalisé.

- **Favoris des catalogues volumineux (de nombreuses offres spécifiques) :** précision de personnalisation supérieure, sélections plus pertinentes pour des audiences diverses, taux de secours inférieurs
- **Petits catalogues (moins d’offres larges) en faveur de :** gestion plus facile, configuration plus rapide, tests plus simples, risque plus faible d’offres orphelines
- **Recommandation :** commencez avec 5 à 15 offres personnalisées, plus une solution de secours par décision. Ajoutez d’autres offres car vous constatez quels segments reçoivent les offres de secours les plus fréquemment. Utilisez les qualificateurs de collection pour organiser les offres par catégorie, niveau ou ligne de produit afin de permettre une croissance gérable.

#### Prise de décision basée sur les priorités par rapport à l’IA

Le classement par priorité est déterministe et transparent. La prise de décision classée par l’IA s’optimise automatiquement, mais nécessite des données d’identification et est moins transparente.

- **Le classement par priorité favorise :** prévisibilité, transparence, déploiement immédiat, aucune exigence de données de formation.
- **La prise de décision classée par l’IA favorise :** l’optimisation continue, la sélection pilotée par les données, la capacité à découvrir des affinités non évidentes entre les profils d’offre
- **Recommandation :** utilisez le classement par priorité ou par formule pour le déploiement initial. Passez à la prise de décision avec classement par l’IA une fois que vous avez accumulé au moins 1 000 événements de conversion et que vous souhaitez passer d’une optimisation basée sur des règles à une optimisation basée sur des modèles.

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

### Orchestration des parcours

- [Prise en main des parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Créer un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Propriétés du parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Activité Lecture d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Événements généraux](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Événements de qualification d’audience](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Activité de condition](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Activité Attente](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ajouter un message dans un parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Critères de sortie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [gestion des entrées de parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Tester votre parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publication du parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Création de qualificateurs de collection](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Créer des groupes d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Plans de préchauffage d’adresses IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurer le canal SMS](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Création et personnalisation de messages

- [Créer un e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/channels/email/create-email)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Gestion des conflits, des priorités et des fréquences

- [Gestion des conflits et des priorités - Aperçu](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Scores de priorité](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identification des conflits potentiels](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [plafonnement et arbitrage des parcours](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Composition de l’audience](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/pql/overview)

### Rapports et analyses

- [Rapport dynamique sur les parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)

### Profil et identité

- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation de Customer AI](https://experienceleague.adobe.com/fr/docs/experience-platform/intelligent-services/customer-ai/overview)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Gérer la liste de suppression](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/guardrails)
