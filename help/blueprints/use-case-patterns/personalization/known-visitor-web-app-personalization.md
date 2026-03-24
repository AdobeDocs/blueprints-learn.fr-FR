---
title: Personalization Web/App Connu Des Visiteurs
description: Découvrez comment diffuser du contenu, des offres ou des promotions personnalisés à des visiteurs identifiés en fonction de l’appartenance à un profil et à un segment en temps réel.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7968'
ht-degree: 2%

---

# Personnalisation web/d’application de visiteurs connus

Ce plan de référence fournit un guide de mise en œuvre complet pour diffuser du contenu personnalisé aux visiteurs identifiés sur des surfaces numériques à l’aide de [!DNL Adobe Journey Optimizer] (AJO) et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Il est destiné aux architectes de solution, aux techniciens marketing et aux ingénieurs d’implémentation qui doivent connaître toutes les approches d’implémentation viables, les décisions à prendre à chaque phase et la documentation d’Experience League prenant en charge la configuration.

La personnalisation web/de l’application d’un visiteur connu est le modèle de personnalisation principal pour les expériences digitales authentifiées. Contrairement à la personnalisation du visiteur anonyme, qui repose uniquement sur des signaux comportementaux en session, ce modèle exploite le profil unifié complet : données comportementales historiques, appartenance à un segment, niveau de fidélité, historique d’achats, étape du cycle de vie, attributs calculés et scores de propension. Il prend en charge la personnalisation sur plusieurs pages web (via le canal web d’AJO), les messages in-app mobiles et les cartes de contenu.

Ce guide présente toutes les options d’implémentation viables (basées sur les segments, basées sur la prise de décision et multi-surfaces) avec des compromis, des conseils de décision et des références à la documentation [!DNL Adobe Experience League].

## Présentation du cas d’utilisation

Les entreprises disposant de propriétés numériques authentifiées (sites d’e-commerce, portails bancaires, services d’abonnement, programmes de fidélité, applications mobiles) doivent offrir des expériences personnalisées qui reflètent la relation de chaque client avec la marque. Lorsqu’un visiteur se connecte ou est reconnu par la résolution d’identité, la plateforme peut accéder à son profil unifié complet et diffuser du contenu adapté à ses attributs, comportements et préférences spécifiques.

Ce modèle résout le scénario où un visiteur identifié arrive sur une propriété web ou ouvre une application mobile et où le système doit déterminer le contenu, l’offre ou la promotion optimal à afficher en fonction des données de profil en temps réel et de l’appartenance à l’audience. La décision de personnalisation se produit à la périphérie de l’application, en millisecondes, ce qui permet la diffusion de contenu pendant une sous-seconde sans latence perceptible.

Le modèle prend en charge la personnalisation déterministe (où un contenu spécifique correspond à des segments d’audience spécifiques) et la prise de décision dynamique (où AJO Decisioning évalue les règles d’éligibilité et les stratégies de classement pour sélectionner le contenu optimal par profil). Il s’étend sur plusieurs surfaces numériques (pages web, messages in-app mobiles et cartes de contenu), ce qui permet une personnalisation cohérente sur le parcours numérique du client.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Offrir des expériences personnalisées aux clients

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus. Pour plus d’informations, voir [Offrir des expériences client personnalisées](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

### Augmenter l’engagement du site web

Améliorez le temps passé sur le site, les pages par session et l’interaction avec le contenu web grâce à des expériences pertinentes. Pour plus d’informations, voir [Augmenter l’engagement du site web](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPI :** de la page (web), engagement, taux de conversion

### Augmenter l’engagement des applications mobiles

Stimulez l’utilisation active quotidienne, l’adoption des fonctionnalités et les conversions in-app par le biais d’expériences in-app personnalisées.

**KPI : engagement** rétention et taux de conversion

## Exemples de cas d’utilisation tactiques

Voici quelques implémentations tactiques courantes de ce modèle :

- Personnalisation du héros de la page d’accueil par niveau de fidélité ou étape du cycle de vie : affichez différentes bannières principales selon que le client est nouveau, actif, à risque ou VIP
- Carrousel de recommandations de produits basé sur l’historique des achats — suggestions de produits pertinentes à la surface utilisant les données d’achat passées et les scores d’affinité du produit
- Bannière promotionnelle personnalisée par segment de clients — afficher différentes promotions sur des segments à forte valeur, à risque et nouveaux clients
- Message in-app pour les utilisateurs et utilisatrices mobiles basé sur l’adoption des fonctionnalités : guide les utilisateurs et utilisatrices vers des fonctionnalités sous-utilisées en fonction de leurs schémas d’utilisation
- Carte de contenu avec offre personnalisée sur le tableau de bord du compte — offres persistantes, non admissibles adaptées au profil du client
- Affichage personnalisé des prix ou des remises en fonction du niveau client : affichez des prix spécifiques au niveau ou des remises exclusives aux membres du programme de fidélité.
- Widget de recommandation de vente croisée basé sur les produits détenus — suggérez des produits ou services complémentaires basés sur le portefeuille actuel
- Navigation ou ordre de contenu personnalisé en fonction des intérêts : réorganisez les modules de contenu ou les éléments de navigation en fonction des préférences démontrées.

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Approche de mesure | Conseils pour l’évaluation des performances |
| --- | --- | --- |
| Taux d’engagement Personalization | Clics et interactions avec des éléments de contenu personnalisés divisés par des impressions | Le contenu personnalisé doit surpasser le contenu par défaut de 20 à 50 % |
| Augmentation du taux de conversion | Taux de conversion des expériences personnalisées par rapport aux expériences de contrôle/par défaut | Cible 10 à 30 % d’effet élévateur sur les expériences non personnalisées |
| Taux de clic publicitaire (CTR) | Clics sur des appels à l’action, des offres et des recommandations personnalisés divisés par des impressions | Surveiller par surface (web, in-app, carte de contenu) et par segment |
| Chiffre d’affaires par visite | Chiffre d’affaires attribué aux sessions avec expériences personnalisées | Comparaison des cohortes de visiteurs personnalisées et non personnalisées |
| Taux d’interaction des cartes de contenu | Clics et rejets de cartes de contenu relatifs aux impressions | Suivi par type de carte et segment d’audience |
| Engagement Des Messages In-App | Interactions de messages in-app (clics CTA, rejets) relatives aux impressions | Comparer les segments d’audience et les types de messages |
| Temps passé sur la page | Temps moyen passé sur des pages avec du contenu personnalisé par rapport au temps par défaut | Les pages personnalisées doivent afficher un temps d’affichage plus long. |
| Taux d’acceptation de l’offre | Pourcentage d’offres sélectionnées pour la prise de décision qui génèrent un événement de conversion | Suivi par offre, par emplacement et par stratégie de classement |

## Modèle de cas d’utilisation

Cette section décrit le modèle de base et sa chaîne de fonctions.

**Personnalisation web/d’application de visiteurs connus**

Diffusez du contenu, des offres ou des promotions personnalisés à un visiteur identifié en fonction du profil en temps réel et de l’appartenance à un segment sur des surfaces web, mobiles in-app et de cartes de contenu.

**Chaîne de fonctions :** évaluation d’audience > prise de décision Personalization > Configuration de la surface/du canal > Diffusion de contenu > Suivi des impressions > Rapports

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** : configuration du canal web, configuration du canal in-app, configuration du canal de carte de contenu, prise de décision (sélection d’offres et classement), création de messages (création de contenu personnalisé), exécution de campagnes, expérimentation de contenu et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Évaluation d’audience (Edge, streaming et lot), recherche de profil en temps réel via Edge Network, enrichissement du profil avec des attributs calculés et des scores de propension
- **[!DNL Adobe Experience Platform] (AEP)** — Banque de profils, service d’identités, Web SDK, Mobile SDK, configuration des flux de données, diffusion sur le réseau Edge

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction Fondamentale | Etat | Éléments devant être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Sandbox AJO avec canal web, canal in-app et autorisations de prise de décision configurés. Utilisateurs dotés de rôles de marketeur et de créateur de contenu. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Le schéma de profil doit inclure les attributs utilisés pour la personnalisation et la segmentation (par exemple, niveau de fidélité, historique d’achats, centres d’intérêt des produits, étape du cycle de vie). Schéma d’événement d’expérience pour le suivi des interactions web/app et les événements de conversion. Jeux de données activés pour [!DNL Real-Time Customer Profile]. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Obligatoire | SDK web implémentée sur les propriétés web pour la diffusion d’expérience et le suivi des impressions. SDK mobile implémenté sur les applications mobiles pour la diffusion in-app et par carte de contenu. Flux de données configuré avec le service AJO activé pour la personnalisation Edge. Données de profil en temps réel disponibles à la périphérie pour une personnalisation inférieure à la seconde. | [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configuration des identités et des profils | Obligatoire | Espaces de noms d’identité connus (identifiant CRM, e-mail, identifiant utilisateur authentifié) configurés. La combinaison d’identités entre les sessions anonymes et authentifiées est opérationnelle pour une transition transparente de la personnalisation anonyme vers la personnalisation de visiteur connu. Politique de fusion d’Edge configurée avec `isActiveOnEdge: true` pour résoudre le profil authentifié sur edge. | [présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | Audiences définies à l’aide d’attributs de profil, de données comportementales et d’attributs calculés. Évaluation d’Edge ou de streaming activée pour la qualification de la personnalisation en temps réel. Les audiences utilisées pour la personnalisation basée sur les segments doivent être qualifiées pour l’évaluation Edge. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Importance de la résolution | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés (par exemple, les scores de propension [!DNL Customer AI], la valeur de durée de vie, le score d’engagement, l’affinité du produit, le nombre de jours depuis le dernier achat) améliorent considérablement la qualité de la personnalisation en fournissant des signaux plus riches pour la définition de l’audience et la sélection du contenu. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Présentation de l’IA dédiée aux clients](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Gestion du cycle de vie des données | Recommandé | Les politiques de conservation des données de profil et d’événement garantissent que des données récentes et pertinentes alimentent les décisions de personnalisation. L’application du consentement garantit que la personnalisation respecte les préférences de l’utilisateur. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les étiquettes de gouvernance sur les attributs de profil utilisés pour la personnalisation (en particulier les attributs adjacents aux informations d’identification personnelle tels que l’historique des achats, l’emplacement et les données financières) garantissent la conformité aux politiques d’utilisation des données. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Recommandé | La surveillance des performances de diffusion et de personnalisation d’Edge permet de détecter les problèmes de latence, les échecs de diffusion ou les problèmes de fraîcheur des données qui dégradent l’expérience personnalisée. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Rapports et analyses | Inclus | Le rapport de performances de Personalization fait partie de l’étape 6 de la chaîne de fonctions. [!DNL Customer Journey Analytics] l’analyse permet d’étudier en détail l’impact de la personnalisation sur la conversion, l’engagement et le chiffre d’affaires des segments de visiteurs. | [Présentation de &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de canal | Configuration de la surface et des canaux | Configurer des surfaces de canal web, in-app et de carte de contenu pour la diffusion de la personnalisation |
| Création de messages | Création de contenu | Créez des variantes de contenu personnalisées avec du contenu dynamique, des expressions de personnalisation et des blocs conditionnels pour chaque surface |
| Exécution de la campagne | Configuration et activation de Campaign | Créer et activer des campagnes web (planifiées ou déclenchées par API) qui lient les audiences, les surfaces et le contenu |
| Prise de décision. | Configuration De La Prise De Décision (Option B/C) | Configurez des politiques de décision avec des règles d’éligibilité, des stratégies de classement et des éléments d’offre/de contenu pour la personnalisation dynamique |
| Expérimentation de contenu | Optimisation (facultatif) | Exécutez des tests A/B sur des variantes de contenu personnalisées pour optimiser les performances. |
| Fréquence et règles métier | Configuration et activation de Campaign | Application de limites de fréquence d’impression pour éviter la fatigue de surpersonnalisation |
| Rapports et analyse des performances | Rapports et optimisation | Surveillez les mesures de diffusion, d’engagement et de conversion de la personnalisation par surface et segment |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Définition et évaluation de l’audience | Définissez et évaluez des audiences à l’aide des attributs de profil, des données comportementales et des attributs calculés avec une évaluation Edge ou en flux continu |
| Recherche de profil en temps réel | Diffusion de contenu (runtime) | Accédez aux attributs de profil en temps réel et aux appartenances aux segments via Edge Network pour les décisions de personnalisation de la seconde |
| Enrichissement de profil | Pré-implémentation (prise en charge) | Enrichissez les profils avec des attributs calculés, des scores de [!DNL Customer AI] et des signaux comportementaux agrégés qui améliorent la qualité de la personnalisation |

## Conditions préalables

Avant d’implémenter ce modèle de cas d’utilisation, assurez-vous que les éléments suivants sont en place :

- [ ] Web SDK implémenté sur les propriétés web cibles avec des `alloy("sendEvent")` configurées pour le suivi des pages vues et des interactions
- [ ] Mobile SDK implémenté sur les applications mobiles cibles (si les surfaces in-app ou de carte de contenu sont utilisées)
- [ Flux de données ] configuré avec le service [!DNL Adobe Journey Optimizer] activé
- [ ] schéma de profil inclut les attributs utilisés pour la personnalisation (niveau de fidélité, historique d’achats, centres d’intérêt des produits, étape du cycle de vie)
- [ Schéma d’événement d’expérience ] configuré pour le suivi des impressions et des conversions
- [ ] Espaces de noms d’identité connus créés et l’assemblage d’identités opérationnel entre les identités anonymes (ECID) et authentifiées
- [ ] la politique de fusion d’Edge configurée avec `isActiveOnEdge: true`
- [ ] Audiences définies avec une évaluation éligible Edge pour la personnalisation en temps réel
- [ ] des ressources de contenu (images, copie, CTA) préparées pour chaque variante de personnalisation
- [ ] stratégie Personalization documentée : quels attributs génèrent quel contenu, pour quelles surfaces

## Options de mise en œuvre

Cette section décrit les approches d’implémentation disponibles pour ce modèle de cas d’utilisation.

### Option A : personnalisation web basée sur les segments

**Idéal pour** personnalisation déterministe où des variantes de contenu spécifiques sont mappées directement à des segments d’audience : bannières principales spécifiques au niveau de fidélité, messages d’étape de cycle de vie, contenu promotionnel de segment client. Idéal lorsque le mappage contenu-segment est bien défini et ne nécessite pas de classement ou d’optimisation dynamique.

**Fonctionnement :**

La personnalisation basée sur les segments mappe les variantes de contenu directement aux segments d’audience. Lorsque le profil d’un visiteur connu est évalué par rapport aux audiences éligibles à Edge au chargement de la page, le système détermine à quels segments le visiteur appartient et affiche la variante de contenu correspondante. La sélection est basée sur la priorité d’appartenance au segment : si un visiteur remplit les conditions pour plusieurs segments, le contenu du segment avec la priorité la plus élevée s’affiche.

Cette approche utilise les campagnes de canal web AJO (ou les campagnes in-app/de carte de contenu) avec des règles de contenu conditionnel ou plusieurs configurations de ciblage de traitement. Chaque segment d’audience est associé à une expérience de contenu spécifique. Aucun moteur de prise de décision n’est impliqué ; la logique de sélection du contenu est entièrement pilotée par les segments.

Le contenu est créé à l’aide de l’interface de création de messages AJO avec des blocs de contenu dynamiques qui effectuent le rendu de différents contenus en fonction de l’appartenance à l’audience ou des attributs de profil. Le SDK web ou le SDK mobile offre une expérience personnalisée en temps réel via Edge Network.

**Considérations principales :**

- Les variantes de contenu doivent être précréées pour chaque segment.
- Les définitions de segment doivent être éligibles pour la qualification en temps réel
- L’ajout de nouveaux segments ou variantes de contenu nécessite la mise à jour de la configuration de la campagne
- La sélection du contenu est déterministe : le même segment voit toujours le même contenu

**Avantages :**

- Mise en œuvre et maintenance simples grâce à un mappage contenu-segment clair
- Facile à comprendre et à expliquer la logique de personnalisation aux parties prenantes
- Pas de surcharge de prise de décision : résolution plus rapide du contenu
- Contrôle complet du contenu que chaque segment reçoit

**Limitations :**

- Flexibilité limitée lorsque le nombre de segments et de variantes de contenu augmente
- Impossible d’optimiser dynamiquement la sélection de contenu en fonction des signaux au niveau du profil au-delà de l’appartenance au segment
- L’ajout de nouvelles variantes de contenu nécessite des mises à jour manuelles de la campagne
- Ne prend pas en charge les scénarios de meilleure offre suivante où plusieurs offres se disputent le même emplacement

**Experience League:**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Option B : personnalisation basée sur la prise de décision

**Idéal pour :** personnalisation dynamique où le contenu ou l’offre optimal doit être sélectionné par profil à l’aide de règles d’éligibilité et de stratégies de classement : meilleure offre sur la page d’accueil, recommandations de produits personnalisées, sélection de bannières promotionnelles dynamiques. Idéal lorsque plusieurs offres ou éléments de contenu se disputent le même emplacement et que le système doit choisir le meilleur.

**Fonctionnement :**

La personnalisation basée sur la prise de décision utilise AJO Decisioning pour évaluer le profil de chaque visiteur par rapport à un catalogue d’éléments de contenu ou d’offres, en appliquant des règles d’éligibilité pour déterminer les éléments qui remplissent les critères, puis en appliquant une stratégie de classement (basée sur une priorité, basée sur une formule ou classée par l’IA) pour sélectionner l’élément optimal pour chaque emplacement.

La mise en œuvre implique la création d’emplacements (où le contenu apparaît), la définition d’offres avec des règles d’éligibilité et des représentations de contenu, l’organisation des offres en collections et la création de politiques de décision qui lient les emplacements aux collections avec des stratégies de classement. Au moment de l’exécution, lorsqu’un visiteur charge une page, l’Edge Network évalue la politique de décision par rapport au profil du visiteur et renvoie le contenu de l’offre sélectionnée.

Cette approche prend en charge des scénarios de personnalisation sophistiqués, notamment la meilleure offre suivante, les promotions personnalisées avec limitation et la sélection de contenu optimisée par l’IA. Les offres peuvent avoir des limites de limitation globales et par profil, des périodes de validité et des critères d’éligibilité complexes combinant les attributs de profil et l’appartenance à l’audience.

**Considérations principales :**

- Nécessite une configuration plus en amont (emplacements, offres, règles d’éligibilité, collections, décisions)
- Les stratégies de classement peuvent être basées sur la priorité (manuelle), sur la formule (expression personnalisée) ou sur l’IA (optimisation automatique)
- Le classement par l’IA nécessite au moins 1 000 événements de conversion pour la formation des modèles
- Les compteurs de limitation d’offre peuvent présenter un léger décalage dans les scénarios à débit élevé
- Une offre de secours doit être configurée dans les cas où aucune offre personnalisée ne se qualifie

**Avantages :**

- Sélection dynamique de contenu par profil sans mappage segment-contenu codé en dur
- Prend en charge des critères d’éligibilité et une logique de classement complexes
- Option de classement par l’IA permettant une optimisation automatique sans intervention manuelle
- La limitation de l’offre empêche la surexposition de contenu spécifique
- Gestion centralisée des offres : les offres peuvent être réutilisées dans plusieurs campagnes et canaux.

**Limitations :**

- Une implémentation plus complexe que la personnalisation basée sur les segments
- Le classement par l’IA nécessite un volume d’événement de conversion suffisant pour la formation
- L’évaluation de la prise de décision ajoute une latence marginale par rapport à la diffusion directe de contenu basé sur segment
- Le classement basé sur une formule nécessite une conception soigneuse pour éviter toute hiérarchisation involontaire

**Experience League:**

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

**En quoi cela diffère-t-il de l’option B:** d’Offer Decisioning ?

L’infrastructure est identique : les deux utilisent AJO Decisioning à la périphérie avec Web SDK et une politique de fusion Edge-active. La différence réside dans ce qui est sélectionné. Cette option gère les éléments de contenu pour lesquels le critère de sélection est la personnalisation (appartenance à un segment, classement comportemental). [Offer Decisioning &#x200B;](offer-decisioning.md) l’option B gère un catalogue d’offres régi où les règles d’éligibilité, les limites de limitation et les fenêtres de validité sont des exigences commerciales. Si votre jeu d’éléments nécessite une limitation des impressions par profil, des contraintes d’éligibilité réglementaires ou une gestion du cycle de vie des offres, utilisez plutôt l’option B d’Offer Decisioning.

### Option C : personnalisation multi-surface (web + in-app + carte de contenu)

**Idéal pour** : personnalisation cohérente sur plusieurs surfaces numériques, offrant des expériences personnalisées coordonnées sur des pages web, des messages in-app mobiles et des cartes de contenu. Idéal lorsque l’entreprise dispose de propriétés d’application web et mobile et souhaite une logique de personnalisation unifiée pour tous les points de contact numériques.

**Fonctionnement :**

La personnalisation multi-surface étend l’option A (basée sur un segment) ou l’option B (basée sur la prise de décision) pour diffuser du contenu personnalisé sur plusieurs types de surface AJO. Chaque type de surface (web, in-app, carte de contenu) peut avoir différents formats de contenu et mécanismes de diffusion, mais la logique de personnalisation sous-jacente (appartenance à l’audience ou prise de décision) est partagée.

L’implémentation implique la configuration des surfaces de canal pour chaque type de surface, la création de contenu spécifique à la surface (Web HTML/CSS pour les surfaces web, messages structurés pour in-app, dispositions de carte pour les cartes de contenu) et la création de campagnes qui ciblent la surface appropriée. Le SDK Web gère la diffusion par surface web, tandis que le SDK Mobile gère la diffusion in-app et par carte de contenu.

Les cartes de contenu sont particulièrement utiles pour les messages personnalisés persistants et non admissibles sur les tableaux de bord du compte ou les écrans d’accueil de l’application. Les messages in-app sont parfaits pour les communications contextuelles et spécifiques à une session. La personnalisation web gère les bannières principales, les widgets de recommandation et le contenu promotionnel.

**Considérations principales :**

- Chaque type de surface nécessite sa propre configuration de surface de canal et sa propre création de contenu
- Web SDK et Mobile SDK doivent être implémentés et configurés
- Le contenu doit être conçu pour chaque format de surface (différentes dimensions, mises en page, modèles d’interaction)
- Les audiences partagées et la logique de prise de décision garantissent la cohérence entre les surfaces
- Les tests doivent couvrir tous les types de surface sur tous les appareils

**Avantages :**

- Expérience de personnalisation cohérente pour tous les points de contact numériques
- L’audience partagée et la logique de prise de décision réduisent la duplication
- Les cartes de contenu fournissent une surface de personnalisation persistante et non intrusive
- Les messages in-app permettent une personnalisation contextuelle spécifique à une session sur mobile

**Limitations :**

- Complexité d’implémentation maximale : configuration requise pour chaque type de surface
- Nécessite une implémentation de Web SDK et de Mobile SDK
- Le contenu doit être conçu et conservé pour chaque format de surface
- La portée du test augmente avec chaque type de surface supplémentaire

**Experience League:**

- [Présentation du canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Canal de la carte de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### Comparaison des options

Le tableau suivant compare les trois options d’implémentation.

| Critères | Option A : Basée Sur Les Segments | Option B : Fondée Sur Les Décisions | Option C : Surface Multiple |
| --- | --- | --- | --- |
| Idéal pour | Mappage segment-contenu connu | Sélection dynamique de contenu par profil | Personnalisation cohérente sur le web et les appareils mobiles |
| Complexité | Faible | Medium-Grand | Élevée (repose sur A ou B) |
| Latence | La plus rapide (résolution de segment directe) | Légèrement plus élevé (évaluation de la prise de décision) | Dépend de l&#39;option sous-jacente (A ou B) |
| Flexibilité | Limité aux paires segment-contenu prédéfinies | Élevé : classement et éligibilité dynamiques | La plus élevée : multi-surface avec logique partagée |
| Gestion de contenu | Mappage manuel segment-contenu | Bibliothèque des offres centralisée avec des règles d&#39;éligibilité | Contenu par surface avec logique de personnalisation partagée |
| Optimisation | Test A/B manuel | Optimisation automatique avec classement par l’IA disponible | Optimisation par surface |
| Requiert | Audiences éligibles à Edge, Web SDK | Stages, offres, règles d’éligibilité, décisions | SDK web + SDK mobile, configurations de plusieurs surfaces |
| Surfaces prises en charge | Web (principal) | Web (principal) | Web + In-App + Carte de contenu |

### Choisir la bonne option

Commencez par répondre aux questions suivantes pour sélectionner l’approche d’implémentation appropriée :

1. **Combien de surfaces ?** Si vous avez besoin de personnalisation sur les applications web et mobiles, choisissez l’option C (qui s’appuie sur A ou B pour la logique sous-jacente). En mode web uniquement, choisissez entre A et B.

2. **À quel point votre sélection de contenu est-elle dynamique ?** Si vous disposez d’un mappage bien défini des segments aux variantes de contenu (par exemple, 3 à 5 niveaux de fidélité, chacun avec une bannière principale spécifique), choisissez l’option A. Si vous devez effectuer une sélection dans un catalogue d’offres avec une éligibilité et un classement complexes, choisissez l’option B.

3. **Avez-vous besoin d’une sélection optimisée par l’IA ?** Si vous souhaitez que le système apprenne et optimise automatiquement le contenu le plus performant pour chaque profil, choisissez l’option B avec la prise de décision classée par l’IA.

4. **Combien de variantes de contenu ?** Si vous avez moins de 10 variantes de contenu avec des mappages de segments clairs, l’option A est plus simple. Si vous avez des dizaines d’offres qui nécessitent un filtrage d’éligibilité et un classement, l’option B se met mieux à l’échelle.

5. **Prévoyez-vous d’étendre à d’autres canaux ?** Si votre logique de prise de décision doit finalement diffuser des offres sur les canaux e-mail, web et autres, l’option B fournit la base de prise de décision centralisée que la prise de décision d’offres cross-canal étend.

## Phases de mise en œuvre

Cette section décrit en détail chaque phase de l’implémentation.

### Phase 1 : définition des audiences et configuration de l’évaluation

**Fonction d’application :** RT-CDP : évaluation de l’audience

**Ce que vous allez configurer :** définissez les audiences qui pilotent la sélection du contenu de personnalisation. Ces audiences représentent les segments de visiteurs qui recevront des expériences personnalisées : niveaux de fidélité, étapes du cycle de vie, cohortes comportementales ou groupes d’affinités de produit.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : méthode d’évaluation de l’audience**
>
>Dans quel délai l’appartenance à une audience doit-elle être résolue pour la personnalisation ? Cela a un impact direct sur si la personnalisation peut se produire au chargement de la page ou nécessite un délai.
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Évaluation Edge | Personnalisation web/d’application en temps réel nécessitant une qualification inférieure à la seconde | Limité à de simples vérifications d’attributs de profil et à l’appartenance à un segment. Aucune requête de série temporelle ni agrégation complexe. Requis pour la personnalisation des visiteurs connus. |
>| Évaluation en flux continu | Qualification en temps quasi réel lorsque les profils entrent/sortent des audiences en fonction d’événements comportementaux | Prend en charge les requêtes à événement unique et à fenêtre temporelle limitée. Les modifications d’audience se reflètent en quelques minutes. Convient aux surfaces in-app et de carte de contenu où un léger retard est acceptable. |
>| Évaluation par lots | L’audience quotidienne est actualisée pour les segments en fonction d’agrégations complexes ou de modèles historiques | Prise en charge complète des fonctions de règles de segment. Ne convient pas à la personnalisation en temps réel, mais peut compléter les audiences Edge par des segments précalculés complexes. |

>[!NOTE]
>**Décision : attributs Personalization**
>
>Quels attributs de profil doivent guider la définition de l’audience et la sélection de contenu ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Attributs de profil (niveau de fidélité, étape du cycle de vie) | Personnalisation déterministe basée sur des propriétés client connues | Attributs stables et bien définis. Facile à mapper à des variantes de contenu. Disponible sur le serveur Edge si le profil est correctement configuré. |
>| Signaux comportementaux (historique d’achat, schémas de navigation) | Personalization basé sur les comportements récents et les schémas d’engagement | Nécessite des attributs calculés pour les segments en flux continu. Plus dynamique mais plus complexe à gérer. |
>| Scores de propension ([!DNL Customer AI]) | Personnalisation prédictive basée sur la probabilité de conversion, d’attrition ou d’achat | Nécessite des attributs calculés. Permet une personnalisation sophistiquée, mais nécessite des données d’identification de modèle ML. |
>| Approche combinée | La plupart des implémentations de production | Utilise les attributs de profil pour la segmentation principale avec des signaux comportementaux et des scores de propension pour l’affinement. |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle

**Détails de configuration clés :**

- Définir des audiences à l’aide du créateur de segments avec des expressions de règle de segment référençant des attributs de profil
- Assurez-vous que les expressions de règle de segment remplissent les critères de l’évaluation Edge (vérifications d’attribut simples, appartenance au segment)
- Configurer des audiences éligibles à Edge pour les cas d’utilisation de la personnalisation en temps réel
- Envisagez des audiences de suppression pour exclure les visiteurs récemment convertis ou désinscrits

**Documentation Experience League :**

- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2 : configuration de la prise de décision (options B et C uniquement)

**Fonction d’application :** AJO : prise de décision

**Ce que vous allez configurer :** configurez l’infrastructure de prise de décision qui sélectionne de manière dynamique le contenu ou l’offre optimal pour chaque visiteur. Cela inclut les emplacements (où les offres apparaissent), les offres (le contenu disponible), les règles d’éligibilité (qui se qualifie), les stratégies de classement (comment choisir le meilleur) et les politiques de décision (comment tout se connecte).

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : Stratégie de classement**
>
>Comment les offres éligibles doivent-elles être classées pour sélectionner la meilleure pour chaque visiteur ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Basé sur la priorité (manuel) | Cas d’utilisation simples avec une hiérarchie des offres claire | Chaque offre a une valeur de priorité manuelle. L’offre éligible avec la priorité la plus élevée gagne. Facile à comprendre et à contrôler. |
>| Basé sur une formule (expression personnalisée) | Quand le classement doit prendre en compte les attributs de profil | Les formules de classement personnalisées font référence aux données de profil (par exemple, score par niveau de fidélité + récence). Flexible, mais nécessite la conception et les tests de la formule. |
>| Classement par l’IA (optimisation automatique) | Lorsque vous souhaitez que le système optimise automatiquement la sélection des offres | Le modèle ML identifie les offres les plus performantes pour les profils. Nécessite au moins 1 000 événements de conversion pour la formation. Idéal pour les emplacements à trafic élevé. |

>[!NOTE]
>**Décision : limitation de l’offre**
>
>Doit-on limiter le nombre de fois où une offre est présentée à un visiteur ou à tous les visiteurs et visiteuses ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Limite par profil | Éviter que la lassitude ne voit la même offre à plusieurs reprises | Limite les impressions par visiteur sur une période donnée. Garantit la variété de l’expérience personnalisée. |
>| Limite globale | Limiter le nombre total d’impressions pour une promotion ou une offre à disponibilité limitée | Limite le nombre total d’impressions de tous les visiteurs. Utile pour les promotions à quantité limitée. |
>| Pas de limitation | Contenu en constante évolution ou offres toujours pertinentes | Aucune limite d’impression. Convient aux contenus persistants tels que les bannières de niveau de fidélité. |

**Navigation dans l’interface utilisateur** [!DNL Journey Optimizer] > Composants > Gestion des décisions

**Détails de configuration clés :**

- Créez des emplacements pour chaque surface où les offres apparaîtront (bannière web, zone de message in-app, emplacement de carte de contenu).
- Définir des règles d’éligibilité à l’aide d’expressions de règle de segment faisant référence aux attributs de profil et à l’appartenance aux audiences
- Créer des offres personnalisées avec des représentations de contenu pour chaque emplacement
- Créez une offre de secours qui couvre tous les emplacements (affichée lorsqu&#39;aucune offre personnalisée ne se qualifie)
- Organisez les offres avec des qualificateurs de collection (balises) et regroupez-les dans des collections
- Créez une politique de décision liant les emplacements aux collections avec la stratégie de classement sélectionnée

**Documentation Experience League :**

- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 3 : configuration des surfaces et des canaux

**Fonction d’application :** AJO : Configuration de canal

**Ce que vous allez configurer :** configurez les surfaces de canal qui définissent l’endroit où le contenu personnalisé sera diffusé. Chaque type de surface (web, in-app, carte de contenu) nécessite sa propre configuration spécifiant l’URI de surface, le format de contenu et les paramètres de diffusion.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : surfaces cibles**
>
>Quelles surfaces numériques recevront du contenu personnalisé ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Canal web uniquement | Personalization axé sur les propriétés web | Nécessite le SDK Web. Implémentation la plus simple. Couvre les bannières principales, les zones promotionnelles et les widgets de recommandation. |
>| Canal in-app uniquement | Personalization axé sur les expériences des applications mobiles | Nécessite Mobile SDK. Couvre les messages contextuels spécifiques à une session dans l’application. |
>| Canal de carte de contenu uniquement | Messages personnalisés persistants et non admissibles | Nécessite Mobile SDK ou Web SDK. Les cartes persistent jusqu’à leur rejet. Idéal pour les tableaux de bord et les écrans d’accueil. |
>| Surfaces multiples (option C) | Personnalisation cohérente sur le web et les appareils mobiles | Nécessite à la fois Web SDK et Mobile SDK. Chaque surface nécessite une configuration et un contenu distincts. |

>[!NOTE]
>**Décision : approche de la configuration de la surface web**
>
>Comment la surface web doit-elle être configurée pour la diffusion de contenu ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Application monopage (SPA) | Applications web modernes avec routage côté client | Utilisez `renderDecisions: true` dans les appels de `sendEvent` Web SDK. Contenu rendu automatiquement par le SDK. |
>| Application multi-page (MPA) | Pages web traditionnelles générées par le serveur | Contenu diffusé au chargement de la page via une réponse Edge Network. Peut nécessiter une configuration URI de surface au niveau de la page. |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Administration > Canaux > Surfaces de canal

**Détails de configuration clés :**

- Pour les surfaces web : configurez l’URI de surface web correspondant à la ou aux pages cibles
- Pour les surfaces in-app : configurez la surface de l’application mobile avec l’ID d’application et le type de surface
- Pour les surfaces de carte de contenu : configurez la surface de carte de contenu avec l’ID d’application ou le contexte web
- Assurez-vous que le service AJO est activé pour la diffusion de la personnalisation Edge du flux de données

**Documentation Experience League :**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Configuration du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [Conditions préalables relatives au canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Configuration des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Phase 4 : création de contenu

**Fonction d’application :** AJO : création de messages

**Ce que vous allez configurer :** créez les variantes de contenu personnalisées pour chaque surface et segment ou offre. Cela inclut la conception de la disposition visuelle, l’ajout d’expressions de personnalisation qui font référence à des attributs de profil, la configuration de blocs de contenu conditionnel et la création de fragments de contenu réutilisables.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : approche du contenu**
>
>Comment le contenu personnalisé doit-il être structuré pour ce cas d’utilisation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Blocs de contenu conditionnel | Les différentes sections de contenu d’une même disposition varient selon l’audience | Ressource de contenu unique avec règles conditionnelles. Efficace pour les variations mineures (titre, texte CTA, permutation d’image). |
>| Différentes variantes de contenu par traitement | Dispositions ou conceptions fondamentalement différentes par audience | Plusieurs ressources de contenu complètes. Plus flexible, mais plus facile à gérer. Requis pour l’expérimentation de contenu. |
>| Contenu piloté par les décisions | Contenu sélectionné dynamiquement dans un catalogue d&#39;offres | Les représentations d&#39;offres définissent le contenu. La gestion de contenu est centralisée dans la bibliothèque des offres. |

>[!NOTE]
>**Décision : profondeur du Personalization**
>
>Quelle partie du contenu doit être personnalisée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Personnalisation au niveau de la surface | Seuls des éléments spécifiques sont personnalisés (image principale, CTA, bannière d’offre) | Complexité moindre. Personnalisation ciblée sur les zones à fort impact. Point de départ le plus courant. |
>| Personnalisation de toute la page | La mise en page ou l’ordre du contenu entier est personnalisé | Complexité plus élevée. Nécessite une création de contenu étendue. Offre l’expérience la plus adaptée. |
>| Personnalisation au niveau des jetons | Jetons de personnalisation intégrés (nom, niveau, solde de points) | Forme la plus simple. Insère les valeurs d’attribut de profil dans un contenu statique. |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Campagnes > Créer une campagne > Modifier le contenu

**Là où les options divergent :**

**Pour l’option A (basée sur un segment) :**

- Créez des variantes de contenu pour chaque segment d’audience à l’aide du concepteur web ou de l’éditeur de code
- Utilisez des blocs de contenu dynamiques avec des conditions basées sur l’appartenance à l’audience
- Configurer des expressions de personnalisation faisant référence à des attributs de profil (par exemple, `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}`)
- Configurer des règles conditionnelles pour afficher un contenu différent en fonction de l’appartenance à un segment

**Pour l’option B (basée sur la prise de décision) :**

- Créer des représentations du contenu de l’offre pour chaque emplacement défini à la phase 2
- Chaque offre comporte une ou plusieurs représentations (HTML, image, JSON) associées à des emplacements
- Intégrer la sortie de prise de décision dans la page web ou l&#39;application en incorporant des emplacements de décision
- Le contenu est sélectionné dynamiquement au moment de l’exécution — la création se concentre sur des éléments d’offre individuels

**Pour l’option C (surface multiple) :**

- Créez du contenu spécifique à chaque surface cible (Web HTML/CSS, message structuré in-app, disposition de carte de contenu).
- Conservez une logique de personnalisation cohérente sur toutes les surfaces tout en vous adaptant aux contraintes de format de chaque surface
- Tester le rendu du contenu sur chaque type de surface

**Documentation Experience League :**

- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Créer des messages in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Créer des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Phase 5 : configuration et activation des campagnes

**Fonction d’application :** AJO : exécution de campagne

**Ce que vous allez configurer :** créez et activez la campagne AJO qui lie l’audience, la surface et le contenu pour la diffusion. Pour la personnalisation web, les campagnes sont généralement configurées pour une activation immédiate ou continue, plutôt que pour des envois planifiés uniques.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : type de campagne**
>
>Comment la campagne de personnalisation doit-elle être déclenchée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Campagne planifiée (toujours active) | Une personnalisation continue qui s’exécute en continu pour tous les visiteurs admissibles | Définissez la date de début sur immédiate et aucune date de fin. La campagne reste active jusqu’à l’arrêt manuel. Les plus courants pour la personnalisation web. |
>| Campagne planifiée (limitée dans le temps) | Personalization lié à une période de promotion spécifique | Définissez les dates de début et de fin. La campagne s’arrête automatiquement après la date de fin. Convient aux promotions saisonnières ou aux offres à durée limitée. |
>| Campagne déclenchée par l’API | Personalization déclenché par un événement d’application spécifique | Déclenché par programmation. Utile lorsque la personnalisation ne doit apparaître qu’en réponse à des événements système spécifiques. |

>[!NOTE]
>**Décision : capping de la fréquence**
>
>La fréquence d’impression doit-elle être limitée pour cette personnalisation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Application de règles de fréquence | Personnalisation promotionnelle ou basée sur les offres qui peut fatiguer les visiteurs et visiteuses | Permet d’éviter qu’une même personnalisation ne se répète trop de fois. Configuré via les règles métier d’AJO. |
>| Aucune limitation de fréquence | Personnalisation de contenu permanente (bannière de fidélité, contenu de tableau de bord) | Contenu toujours pertinent et ne provoquant pas de fatigue. Aucune limite d’impression n’est nécessaire. |

**Navigation dans l’interface utilisateur** [!DNL Journey Optimizer] > Campagnes > Créer une campagne

**Détails de configuration clés :**

- Sélectionnez le canal web, in-app ou de carte de contenu et la surface configurée lors de la phase 3
- Liaison de l’audience cible définie dans la phase 1
- Lier le contenu créé lors de la phase 4
- Configurer le planning de la campagne (immédiat, période ou déclenché par l’API)
- Vérification et activation de la campagne
- Pour l’expérimentation de contenu : activez le bouton d’expérience, définissez des traitements, définissez l’affectation du trafic et les mesures de succès avant l’activation

**Documentation Experience League :**

- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Règles de fréquence](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Phase 6 : suivi des impressions et collecte des données

**Fonction d’application :** AEP : Sources et collecte de données

**Ce que vous allez configurer :** assurez-vous que les impressions, interactions et conversions provenant d’expériences personnalisées sont suivies sur la plateforme à des fins de création de rapports, de réévaluation de l’audience et d’optimisation de la prise de décision.

**Détails de configuration clés :**

- Vérifier que Web SDK envoie des événements `decisioning.propositionDisplay` lors du rendu du contenu personnalisé
- Vérifier que Web SDK envoie des événements `decisioning.propositionInteract` lorsque les visiteurs et visiteuses interagissent avec du contenu personnalisé (clics, ignorances)
- Pour Mobile SDK : vérifiez que les événements d’interaction de message et de carte de contenu in-app sont capturés
- Configurer le suivi des événements de conversion pour les mesures de succès en aval (achats, inscriptions, adoption des fonctionnalités)
- Assurez-vous que les événements incluent l’identifiant de proposition pour l’attribution à des décisions de personnalisation spécifiques

**Documentation Experience League :**

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Suivi des événements avec Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Phase 7 : générer des rapports et optimiser

**Fonction d’application :** AJO : Rapports et analyse des performances, Rapports et analyses

**Éléments à configurer :** configurez la surveillance et l’analyse des performances pour mesurer l’efficacité de la personnalisation sur les surfaces, les segments et les variantes de contenu. Utilisez les rapports natifs d’AJO pour les mesures opérationnelles et les [!DNL Customer Journey Analytics] d’analyse de l’impact commercial cross-canal.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : Portée du reporting**
>
>Quel niveau d’analyse est nécessaire pour ce cas d’utilisation de la personnalisation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Rapports natifs AJO uniquement | Suivi opérationnel des mesures de diffusion et d’engagement | Rapports de campagne intégrés contenant des données d’impression, de clic et de conversion. Configuration la plus rapide. |
>| Analyse cross-canal CJA | Analyse approfondie de l’impact de la personnalisation sur les résultats commerciaux | Nécessite une connexion CJA et une vue de données. Permet l’analyse funnel, les comparaisons de cohortes et la modélisation d’attribution sur plusieurs canaux. |
>| AJO + CJA | Visibilité opérationnelle et analytique complète | Utilisez AJO pour la surveillance quotidienne et CJA pour l’analyse stratégique. Recommandé pour les implémentations de production. |

**Navigation dans l’interface utilisateur :**

- Rapports AJO : Campagnes > Sélectionner une campagne > Afficher le rapport
- CJA : Projets > Créer un projet

**Détails de configuration clés :**

- Accès aux rapports dynamiques de campagne pendant la diffusion de personnalisation active
- Consulter les rapports historiques pour les campagnes terminées ou les analyses périodiques
- Pour CJA : configurer une connexion comprenant des jeux de données d’événement d’expérience AJO et créer une vue de données avec des mesures de personnalisation
- Créez des tableaux de bord pour suivre le taux d’engagement de la personnalisation, l’effet élévateur de conversion, le taux d’acceptation des offres et le chiffre d’affaires par visite
- Pour la personnalisation basée sur la prise de décision (option B) : surveillez les performances des offres par l’efficacité des stratégies d’emplacement et de classement

**Documentation Experience League :**

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage pertinentes pour ce modèle de cas d’utilisation.

### Mécanismes de sécurisation et limites

- Les recherches Edge Network ont un temps de réponse SLA inférieur à 200 ms pour les segments évalués par Edge — [mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Les segments Edge sont limités à de simples vérifications d’attributs et requêtes d’appartenance à un segment (aucune requête de série temporelle). [segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Une seule politique de fusion peut être active sur Edge par sandbox — [Politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- Maximum de 10 000 offres personnalisées approuvées par sandbox — [&#x200B; Mécanismes de sécurisation de la gestion des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 30 emplacements par décision - [Mécanismes de sécurisation &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Les modèles de classement par l’IA nécessitent au moins 1 000 événements de conversion pour la formation
- Le temps de réponse de la diffusion des offres SLA est inférieur à 500 ms à l’adresse P95 pour les requêtes à portée unique
- Maximum de 500 campagnes actives en direct par sandbox — [Mécanismes de sécurisation &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 25 attributs calculés actifs par sandbox — [Mécanismes de sécurisation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### Pièges courants

- **Politique de fusion d’Edge non configurée :** sans politique de fusion Edge-active, Edge Network ne peut pas résoudre le profil authentifié, ce qui entraîne l’échec de la personnalisation ou le retour à un comportement anonyme. Assurez-vous qu’une seule politique de fusion a `isActiveOnEdge: true` dans le sandbox.
- **Audience non éligible à Edge :** si les expressions de règle de segment d’audience utilisent des requêtes de série temporelle, des agrégations complexes ou des références `inSegment()` à des segments par lots uniquement, elles ne seront pas qualifiées pour l’évaluation Edge et ne pourront pas alimenter la personnalisation en temps réel. Validez l’éligibilité Edge lors de la définition de l’audience.
- **Écart de combinaison d’identités lors de l’authentification :** lorsqu’un visiteur passe d’anonyme à authentifié, il peut y avoir un bref moment où le profil n’a pas encore été résolu. Assurez-vous que l’assemblage des identités est correctement configuré et que le SDK Web envoie l’identité authentifiée via `identityMap` immédiatement après la connexion.
- **Offre de secours manquante dans la prise de décision :** si aucune offre de secours n’est configurée et qu’aucune offre personnalisée ne se qualifie pour un visiteur, la décision renvoie un contenu vide, créant une expérience rompue. Configurez toujours une offre de secours qui couvre tous les emplacements.
- **Web SDK n’envoie pas d’événements d’affichage de proposition :** si `renderDecisions` est défini sur `true` mais que les événements d’affichage ne sont pas envoyés, les rapports ne reflètent pas les impressions réelles. Vérifiez le suivi des événements en examinant les requêtes réseau dans les outils de développement du navigateur.
- **Le contenu scintille au chargement de la page :** si le contenu personnalisé n’est pas prémasqué pendant l’appel de décision, les visiteurs peuvent voir brièvement le contenu par défaut avant qu’il ne soit remplacé. Utilisez le fragment de code de pré-masquage ou le pré-masquage basé sur CSS pour éliminer le scintillement.

### Bonnes pratiques

- Commencez par la personnalisation basée sur un segment (option A) pour l’implémentation initiale, puis passez à la personnalisation basée sur la prise de décision (option B) à mesure que le catalogue d’offres se développe et que les besoins d’optimisation augmentent
- Utilisez des audiences évaluées par Edge chaque fois que possible pour la personnalisation en temps réel. Réservez les audiences en flux continu et par lots pour des cas d’utilisation complémentaires.
- Mettez en œuvre l’expérimentation de contenu sur des expériences personnalisées pour vérifier que la personnalisation génère une augmentation mesurable du contenu par rapport au contenu par défaut
- Concevez une personnalisation avec une stratégie de dégradation élégante : si le profil ne peut pas être résolu en périphérie, affichez du contenu par défaut bien conçu plutôt qu’une expérience rompue
- Utilisez des attributs calculés pour créer des signaux de personnalisation à forte valeur ajoutée, tels que le score d’engagement, l’affinité du produit et le nombre de jours depuis le dernier achat, ce qui améliore la qualité de la personnalisation basée sur les segments et la prise de décision
- Maintenez un processus de gouvernance du contenu pour vous assurer que le contenu personnalisé reste à jour, sur la marque et conforme sur toutes les surfaces
- Surveillez les performances de personnalisation par segment pour identifier les audiences qui bénéficient le plus de la personnalisation et celles pour lesquelles l’effet élévateur est le plus important

### Décisions de compromis

>[!NOTE]
>**Compromis : granularité de Personalization et complexité de la gestion de contenu**
>
>Une personnalisation plus granulaire (plus de segments, plus de variantes de contenu, plus de surfaces) offre des expériences de plus en plus personnalisées, mais nécessite proportionnellement plus d’efforts de création, de maintenance et de gouvernance de contenu.
>
>- **Favoris de granularité plus élevée :** meilleure expérience client, engagement plus élevé, effet élévateur de conversion plus fort
>- **Une granularité plus faible favorise :** mise en œuvre plus rapide, réduction de la charge de maintenance du contenu et simplification de la gouvernance
>- **Recommandation :** commencez par 3 à 5 segments à fort impact (par exemple, les niveaux de fidélité ou les étapes de cycle de vie) avec une différenciation claire du contenu. Développez la granularité en fonction de l’effet élévateur de performance mesuré. Utilisez la prise de décision (option B) pour mettre à l’échelle la granularité sans augmentation proportionnelle de la gestion de contenu.

>[!NOTE]
>**Compromis : prise de décision en temps réel et contrôle de contenu déterministe**
>
>La personnalisation basée sur la prise de décision (option B) offre une optimisation dynamique, mais réduit le contrôle direct sur le contenu que chaque visiteur voit. La personnalisation basée sur segments (option A) offre un contrôle déterministe complet, mais limite l’optimisation dynamique.
>
>- **Favoris de la prise de décision :** évolutivité, optimisation automatique, scénarios d’éligibilité complexes
>- **Avantages basés sur les segments :** prévisibilité, contrôle de conformité, transparence des parties prenantes.
>- **Recommandation :** utilisez la personnalisation basée sur les segments pour les contenus sensibles à la conformité (messages réglementaires, tarification spécifique au niveau) où un contrôle exact est requis. Utilisez la prise de décision pour le contenu promotionnel, les offres et les recommandations où l’optimisation dynamique ajoute de la valeur.

>[!NOTE]
>**Compromis : disponibilité des données Edge et richesse de la personnalisation**
>
>La personnalisation évaluée par Edge se limite aux attributs disponibles dans le magasin de profils edge. Des signaux de personnalisation plus riches (historique comportemental complet, attributs calculés complexes) peuvent nécessiter une recherche ou un pré-calcul côté serveur.
>
>- **Edge uniquement privilégie** latence inférieure à la seconde, architecture la plus simple.
>- **L’enrichissement pré-calculé favorise :** signaux de personnalisation plus riches, définitions d’audience plus sophistiquées.
>- **Recommandation :** utilisez des attributs calculés pour pré-agréger les signaux comportementaux riches en attributs de profil disponibles sur le serveur Edge. Cela permet d’obtenir la richesse des données comportementales avec la vitesse d’évaluation Edge.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les technologies et configurations référencées dans ce guide.

### Personnalisation des canaux web

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Configuration du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### Canaux in-app et de carte de contenu

- [Présentation du canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Conditions préalables relatives au canal in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Créer des messages in-app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Canal de la carte de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configuration des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Créer des cartes de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization et contenu

- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Fonctions d&#39;assistance](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Collecte de données et SDK

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campagnes et expérimentation

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Attributs calculés et enrichissement

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Rapports et analyses

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Gouvernance et confidentialité

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
