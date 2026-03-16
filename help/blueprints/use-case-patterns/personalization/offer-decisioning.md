---
title: Offer Decisioning
description: Découvrez comment utiliser une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur plusieurs canaux.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7889'
ht-degree: 2%

---


# Offer Decisioning

Ce guide fournit une référence d’implémentation complète pour Offer Decisioning à l’aide de [!DNL Adobe Journey Optimizer] (AJO) Decisioning et [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui doivent mettre en œuvre une logique de sélection d’offres centralisée qui détermine la meilleure offre pour chaque profil client sur l’ensemble des canaux.

Utilisez ce guide pour comprendre ce qui doit être configuré, où se trouvent les choix et quels compromis s’appliquent à chaque décision.

Le modèle découple la décision « ce qu’il faut afficher » de la logique de canal « où l’afficher », ce qui permet une sélection d’offres cohérente et optimisée sur les e-mails, le web, les applications mobiles et tout autre point de contact. AJO Decisioning gère l&#39;ensemble du cycle de vie des offres : la création d&#39;offres et la gestion des catalogues, les règles d&#39;éligibilité (qui peut voir chaque offre), les stratégies de classement (comment sélectionner parmi les offres éligibles), les emplacements (où les offres apparaissent) et les politiques de décision (qui lient tout).

## Présentation du cas d’utilisation

Les entreprises ont souvent besoin de présenter l’offre, la promotion ou l’incitation la plus pertinente à chaque client au moment de l’interaction. Que l’interaction se produise dans une campagne par e-mail, sur la page d’accueil d’un site web, dans une application mobile ou à un point de décision dans un parcours à plusieurs étapes, le défi est le même : sélectionnez l’offre optimale dans un catalogue d’options disponibles en fonction de l’identité du client, de ses qualifications et de l’offre la plus susceptible de générer le résultat souhaité.

Offer Decisioning résout ce problème en centralisant toute la logique de sélection des offres dans le moteur de gestion des décisions d&#39;AJO. Plutôt que de coder en dur les affectations d’offres dans des campagnes ou des canaux individuels, le moteur de décision évalue les attributs de chaque profil, l’appartenance à l’audience et les signaux contextuels afin de déterminer la meilleure offre en temps réel. Cette centralisation garantit que le même client reçoit des offres cohérentes et optimisées, quel que soit le canal par lequel il s’engage.

Ce modèle diffère de la personnalisation web/de l’application pour les visiteurs connus en termes de portée : la prise de décision des offres est indépendante du canal et centralisée, tandis que la personnalisation des visiteurs connus se concentre sur la personnalisation des surfaces numériques. Elle diffère de la recommandation comportementale dans l’approche : Offer Decisioning utilise des règles d’éligibilité et des stratégies de classement explicites, tandis que la recommandation comportementale met l’accent sur les recommandations comportementales basées sur les signaux à l’aide de stratégies de sélection et de modèles ML.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.
**KPI : engagement**, taux de conversion, satisfaction de la clientèle (CSAT)

**[Stimuler les ventes croisées et les ventes incitatives](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promouvoir des produits ou services complémentaires et de qualité auprès des clients existants en fonction du comportement et de l’historique d’achat.
**KPI :** % de ventes incitatives/croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

**[Augmenter la fidélité du client et la valeur de durée de vie](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Approfondissez les relations client et optimisez la valeur à long terme par le biais de programmes de fidélité, de récompenses et d’un engagement personnalisé.
**KPI :** valeur de durée de vie du client, conservation, pourcentage de ventes incitatives/croisées

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont Offer Decisioning peut être appliqué dans la pratique.

- Prochaine meilleure offre dans les campagnes par e-mail — Sélectionnez la promotion la plus pertinente par destinataire au moment de l’envoi
- Bannière promotionnelle en temps réel sur le site web : la prise de décision sélectionne l’offre au chargement de la page en fonction du profil du visiteur.
- Carte in-app personnalisée offrant le meilleur incentives pour l’étape du cycle de vie de l’utilisateur
- Cohérence des offres cross-canal : la même logique de prise de décision sert les e-mails, le web et les notifications push afin que le client bénéficie d’une expérience d’offre unifiée
- Sélection dynamique de coupons ou de remises basée sur le niveau de valeur client (par exemple, les clients à forte valeur reçoivent une offre premium).
- Sélection d’offres de mise à niveau ou de vente incitative de produits en fonction du niveau d’abonnement actuel
- La récompense de fidélité offre une personnalisation basée sur le niveau et l’historique des activités

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer l’efficacité d’une implémentation d’Offer Decisioning.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’acceptation de l’offre | Pourcentage d’offres diffusées qui entraînent un clic, un échange ou une conversion | Clics ou rachats d’offres / Total des offres diffusées |
| Distribution de la sélection des offres | Proportion de chaque offre sélectionnée dans toutes les décisions | Nombre par offre / Nombre total de décisions rendues |
| Taux de secours | Pourcentage de décisions pour lesquelles aucune offre personnalisée n’a été qualifiée et la solution de secours a été diffusée | Impressions de secours/Nombre total de décisions |
| Taux de conversion | Pourcentage de destinataires de l&#39;offre qui ont effectué l&#39;action souhaitée (achat, inscription, échange) | Conversions/impressions d’offres |
| Revenu incrémentiel | Chiffre d’affaires attribuable aux offres sélectionnées pour la prise de décision par rapport à une population témoin ou une offre de secours | Chiffre d’affaires provenant d’offres personnalisées - Chiffre d’affaires de secours/contrôle |
| Score de cohérence cross-canal | Pourcentage de profils recevant la même offre sur plusieurs canaux dans une fenêtre définie | Offres cohérentes/Nombre total d’impressions multicanaux |
| Taux De Clics Publicitaires De L’Offre | Pourcentage d’impressions d’offres qui génèrent un clic | Clics sur les offres/impressions des offres |

## Modèle de cas d’utilisation

Cette section décrit la chaîne de fonctions et la définition de modèle pour Offer Decisioning.

**Offer Decisioning**

Utilisez une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur l’ensemble des canaux.

**Chaîne de fonctions :** évaluation d&#39;audience > Éligibilité de l&#39;offre > Stratégie de classement > Exécution des décisions > Diffusion > Reporting

Voir la section [Options d’implémentation](#implementation-options) pour savoir comment chaque composition se manifeste.

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Moteur de gestion des décisions pour la création d’offres, les règles d’éligibilité, les stratégies de classement, les emplacements et les politiques de décision ; la configuration des canaux et la création de messages pour la diffusion d’offres ; l’exécution de campagnes et de parcours
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Évaluation des audiences pour les segments d’éligibilité des offres ; données de profil et attributs calculés utilisés dans l’éligibilité et le classement
- **[!DNL Adobe Experience Platform] (AEP)** : banque de profils unifiée, résolution d’identité et base de données prenant en charge AJO et RT-CDP

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Sandbox AJO avec autorisations Decisioning activées. Rôles de gestion des offres (responsable de décision, approbateur d’offres) affectés à l’équipe d’implémentation. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Le schéma de profil doit inclure les attributs utilisés pour les règles d’éligibilité de l’offre (par exemple, niveau de fidélité, historique d’achat, type d’abonnement). Un schéma de réponse/interaction de l’offre pour le suivi des impressions, des clics et des conversions de l’offre doit être en place. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Supposé en place | Les attributs de profil utilisés dans les règles d’éligibilité doivent être à jour. Pour la diffusion web (option B), Web SDK doit être implémenté avec le service AJO activé sur le flux de données. Pour la diffusion par e-mail, les attributs de profil doivent pouvoir être résolus au moment de l’envoi. | [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configuration des identités et des profils | Supposé en place | Les profils doivent pouvoir être résolus sur tous les canaux où les offres sont diffusées. Pour la cohérence entre les offres cross-canal, l’identité unifiée est essentielle : le même profil doit être reconnu dans les contextes e-mail, web et mobile. Une politique de fusion Edge-active est requise pour la diffusion web/d’applications en temps réel. | [présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | Les audiences utilisées comme critères d’éligibilité de l’offre doivent être définies et évaluées (par exemple, « clients à forte valeur ajoutée », « utilisateurs à l’essai », « niveau or de fidélité »). La méthode d’évaluation doit correspondre à la latence de diffusion. Évaluation Edge pour le web/l’application en temps réel, le lot ou le streaming pour les campagnes par e-mail. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les scores de propension, les calculs de valeur de durée de vie et les mesures d’engagement de Customer AI améliorent considérablement l’efficacité de la stratégie de classement. Les attributs calculés tels que « jours depuis le dernier achat » ou « dépenses totales pendant 90 jours » permettent d’obtenir des règles d’éligibilité et un classement basé sur des formules plus précis. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Présentation de l’IA dédiée aux clients](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Gestion du cycle de vie des données | Recommandé | Les données d’historique des offres et d’événement de décision s’accumulent au fil du temps. Les politiques de conservation (expiration) doivent être configurées pour les jeux de données d’événements d’interaction d’offres afin de gérer le stockage et de respecter les exigences de conservation des données. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Expiration des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les étiquettes de gouvernance garantissent que les offres avec des critères de ciblage sensibles (par exemple, statut financier, conditions d’intégrité) sont conformes aux politiques d’utilisation des données. Les libellés des champs utilisés dans les règles d&#39;éligibilité empêchent le ciblage des offres non conformes. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Recommandé | Les performances du moteur de décision, les taux de secours et l&#39;intégrité de la diffusion des offres doivent être surveillés. Les alertes relatives à des taux de secours élevés peuvent indiquer une mauvaise configuration des règles d’éligibilité ou des problèmes d’actualisation des données. | [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Le rapport des performances des offres fait partie de la chaîne de fonctions (phase 7). L’analyse CJA permet de mesurer l’efficacité des offres cross-canal, d’attribuer l’impact du chiffre d’affaires et d’identifier les opportunités d’optimisation. | [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

Le tableau suivant répertorie les fonctions AJO et les phases d’implémentation où elles sont configurées.

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Prise de décision. | Phase 3 : configuration de la prise de décision | Créez des éléments d’offre, définissez des règles d’éligibilité, configurez des stratégies de classement, créez des offres de secours, définissez des emplacements et créez des politiques de décision |
| Configuration de canal | Phase 4 : configuration du canal et de la surface | Configurer des surfaces de canal e-mail, web, in-app ou basées sur du code pour la diffusion d’offres |
| Création de messages | Phase 5 : configuration du contenu et de la diffusion | Conception de modèles de messages avec des zones d&#39;emplacement d&#39;offre ; configuration d&#39;expériences basées sur du code pour la diffusion web/app |
| Exécution de la campagne | Phase 5 : configuration du contenu et de la diffusion | Exécuter des campagnes planifiées ou déclenchées par une API qui appellent des politiques de décision (option A) |
| Expérimentation de contenu | Phase 5 : configuration du contenu et de la diffusion | Vous pouvez éventuellement tester différentes stratégies de classement A/B ou proposer des variantes créatives |
| Rapports et analyse des performances | Phase 7 : Rapports et surveillance des performances | Surveillez la distribution de la sélection d’offres, les taux d’acceptation, les taux de secours et les performances au niveau du canal |

### [!DNL Real-Time CDP] (RT-CDP)

Le tableau suivant répertorie les fonctions RT-CDP et les phases d’implémentation où elles sont configurées.

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 2 : évaluation de l’audience | Définir et évaluer les audiences utilisées pour les règles d’éligibilité de l’offre ; sélectionner la méthode d’évaluation appropriée (par lots, en flux continu ou Edge) |
| Enrichissement de profil | Phase 1 (prise en charge) : attributs calculés | Enrichir les profils avec des attributs calculés et des scores de propension qui améliorent l’efficacité de la stratégie de classement |

## Conditions préalables

Remplissez les conditions préalables suivantes avant de commencer l’implémentation.

- [ ] AJO sandbox avec les fonctionnalités de gestion des décisions activées
- [ ] Rôles utilisateur disposant d’autorisations de gestion des décisions (création/modification d’offres, d’emplacements, de décisions)
- [ ] schéma Profil comprend les attributs requis pour l’éligibilité de l’offre (par exemple, niveau de fidélité, segment client, niveau d’abonnement)
- [ ] données de profil sont actuelles et activement ingérées pour l’actualisation des attributs d’éligibilité
- [ ] pour l’option A (e-mail) : surface de canal e-mail configurée avec le sous-domaine vérifié et le groupe d’adresses IP préchauffé
- [ ] Pour l’option B (Web/App) : Web SDK implémenté avec le service AJO activé sur le flux de données ; politique de fusion Edge-active configurée
- [ ] pour l’option C (Parcours) : autorisations de la zone de travail de Parcours et au moins un événement ou une audience d’entrée de parcours configurés
- [ ] Ressources de création d’offres (images, copie, CTA) préparées pour chaque combinaison d’offre et d’emplacement.
- [ ] du contenu de l’offre de secours préparé pour chaque emplacement
- [ ] des audiences pour les règles d’éligibilité d’offre définies et évaluées dans RT-CDP

## Options de mise en œuvre

Cette section décrit les options d’implémentation disponibles pour Offer Decisioning. Chaque option correspond à un canal de diffusion et à un contexte de cas d’utilisation différents.

### Option A : Email Offer Decisioning

Cette option est idéale pour sélectionner la meilleure offre à inclure dans les campagnes par e-mail sortantes (e-mails promotionnels, personnalisation de newsletter, e-mails relatifs au cycle de vie avec contenu d’offre dynamique). La décision est prise au moment du rendu du message pour chaque destinataire.

#### Fonctionnement

Les politiques de décision sont invoquées lors du rendu des e-mails pour sélectionner la meilleure offre pour chaque destinataire. Le modèle d’e-mail comprend une zone d’emplacement des offres dans laquelle le moteur de décision insère la représentation du contenu de l’offre sélectionnée (image, HTML ou texte). Au moment de l’envoi, le moteur évalue le profil de chaque destinataire par rapport aux règles d’éligibilité de l’offre, applique la stratégie de classement et incorpore le contenu de l’offre gagnante dans l’e-mail.

Cette approche fonctionne avec les campagnes planifiées (évaluées au moment de l’exécution de la campagne) et les e-mails incorporés au parcours (évalués lorsque le profil atteint le nœud d’action du message). Le contenu de l’offre (image, titre, corps de texte et CTA) est personnalisé par destinataire en fonction du résultat de la décision.

#### Considérations principales

- L’éligibilité de l’offre est évaluée au moment de l’envoi en utilisant le statut actuel du profil
- L’évaluation de l’audience par lots est suffisante, car les décisions se prennent pendant le rendu des messages
- Chaque offre nécessite une représentation de contenu HTML ou image pour l&#39;emplacement de l&#39;e-mail
- L’offre de secours doit contenir du contenu pour chaque emplacement d’e-mail utilisé

#### Avantages

- Chemin d’implémentation le plus simple : utilise la diffusion d’e-mails de campagne ou par parcours
- Aucune exigence SDK côté client
- Fonctionne avec l’infrastructure de messagerie et les surfaces de canal existantes
- Prend en charge des volumes d’audience importants par l’exécution de campagnes par lots

#### Restrictions

- La décision est prise au moment de l’envoi. Impossible de s’adapter au comportement post-envoi.
- Le contenu de l’offre est statique une fois l’e-mail diffusé (aucune mise à jour en temps réel)
- Limité aux attributs de profil disponibles dans le magasin de profils du hub (et non dans Edge)

#### Ressources Experience League

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B : Offer Decisioning en temps réel sur le web/sur les applications

Cette option est idéale pour la sélection d’offres en temps réel sur des pages web ou des applications mobiles (bannières promotionnelles de page d’accueil, widgets d’offre de tableau de bord de compte, cartes d’offre in-app ou toute surface numérique sur laquelle l’offre doit être sélectionnée au moment du chargement de la page ou du rendu de l’écran).

#### Fonctionnement

Les politiques de décision sont appelées au chargement de la page ou au rendu de l’écran de l’application via le réseau Edge Decisioning ou les expériences basées sur le code. Lorsqu’un visiteur charge une page, le SDK Web envoie une requête à Edge Network, qui évalue le profil Edge du visiteur par rapport aux règles d’éligibilité et aux stratégies de classement de l’offre. L’offre sélectionnée est renvoyée dans la réponse et rendue à l’emplacement configuré sur la surface numérique.

Pour les expériences basées sur du code, l’application récupère la réponse de décision et effectue le rendu du contenu de l’offre à l’aide d’une logique front-end personnalisée. Pour les expériences de canal web, le canal web AJO peut injecter le contenu de l’offre directement dans la page à l’aide de la création visuelle ou basée sur le code.

#### Considérations principales

- Nécessite une implémentation de Web SDK ou de Mobile SDK avec le service AJO activé sur le flux de données
- Une politique de fusion active Edge est requise pour les recherches de profil en temps réel
- Les audiences utilisées pour l’éligibilité doivent prendre en charge l’évaluation Edge (vérifications d’attributs simples et appartenance à un segment)
- Les représentations du contenu de l’offre doivent utiliser des formats d’URL JSON ou image pour le rendu côté client
- Le tracking des impressions doit être implémenté pour capturer les vues d’offres et les clics

#### Avantages

- Sélection d’offres en temps réel et en session en fonction de l’état du profil actuel du visiteur
- Latence de décision inférieure à la seconde via Edge Network
- Les offres s’adaptent aux données de profil les plus récentes disponibles sur Edge
- Prend en charge les tests A/B des stratégies d’offre via l’expérimentation de contenu

#### Restrictions

- Nécessite une implémentation de SDK côté client (Web SDK ou Mobile SDK)
- le profil Edge comporte un sous-ensemble d’attributs de profil hub complets - des règles d’éligibilité complexes peuvent ne pas être évaluées correctement
- Les segments Edge comportent des restrictions de complexité de règle de segment (aucune requête de série temporelle)
- Nécessite un développement front-end pour le rendu personnalisé dans les expériences basées sur du code

#### Ressources Experience League

- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Canal d’expérience basé sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

### Option C : nœud de décision du Parcours

Cette option est idéale pour la sélection d’offres dans un parcours à plusieurs étapes : la sélection de la meilleure offre à un point de décision dans un parcours client, puis sa diffusion via le nœud d’action suivant. Utilisez ceci lorsque la décision d’offre fait partie d’un flux d’orchestration plus large avec des attentes, des conditions et plusieurs actions de message.

#### Fonctionnement

Les politiques de décision sont appelées à partir d’un nœud de décision dans une zone de travail de parcours AJO. Lorsqu’un profil atteint le nœud de décision, le moteur évalue l’éligibilité et le classement de l’offre pour sélectionner l’offre optimale. L’offre sélectionnée renseigne l’action de message suivante : le contenu de l’offre à inclure, le canal à utiliser ou la branche de parcours à utiliser en fonction du résultat de l’offre.

Cette approche permet des parcours adaptatifs où la décision d’offre influence les étapes de parcours suivantes. Par exemple, un parcours peut sélectionner la meilleure offre, la diffuser par e-mail, attendre l&#39;engagement, puis poursuivre avec une notification push si l&#39;offre n&#39;a pas été ouverte.

#### Considérations principales

- Le parcours doit être conçu avec un nœud de décision suivi d’un ou de plusieurs nœuds d’action de message
- L’éligibilité de l’offre est évaluée à l’aide de l’état du profil au moment où le profil atteint le nœud de décision
- Les étapes d’attente de parcours entre la décision et la diffusion peuvent entraîner un changement de l’état du profil
- Peut se combiner avec l’embranchement par parcours pour emprunter différents chemins en fonction de l’offre sélectionnée

#### Avantages

- Intègre la sélection d’offres dans des flux d’orchestration à plusieurs étapes
- Active les parcours adaptatifs où le choix de l’offre influence les étapes suivantes
- Prise en charge de la diffusion cross-canal dans le même parcours (e-mail, notification push ou SMS)
- Peut se combiner avec des conditions de parcours pour le suivi de l’engagement post-offre

#### Restrictions

- Configuration plus complexe que la prise de décision de campagne autonome
- Des limites de débit de parcours s’appliquent (taux d’entrée de 5 000 profils par seconde)
- La décision est liée au contexte du parcours. Les modifications nécessitent le contrôle de version du parcours.
- Le parcours doit être republié pour que les mises à jour du catalogue d’offres ou de la politique de décision prennent effet

#### Ressources Experience League

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : prise de décision par e-mail | Option B : Web/application en temps réel | Option C : nœud de décision du Parcours |
| --- | --- | --- | --- |
| Idéal pour | Campagnes par e-mail par lots avec sélection d’offres par destinataire | Bannières d’offres en temps réel sur les surfaces web/d’application | Sélection d’offres dans des parcours orchestrés à plusieurs étapes |
| Latence de décision | À l’envoi (secondes par destinataire pendant le rendu par lots) | Sous-seconde (Edge Network) | Exécution du nœud en parcours (secondes) |
| Canal | E-mail | Web, application mobile, surfaces basées sur du code | Tout canal (e-mail, notification push, SMS) du parcours |
| SDK obligatoire | Non | Oui (Web SDK ou Mobile SDK) | Non (pour les e-mails/notifications push) ; Oui (si le canal web est une action de parcours) |
| Évaluation d’audience | Lot ou diffusion en continu | Edge | Lot, diffusion en continu ou Edge (selon l’entrée du parcours) |
| Portée des données de profil | Profil de hub complet | Profil Edge (sous-ensemble) | Profil de hub complet |
| Complexité | Faible | Medium-Grand | Moyenne |
| Débit | Élevée (volumes de campagnes par lots) | Élevée (échelle Edge Network) | Medium (des limites de débit par parcours s’appliquent) |

### Choisir la bonne option

Suivez les instructions ci-dessous pour sélectionner la meilleure option d’implémentation pour votre cas d’utilisation.

- **Choisissez l’option A** si le principal cas d’utilisation consiste à sélectionner la meilleure offre par destinataire dans les campagnes par e-mail sortantes et qu’aucun SDK côté client n’est disponible. Il s’agit du chemin d’implémentation le plus simple et il fonctionne bien pour les e-mails promotionnels, les newsletters et les campagnes de cycle de vie.
- **Choisissez l’option B** si les offres doivent être sélectionnées en temps réel au moment où un visiteur charge une page web ou ouvre une application mobile. Cela nécessite Web SDK ou Mobile SDK et une politique de fusion Edge-active, mais permet de sélectionner les offres les plus rapides et les plus contextuelles.
- **Choisissez l’option C** si la décision d’offre fait partie d’un parcours client plus large avec plusieurs étapes, attentes et embranchements conditionnels. Il s’agit du bon choix lorsque l’offre sélectionnée doit influencer les actions de parcours en aval ou lorsqu’un suivi multicanal basé sur l’engagement de l’offre est nécessaire.
- **Combiner les options** lorsque les offres doivent être diffusées de manière cohérente sur plusieurs canaux. Utilisez la même politique de décision pour les trois options afin de vous assurer qu’un client voit la même offre dans un e-mail (option A), sur le site web (option B) et dans le cadre d’un suivi parcours (option C).

## Phases de mise en œuvre

Les phases suivantes décrivent la séquence d&#39;implémentation de bout en bout pour Offer Decisioning.

### Phase 1 : validation des conditions préalables fondamentales

**Fonction d’application :** AEP : modélisation et préparation des données, AEP : configuration des identités et des profils

Cette phase confirme que la couche de données de base prend en charge Offer Decisioning. Les schémas de profil doivent inclure les attributs utilisés dans les règles d’éligibilité de l’offre et la configuration d’identité doit activer la résolution de profil cross-canal.

#### Décision : attributs de profil pour l’éligibilité

Déterminez quels attributs de profil seront utilisés dans les règles d’éligibilité de l’offre.

>[!NOTE]
>Le choix des attributs de profil affecte à la fois la conception des règles d’éligibilité et l’efficacité des stratégies de classement. Tenez compte des attributs calculés et des scores de propension pour améliorer la qualité des décisions.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Attributs de profil standard (niveau de fidélité, historique d’achat) | Les attributs existent déjà dans le schéma de profil | Aucune modification de schéma nécessaire ; vérifiez l’actualisation des données. |
| Attributs calculés (valeur de durée de vie, score d’engagement) | L&#39;éligibilité ou le classement dépend des données comportementales agrégées | Nécessite une configuration S1 ; ajoute une dépendance à la cadence d’actualisation des attributs calculés |
| Scores de propension de l’IA dédiée aux clients | Le classement doit utiliser les prédictions basées sur le machine learning | Nécessite suffisamment de données de formation (plus de 10 000 profils avec événement cible) ; modélise le temps de formation |

#### Détails de configuration clés

- Vérifiez que le schéma de profil inclut les champs référencés dans les règles d’éligibilité (par exemple, `_tenantId.loyaltyTier`, `_tenantId.subscriptionType`).
- Confirmer que le schéma de suivi des interactions d’offre existe pour les événements d’impression, de clic et de conversion
- Pour l’option B : vérifiez que la politique de fusion Edge-active est configurée et que le service AJO est activé pour le flux de données Web SDK

#### Documentation Experience League

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Activation d&#39;un schéma pour Profil](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 2 : configuration de l’évaluation des audiences

**Fonction d’application :** RT-CDP : évaluation de l’audience

Cette phase définit et évalue les audiences utilisées comme critères d&#39;éligibilité de l&#39;offre. Ces audiences déterminent quels segments de clients sont qualifiés pour des offres spécifiques (par exemple, les « clients à forte valeur ajoutée » sont qualifiés pour les offres Premium, les « utilisateurs en version d’essai » sont qualifiés pour les offres de conversion).

#### Décision : méthode d’évaluation de l’audience

Déterminez la vitesse à laquelle l’adhésion à l’audience doit être mise à jour pour l’éligibilité de l’offre.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Évaluation par lots | Option A (campagnes par e-mail) où l’éligibilité est évaluée au moment de l’envoi | Plus simple ; toutes les expressions de règle de segment prises en charge ; actualisation quotidienne ou à la demande |
| Évaluation en flux continu | Option A ou C lorsque des mises à jour d’audience en temps quasi réel sont nécessaires entre les lots | Automatique pour les segments éligibles ; prise en charge limitée des règles de segment (événements uniques, comparaisons d’attributs) |
| Évaluation Edge | Option B (web/app real-time) où l’éligibilité doit être évaluée au chargement de la page | Sous-seconde ; requise pour les offres web/d’application en temps réel ; limitée à de simples vérifications d’attributs et à l’appartenance à un segment |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle

#### Détails de configuration clés

- Définir les audiences de ciblage pour l’éligibilité de l’offre (par exemple, « Niveau de fidélité or », « Clients à forte valeur ajoutée », « Utilisateurs en version d’évaluation »)
- Définissez des audiences de suppression si nécessaire (par exemple, « Offre X récemment reçue »)
- Pour l’option B : vérifier que les audiences d’éligibilité remplissent les critères de l’évaluation Edge — éviter les requêtes de série temporelle et les agrégations complexes dans les expressions de règle de segment

#### Là où les options divergent

**Pour L’Option A (Email Decisioning) :**
L’évaluation par lots ou par flux est suffisante. Les audiences sont évaluées avant ou pendant l’exécution de la campagne. Les expressions de règle de segment complexes, y compris les conditions temporelles et les agrégations d’événements, sont entièrement prises en charge.

**Pour L’Option B (Web/App Real-Time) :**
Une évaluation Edge est requise. Les audiences doivent utiliser des vérifications d’attributs simples ou des conditions d’appartenance à un segment. Testez l’éligibilité Edge en vérifiant que l’expression de règle de segment est qualifiée pour la segmentation Edge.

**Pour L’Option C (Nœud De Décision De Parcours) :**
Toute méthode d’évaluation fonctionne en fonction des critères d’entrée sur le parcours. Si le parcours utilise une entrée basée sur une audience, la méthode d’évaluation de l’audience correspond aux exigences du parcours.

#### Documentation Experience League

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Phase 3 : configuration de la prise de décision

**Fonction d’application :** AJO : prise de décision

Il s’agit de la phase principale dans laquelle le catalogue d’offres, les règles d’éligibilité, les stratégies de classement et les politiques de décision sont créés. Cette phase crée la configuration du moteur de décision que toutes les options de diffusion (A, B, C) partagent.

#### Décision : canal d&#39;emplacement et format de contenu

Déterminez où les offres apparaîtront et dans quel format.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail (HTML) | Option A : offre de contenu rendu en tant qu’HTML dans le corps de l’e-mail | Prend en charge la mise en forme enrichie ; doit être compatible avec les clients de messagerie |
| E-mail (URL de l’image) | Option A : offre générée sous forme d’image hébergée dans un e-mail | Plus simple : l’image doit être hébergée et accessible ; pas de texte dynamique |
| Web (HTML) | Option B : offre générée en tant qu’HTML sur une page web | Contrôle de disposition complet ; prend en charge les éléments interactifs |
| Web/Mobile (JSON) | Option B — Données d’offre renvoyées au format JSON pour le rendu personnalisé | Flexibilité maximale ; nécessite un développement front-end pour le rendu. |
| Basé sur le code (JSON) | Option B — Données d’offre pour les surfaces d’expérience basées sur le code | L&#39;application contrôle le rendu ; plus flexible |

#### Décision : stratégie de classement

Déterminez comment la meilleure offre doit être sélectionnée parmi les offres éligibles.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Basé sur la priorité (manuel) | Catalogues d’offres de petite taille ; règles métier explicites pour la commande d’offres | Plus simple à configurer ; affectation manuelle d’une valeur de priorité par offre ; déterministe |
| Basé sur une formule (expression personnalisée) | Le classement doit prendre en compte les attributs de profil (par exemple, niveau de fidélité, récence) | Flexible ; utilise les données de profil pour calculer un score de classement ; nécessite la conception de l’expression de la règle de segment |
| Classement par l’IA (optimisation automatique) | Catalogues d’offres volumineux ; souhaitez que ML optimise la sélection au fil du temps. | Nécessite au moins 1 000 événements de conversion pour la formation des modèles ; tire des enseignements des données de performances des offres |

#### Décision : limitation de l’offre

Déterminez s’il doit y avoir des limites au nombre d’affichages d’une offre.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Limite par profil | Empêcher qu’une même offre ne soit présentée trop de fois à un seul client | Évite la fatigue de l’offre ; retard de quelques secondes dans les scénarios à débit élevé |
| Limite globale | Limiter le nombre total d’impressions pour une offre sur tous les profils (par exemple, inventaire limité) | Contrôle l’offre d’offre. Une fois la limite atteinte, l’offre est exclue des décisions. |
| Pas de limitation | Les offres ont une disponibilité illimitée | Simplest ; adapté aux promotions permanentes |

**Navigation dans l’interface utilisateur :** Composants > Gestion des décisions > Emplacements / Règles / Offres / Décisions

#### Détails de configuration clés

1. **Créer des emplacements** — Définissez où les offres apparaissent en spécifiant le type de canal et le format de contenu pour chaque emplacement.
   - Interface utilisateur : Composants > Gestion des décisions > Emplacements
   - Créez un emplacement par combinaison de canal/format (par exemple, « Bannière principale d’e-mail - HTML », « Page d’accueil web - JSON », « Carte d’application mobile - JSON »).

2. **Définir des règles d’éligibilité** — Créez des règles à l’aide d’expressions de règle de segment qui font référence aux attributs de profil ou à l’appartenance à une audience.
   - Interface utilisateur : Composants > Gestion des décisions > Règles
   - Les règles peuvent référencer l’appartenance à une audience, les attributs de profil (niveau de fidélité, type d’abonnement), les contraintes de date ou les données contextuelles

3. **Créer des offres personnalisées** — Créez chaque offre avec des représentations de contenu pour chaque emplacement, attribuez des règles d’éligibilité, définissez une priorité et configurez une limitation facultative.
   - Interface utilisateur : Composants > Gestion des décisions > Offres > Créer une offre
   - Chaque offre nécessite une représentation du contenu par emplacement (par exemple, HTML pour les e-mails, JSON pour le web)
   - Attribuez des règles d’éligibilité pour contrôler quels profils peuvent voir chaque offre
   - Définir les dates de validité de l’offre (début/fin) et le capping de la fréquence facultatif
   - Valider chaque offre pour la rendre éligible à la prise de décision

4. **Créer des offres de secours** — Créez une offre par défaut pour chaque emplacement affiché lorsqu&#39;aucune offre personnalisée ne se qualifie.
   - Interface utilisateur : Composants > Gestion des décisions > Offres > Créer une offre de secours
   - La solution de secours doit comporter des représentations pour chaque emplacement utilisé dans la décision

5. **Créer des qualificateurs de collection et des collections** — Organisez les offres en collections à l’aide de balises de qualificateur.
   - Interface utilisateur : Composants > Gestion des décisions > Qualificateurs de collection
   - Offres liées au groupe (par exemple, « Promotions d’été », « Récompenses de fidélité ») à utiliser dans les portées de décision

6. **Créer des politiques de décision** — Liez les emplacements, les collections, les stratégies de classement et les offres de secours dans des décisions exécutables.
   - Interface utilisateur : Composants > Gestion des décisions > Décisions > Créer une décision
   - Chaque portée de décision relie un emplacement à une collection et spécifie la méthode de classement

#### Documentation Experience League

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Création de qualificateurs de collection](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4 : configuration du canal et de la surface

**Fonction d’application :** AJO : Configuration de canal

Cette phase configure les surfaces de canal par lesquelles les offres seront diffusées. La configuration dépend de la ou des options d’implémentation utilisées.

#### Décision : type de canal

Déterminez le canal de messagerie dont le cas d’utilisation a besoin.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail | Option A ou Option C avec diffusion par e-mail | Nécessite la délégation de sous-domaine, le groupe d’adresses IP, les paramètres de l’expéditeur |
| Web | Option B pour la diffusion sur la surface web | Nécessite une configuration de SDK Web et de flux de données |
| In-app | Option B pour la diffusion d’applications mobiles | Nécessite des informations d’identification Mobile SDK et push |
| Expérience basée sur le code | Option B pour les surfaces de rendu personnalisées | Plus flexible ; l’application gère le rendu |

#### Là où les options divergent

**Pour L’Option A (Email Decisioning) :**
- Interface utilisateur : Administration > Canaux > Surfaces de canal > Créer une surface (e-mail)
- Configurer le sous-domaine, le groupe d’adresses IP, le nom/l’adresse e-mail de l’expéditeur, la réponse, les paramètres de désabonnement
- Vérifiez les enregistrements SPF, DKIM et DMARC pour le sous-domaine d’envoi

**Pour L’Option B (Web/App Real-Time) :**
- Interface utilisateur : Administration > Canaux > Surfaces de canal > Créer une surface (web ou in-app)
- Pour le web : configurer le modèle d’URL de surface web
- Pour les expériences basées sur du code : définissez l’URI de surface pour l’application
- Vérifiez que le service AJO est activé pour le flux de données.

**Pour L’Option C (Nœud De Décision De Parcours) :**
- Configurer des surfaces de canal pour chaque canal utilisé dans le parcours (e-mail, notification push, SMS ou web)
- Chaque action de message de parcours nécessite une surface de canal active correspondante

#### Documentation Experience League

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5 : configuration du contenu et de la diffusion

**Fonction d’application :** AJO : création de messages, AJO : exécution de campagnes

Cette phase conçoit les modèles de messages ou les surfaces d’expérience qui affichent l’offre sélectionnée, puis configure le mécanisme de diffusion (campagne, parcours ou expérience basée sur un code).

#### Décision : approche de contenu pour le rendu des offres

Déterminez comment le contenu de l&#39;offre doit être intégré au message ou à l&#39;expérience.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Composant Décision d’offre dans Email Designer | Option A — Incorporer l’emplacement de l’offre dans le modèle d’e-mail | Glisser-déposer ; le contenu de l’offre s’affiche automatiquement en fonction du résultat de la décision |
| Expérience basée sur le code avec la politique de décision | Option B : l’application récupère et effectue le rendu des données d’offre | Contrôle maximal du rendu ; nécessite un développement front-end. |
| Action de message de parcours avec décision incorporée | Option C : le nœud de décision transmet le contenu de l’offre au message de parcours | La sélection et la diffusion des offres sont orchestrées dans le flux du parcours |

#### Décision : type de campagne (option A uniquement)

Déterminez s’il s’agit d’une campagne marketing planifiée ou d’une campagne déclenchée par une API.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Campagne planifiée | Envois par lots ponctuels ou récurrents à une audience définie | Audience évaluée au moment de l’exécution ; définir la date/heure ou la périodicité |
| Campagne déclenchée par l’API | Envois pilotés par les événements ou déclenchés par le système vers des profils spécifiés | Profils spécifiés dans la payload de déclenchement ; prend en charge jusqu’à 20 destinataires par requête |

#### Là où les options divergent

**Pour L’Option A (Email Decisioning) :**

1. Créez l’e-mail à l’aide du Designer d’e-mail.
   - Interface utilisateur : Campagnes > Créer une campagne > Sélectionner un e-mail > Modifier le contenu
   - Insérez un composant Décision d&#39;offre dans la disposition de l&#39;e-mail pour définir la zone d&#39;emplacement
   - Ajouter des jetons de personnalisation pour le contenu au niveau du profil (nom, niveau de fidélité)
   - Configurer l’objet et le pré-titre avec une personnalisation facultative
2. Création et configuration de la campagne
   - Interface utilisateur : Campagnes > Créer une campagne > Planifié ou déclenché par l’API
   - Lier l’audience cible et sélectionner la surface de canal
   - Définir le planning d’exécution ou la configuration du déclencheur d’API
   - Vérification et activation de la campagne

**Pour L’Option B (Web/App Real-Time) :**

1. Configurer l’expérience basée sur le code ou le canal web
   - Interface utilisateur : Campagnes > Créer une campagne > Expérience basée sur le code (ou web)
   - Lier la politique de décision à la surface d’expérience
   - Définir le format de rendu (réponse JSON pour le code ; éditeur visuel pour le canal web)
2. Implémentation du rendu côté client
   - Utiliser la réponse `sendEvent` de Web SDK pour récupérer l&#39;offre sélectionnée
   - Effectuez le rendu du contenu de l’offre à l’emplacement désigné sur la page
   - Implémenter le suivi des impressions et des clics

**Pour L’Option C (Nœud De Décision De Parcours) :**

1. Concevoir le parcours avec un nœud de décision
   - Interface utilisateur : Parcours > Créer un Parcours > Ajouter un nœud de décision
   - Configurez le nœud de décision pour appeler la politique de décision à partir de la phase 3
2. Ajouter des nœuds d’action de message après la décision
   - Configurer des actions de type e-mail, push ou SMS qui font référence à l’offre sélectionnée
   - Ajouter des étapes d’attente, des conditions ou un embranchement en fonction de l’engagement de l’offre
3. Publication du parcours

#### Documentation Experience League

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 6 : test et validation

**Fonction d’application :** AJO: Prise de décision, AJO: Création de messages

Cette phase valide que le moteur de prise de décision renvoie les offres correctes pour les profils de test et que le contenu de l’offre s’affiche correctement dans chaque canal de diffusion.

#### Test de la logique de prise de décision

Utilisez des profils de test avec des attributs connus pour vérifier que les offres correctes sont sélectionnées en fonction de l’éligibilité et du classement.

- Créez des profils de test qui correspondent à différents critères d’éligibilité (par exemple, niveau Gold, niveau Silver, utilisateur Trial).
- Vérifiez que chaque profil de test reçoit l’offre attendue
- Vérifiez que les profils correspondant à aucune règle d’éligibilité reçoivent l’offre de secours

#### Test du rendu du contenu

Prévisualisez le contenu de l&#39;offre dans chaque canal de diffusion.

- Pour l’option A : utiliser l’aperçu d’e-mail avec les profils de test pour vérifier que le contenu de l’offre est correctement rendu
- Pour l’option B : test de la réponse Edge Decisioning dans un environnement d’évaluation
- Pour l’option C : utiliser le mode Test parcours pour vérifier que le nœud de décision sélectionne correctement

#### Validation du suivi des impressions

Vérifiez que les impressions, clics et conversions d’offres font l’objet d’un suivi.

- Vérifier que les événements d’interaction d’offre apparaissent dans les jeux de données de suivi
- Confirmer l’attribution entre les impressions d’offre et les conversions en aval

#### Documentation Experience League

- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Envoyer des BAT par e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### Phase 7 : configuration des rapports et de la surveillance des performances

**Fonction d’application :** AJO : Rapports et analyse des performances

Cette phase configure les rapports pour effectuer le suivi de la distribution de sélection des offres, des taux d’acceptation, de l’impact de la conversion et des taux de secours. Cette phase couvre à la fois les rapports natifs AJO et l’analyse cross-canal basée sur CJA.

#### Décision : méthode de création de rapports

Déterminez quels outils de création de rapports sont nécessaires pour l’analyse des performances des offres.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rapports natifs AJO uniquement | Suivi opérationnel de campagnes ou de parcours individuels | Accès rapide ; diffusion et mesures d’engagement intégrées ; analyse inter-entités limitée |
| Analyse de l’espace de travail CJA | Efficacité des offres cross-canal, attribution des recettes, analyse funnel | Nécessite une connexion CJA et une vue de données ; fonctionnalités d’analyse plus approfondies |
| AJO et CJA | Couverture opérationnelle et analytique complète | Recommandé pour les implémentations de production ; AJO pour la surveillance en temps réel et CJA pour l’analyse stratégique. |

#### Détails de configuration clés

1. **Création de rapports natifs AJO** — Surveillez les performances des campagnes ou des parcours à l&#39;aide de rapports intégrés.
   - Interface utilisateur : Campagnes > Sélectionner une campagne > Rapport à toute heure (ou Rapport dynamique)
   - Vérifier les mesures spécifiques aux offres : impressions par offre, taux de clic publicitaire par offre, taux de secours
   - Surveiller les funnel de diffusion : Ciblé > Envoyé > Diffusé > Ouvertures > Clics

2. **Analyse CJA (recommandée)** — Créez des tableaux de bord de performances des offres cross-canal.
   - Configurer une connexion CJA incluant des jeux de données d’interaction d’offres AJO
   - Créez une vue de données avec des dimensions spécifiques à l’offre (nom de l’offre, emplacement, décision) et des mesures (impressions, clics, conversions)
   - Créer une analyse de l’espace de travail pour : répartition de la sélection des offres, taux d’acceptation par segment, impact sur le chiffre d’affaires, cohérence entre les offres cross-canal

#### Documentation Experience League

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage pour les implémentations d’Offer Decisioning.

### Mécanismes de sécurisation et limites

Tenez compte des mécanismes de sécurisation et limites de plateforme suivants lors de la planification de votre implémentation.

- Maximum de 10 000 offres personnalisées approuvées par sandbox — [&#x200B; Mécanismes de sécurisation de la gestion des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 30 emplacements par décision
- Maximum de 30 portées de collection par demande de décision
- Les modèles de classement par l’IA nécessitent au moins 1 000 événements de conversion pour la formation
- Les compteurs de limitation d’offre peuvent présenter un retard de quelques secondes maximum dans les scénarios à débit élevé
- les décisions Edge sont limitées aux attributs de profil disponibles dans le magasin de profils edge
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de Platform](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Une seule politique de fusion peut être active sur Edge par sandbox
- Maximum de 500 campagnes actives en direct par sandbox
- Limite du taux d’entrée du parcours : 5 000 profils par seconde
- Maximum de 10 surfaces de canal par type de canal par sandbox

### Pièges courants

Évitez ces problèmes fréquents lors de la mise en œuvre.

- **La décision renvoie toujours une offre de secours :** cela signifie généralement que les offres personnalisées ne sont pas approuvées, qu&#39;elles se trouvent en dehors de leur période de validité ou que les règles d&#39;éligibilité ne correspondent pas aux attributs du profil de test. Vérifiez la précision de chaque condition : statut d’approbation, période et expression de règle de segment. Vérifiez également que les limites de limitation n’ont pas été atteintes.
- **L’offre n’apparaît pas dans la collection :** assurez-vous que l’offre a été balisée avec le qualificateur de collection approprié et que le filtre de collection correspond. Les offres doivent être balisées et approuvées pour apparaître dans les portées de décision basées sur la collection.
- **Formule de classement non appliquée :** vérifiez que la formule est valide sur le plan syntaxique et fait référence à des attributs de profil accessibles. Les erreurs de formule reviennent silencieusement au classement par priorité, sans erreur visible.
- **La diffusion Edge renvoie une personnalisation vide :** assurez-vous que le flux de données est configuré avec le service [!DNL Adobe Journey Optimizer] activé et que la portée de décision est correctement formatée. Vérifiez que la politique de fusion Edge-active existe.
- **Offres incohérentes sur plusieurs canaux :** si des politiques de décision distinctes sont utilisées par canal, le même profil peut recevoir différentes offres. Utilisez une politique de décision unique sur l’ensemble des canaux par souci de cohérence ou acceptez une divergence intentionnelle basée sur des emplacements spécifiques aux canaux.
- **Le contenu de l’offre n’est pas rendu dans l’e-mail :** vérifiez que la représentation du contenu de l’offre correspond au format d’emplacement de l’e-mail (HTML ou URL de l’image). Les représentations manquantes génèrent des zones d&#39;emplacement vides.

### Bonnes pratiques

Suivez ces recommandations pour une implémentation réussie d’Offer Decisioning.

- **Commencez par un petit catalogue d’offres et itérez** — Commencez par 5 à 10 offres et développez-les à mesure que le cadre de prise de décision est validé. Cela simplifie la résolution des problèmes et garantit que les règles d’éligibilité fonctionnent correctement avant la mise à l’échelle.
- **Utiliser les qualificateurs de collection de manière stratégique** — Balisez les offres par catégorie (par exemple, « Acquisition », « Rétention », « Vente incitative ») pour permettre des portées de décision flexibles basées sur la collection qui peuvent être réutilisées dans les campagnes et les parcours.
- **Créez toujours des offres de secours significatives** — Les offres de secours ne sont pas seulement un filet de sécurité ; elles constituent l’expérience par défaut pour les profils qui ne correspondent à aucune règle d’éligibilité. Investissez dans un contenu de secours qui offre de la valeur, même sans personnalisation.
- **Concevez des règles d’éligibilité qui s’excluent mutuellement dans la mesure du possible** — Lorsque plusieurs offres ont des critères d’éligibilité qui se chevauchent, la stratégie de classement devient critique. Si les exigences commerciales imposent une offre spécifique pour un segment spécifique, définissez des règles d’éligibilité s’excluant mutuellement au lieu de vous fier uniquement au classement.
- **Tester avec des profils représentatifs des arcs pour l’option B** — Les profils Edge contiennent un sous-ensemble d’attributs de profil de hub. Testez avec des profils ayant des attributs disponibles sur le serveur Edge afin de vous assurer que l’éligibilité est correctement évaluée en production.
- **Surveiller les taux de secours en tant que mesure d’intégrité** — Un taux de secours élevé (supérieur à 20-30 %) indique que le catalogue d’offres ne couvre pas suffisamment de segments de clientèle. Développez le catalogue d&#39;offres ou élargissez les règles d&#39;éligibilité.
- **Version des politiques de décision plutôt que de modifier les politiques actives** — Créez une nouvelle version de politique de décision plutôt que de modifier une version active. Cela évite d’interrompre les campagnes actives et permet la comparaison A/B des stratégies de décision.

### Décisions de compromis

Tenez compte des compromis suivants lors de la prise de décisions relatives à l’architecture et à la configuration.

#### Précision d&#39;éligibilité / couverture d&#39;offre

Des règles d’éligibilité strictes garantissent que chaque offre n’atteint que les profils les plus pertinents, mais peuvent entraîner des taux de secours élevés lorsque les profils ne correspondent à aucune offre. Des règles d’éligibilité étendues optimisent la couverture d’offre mais réduisent la précision de personnalisation.

- **Favoris d’éligibilité stricts :** taux d’acceptation plus élevés, meilleure personnalisation, fatigue d’offre plus faible
- **Favoris d’éligibilité étendus :** taux de secours réduits, plus de profils reçoivent des offres personnalisées, gestion plus simple des règles
- **Recommandation :** Commencez par des règles d’éligibilité plus larges et resserrez-les en fonction des données de performance. Surveillez les taux de secours et d’acceptation pour trouver le bon équilibre. Utilisez des stratégies de classement pour différencier les offres largement éligibles.

#### Classement en fonction de la priorité par rapport au classement par l’IA

Le classement par priorité donne à l’entreprise un contrôle total sur les offres affichées, tandis que le classement par IA s’optimise pour la conversion, mais réduit le contrôle humain sur la sélection des offres.

- **Favoris basés sur les priorités :** contrôle de l’entreprise, prévisibilité, aucune exigence de données de formation, déploiement immédiat.
- **Favoris classés par l’IA :** optimisation des conversions, découverte de modèles inattendus, adaptation automatique au changement du comportement des clients
- **Recommandation :** utilisez le classement par priorité pour les lancements initiaux et les offres sensibles à la réglementation où le contrôle commercial est primordial. Passez à un classement par l’IA pour les cas d’utilisation de gros volumes optimisés pour de bonnes performances dès que des données de conversion suffisantes (plus de 1 000 événements) sont disponibles.

#### Politique de décision unique par rapport aux politiques de décision par canal

Une politique de décision unique garantit la cohérence de l’offre sur tous les canaux, mais limite l’optimisation par canal. Les politiques par canal permettent un classement et une éligibilité spécifiques au canal, mais risquent d’entraîner des expériences client incohérentes.

- **Avantages d’une politique unique :** cohérence cross-canal, gestion simplifiée, reporting unifié
- **Les politiques par canal favorisent :** classement optimisé pour le canal, éligibilité spécifique au canal (par exemple, offres web uniquement), itération indépendante.
- **Recommandation :** commencez par une politique de décision unique pour la cohérence cross-canal. Créez des politiques par canal uniquement lorsque les besoins de l’entreprise exigent des stratégies d’offre spécifiques au canal (par exemple, ventes flash exclusives sur le web).

#### Prise de décision Hub (option A/C) par rapport à la prise de décision Edge (option B)

La prise de décision Hub a accès au profil complet, mais fonctionne au moment de l’envoi. La prise de décision d’Edge fonctionne en temps réel avec une latence inférieure à la seconde, mais elle se limite aux attributs de profil disponibles sur le serveur Edge.

- **Avantages de la prise de décision Hub :** accès à des données de profil complètes, des règles d’éligibilité complexes et des volumes de campagnes par lots.
- **La prise de décision Edge privilégie :** le contexte en temps réel, la personnalisation en session, la réponse de moins d’une seconde
- **Recommandation :** utilisez la prise de décision hub pour les canaux sortants (e-mail, push) où les données de profil complètes améliorent la pertinence de l’offre. Utilisez la prise de décision Edge pour les canaux entrants (web, application) où la réponse en temps réel est essentielle. Assurez-vous que les règles d’éligibilité pour Edge utilisent uniquement les attributs disponibles pour Edge.

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les composants utilisés dans ce modèle de cas d’utilisation.

### Gestion des décisions

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Création de qualificateurs de collection](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Diffusion d’offres

- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Diffuser des offres à l’aide de l’API Edge Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Diffuser des offres à l’aide de l’API Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Paramètres de surface d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Délégation de sous-domaines](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configuration du canal de notification push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Création et personnalisation de messages

- [Concevoir le contenu d’un e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Prévisualiser et tester votre contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campagnes et parcours

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Prise en main des parcours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Expérimentation de contenu

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Audiences et segmentation

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profil et identité

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation de Customer AI](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Modélisation et collecte des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Rapports et analyses

- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Parcours du rapport global](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Gouvernance et cycle de vie des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consentement dans Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Garde-fous

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutoriels

- [Prise en main de l’API Decision Management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
