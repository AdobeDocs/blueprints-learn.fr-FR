---
title: Audience Collaboration avec correspondance de segments
description: Découvrez comment partager et faire correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de la correspondance de segments.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6238'
ht-degree: 1%

---


# Collaboration avec l’audience à l’aide de la correspondance de segments

Ce guide fournit une référence d’implémentation complète pour la collaboration avec les audiences à l’aide de [!DNL Segment Match] dans [!DNL Real-Time CDP] et [!DNL Adobe Experience Platform]. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de partager et de faire correspondre des segments d’audience entre des sandbox ou des organisations dans le respect de la confidentialité.

Utilisez ce plan pour comprendre les approches disponibles, évaluer les arbitrages et naviguer [!DNL Adobe Experience League] pour obtenir des instructions de configuration détaillées.

[!DNL Segment Match] permet à plusieurs organisations [!DNL Experience Platform] (ou sandbox au sein d’une organisation) de collaborer sur les données d’audience en partageant les informations d’appartenance à un segment sans exposer les informations d’identification personnelles sous-jacentes. Les participants peuvent estimer le chevauchement, partager des audiences et activer les profils correspondants vers des destinations en aval.

## Présentation du cas d’utilisation

Les entreprises doivent de plus en plus collaborer sur les données d’audience avec des partenaires, des filiales ou plusieurs unités opérationnelles tout en maintenant des contrôles stricts de la confidentialité. La collaboration avec les audiences répond à ce besoin en activant le partage de segments sécurisé par le biais de [!DNL Segment Match], une fonctionnalité de [!DNL Real-Time CDP] qui permet à deux organisations [!DNL Experience Platform] ou plus (ou sandbox) d’échanger des informations sur l’appartenance à une audience à l’aide d’identifiants hachés et sécurisés pour la confidentialité.

Le scénario commercial implique généralement une organisation (l’expéditeur) qui a créé un segment d’audience utile et souhaite le partager avec une organisation partenaire (le destinataire) à des fins de ciblage, de suppression ou d’enrichissement communs. Avant de partager, les deux parties peuvent estimer le chevauchement des audiences pour en évaluer la valeur. Une fois partagée, l’organisation de réception peut activer l’audience correspondante par l’intermédiaire de ses propres destinations.

Ce modèle est distinct de l’activation d’audience standard, car il fonctionne entre des organisations ou des sandbox plutôt qu’avec des destinations publicitaires ou marketing externes. Il se distingue également des salles blanches de données ou des plateformes de collaboration tierces, car il fonctionne en mode natif dans l’écosystème Adobe à l’aide d’une infrastructure d’identités [!DNL Experience Platform].

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés. La collaboration avec les audiences permet aux entreprises de découvrir de nouveaux pools de prospects en comparant leurs segments aux audiences de partenaires, en identifiant les chevauchements à forte valeur ajoutée et en atteignant de nouveaux clients par le biais d’une activation conjointe.

- **KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads
- [Acquérir de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Réduire le coût d’acquisition du client

Améliorez l’efficacité du ciblage, supprimez les clients existants des campagnes d’acquisition et optimisez les dépenses multimédia. En partageant les segments de suppression entre les organisations ou les unités commerciales, les équipes peuvent éviter les dépenses inutiles sur des clients déjà convertis et concentrer les budgets sur des prospects réellement nouveaux.

- **KPI :** coût d’acquisition client, coût par lead, efficacité
- [Réduire le coût d’acquisition du client](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace. [!DNL Segment Match] permet la suppression des audiences entre les organisations et le ciblage conjoint, ce qui réduit la duplication et améliore la précision.

- **KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels
- [Optimiser les dépenses marketing et le retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

- **Correspondance entre l’éditeur et l’annonceur et l’audience** — Une marque partage son segment client à forte valeur ajoutée avec un éditeur de médias afin d’estimer le chevauchement et de cibler les utilisateurs appariés avec des annonces personnalisées, ce qui améliore la pertinence de la campagne sans exposer les informations d’identification personnelle.
- **Suppression intermarques au sein d’une société holding** — Plusieurs marques d’une organisation parent partagent des segments de clientèle afin de supprimer les clients existants de marques sœurs des campagnes d’acquisition, ce qui réduit le gaspillage des dépenses publicitaires.
- **Enrichissement de l’audience du réseau de médias de vente au détail** — Un retailer partage des segments basés sur les achats avec les partenaires de marque CPG, ce qui permet aux marques de cibler des acheteurs éprouvés sur le réseau de médias retailer avec des taux de conversion plus élevés.
- **Découverte d’audiences de partenaires de co-marketing** — Deux marques non concurrentes évaluent le chevauchement des audiences pour évaluer le potentiel du partenariat avant de lancer une campagne conjointe, en utilisant une estimation du chevauchement pour valider l’alignement des audiences.
- **Partage de segments coopératif de données** — Les organisations membres d’une coopérative de données partagent des segments d’audience hachés afin d’étendre la portée du ciblage tout en maintenant la conformité en matière de confidentialité et les contrôles de gouvernance des données.
- **Fédération d’audiences multi-sandbox** — Une entreprise mondiale partage des segments d’audience sur plusieurs sandbox régionaux afin de permettre un ciblage cohérent des clients sur l’ensemble des marchés tout en respectant les exigences régionales en matière de résidence des données.
- **Activation entre partenaires du programme de fidélité** — Une coalition de fidélité partage les segments de niveau de fidélité avec les commerçants participants afin que chaque partenaire puisse offrir des promotions adaptées au niveau à la base de clients partagée.
- **Collaboration en matière de mesure et d’attribution** — Un annonceur partage un segment de conversion avec un partenaire multimédia afin que ce dernier puisse mesurer l’efficacité de la campagne en comparant les utilisateurs exposés aux convertisseurs.

## Indicateurs clés de performance

Les KPI suivants permettent de mesurer le succès des implémentations de collaboration avec les audiences.

| KPI | Description | Méthode de mesure |
| --- | --- | --- |
| Taux de chevauchement des audiences | Pourcentage de profils dans le segment partagé qui correspondent entre l’expéditeur et le destinataire | [!DNL Segment Match] rapport d’estimation de chevauchement |
| Taille d’audience correspondante | Nombre de profils correspondants et disponibles pour l’activation | Statut du partage de [!DNL Segment Match] et nombre de populations de l’audience |
| Nouvelle acquisition de clients à partir des audiences correspondantes | Nouveaux clients acquis par le biais de campagnes ciblant les segments correspondants | Suivi des conversions sur les campagnes à l’aide d’audiences correspondantes |
| Réduction des coûts d&#39;acquisition client | Diminution du coût par acquisition lors de l’utilisation d’audiences appariées par rapport au ciblage large | Analyse des coûts de campagne comparant les performances des audiences appariées aux performances inégalées |
| Économies de suppression | Économie de médias grâce à la suppression des clients connus des campagnes d’acquisition | Comparaison des dépenses des médias avant et après la suppression |
| Effet élévateur des performances de Campaign | Amélioration du taux de conversion, du taux de clics publicitaires ou de l’engagement pour les campagnes utilisant des audiences correspondantes | Test A/B comparant les campagnes d’audience correspondantes au contrôle |
| Délai jusqu’à Collaboration | Temps écoulé entre le lancement du partage de segment et la préparation à l’activation | [!DNL Segment Match] la date et l’heure du workflow |

## Modèle de cas d’utilisation

Ce cas d’utilisation suit le modèle d’Audience Collaboration.

Partagez et faites correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de [!DNL Segment Match].

**Chaîne de fonctions :** sélection de segments > Configuration des correspondances > Estimation des chevauchements > Partage d’audience > Activation

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Real-Time CDP]** — Fournit la fonctionnalité [!DNL Segment Match] pour le partage d&#39;audience sécurisé par la confidentialité, l&#39;évaluation d&#39;audience pour la création de segments et l&#39;activation de destination pour l&#39;utilisation en aval des audiences correspondantes.
- **[!DNL Adobe Experience Platform]** : fournit l’infrastructure de données de base, notamment la résolution d’identité, l’unification des profils, la gouvernance des données et l’application du consentement dont [!DNL Segment Match] dépend.

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Les organisations d’expéditeur et de destinataire doivent disposer de sandbox configurés avec des rôles et des autorisations appropriés. Les utilisateurs qui gèrent les [!DNL Segment Match] doivent disposer des autorisations nécessaires pour afficher et partager des segments, configurer des connexions et gérer les flux des partenaires. Les politiques ABAC doivent être configurées pour contrôler quels utilisateurs peuvent initier et accepter des partages de segments. | [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Supposé en place | Les schémas XDM pour les profils et les événements doivent exister avec les groupes de champs requis. Les jeux de données de profil et d’événement doivent être créés et activés pour [!DNL Real-Time Customer Profile]. Le modèle de données doit prendre en charge les espaces de noms d’identité utilisés pour la correspondance de segments (généralement e-mail ou téléphone haché). | [ Présentation du système XDM ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Sources et collecte de données | Supposé en place | Les données client doivent circuler activement dans [!DNL Experience Platform] par le biais de sources de données configurées (SDK, connecteurs source, ingestion par lots). Les profils doivent être renseignés avec les types d’identité utilisés pour les [!DNL Segment Match] (e-mails hachés, par exemple). | [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configuration des identités et des profils | Obligatoire | Les espaces de noms d’identité doivent être configurés pour les identifiants utilisés dans la correspondance de segments. L’expéditeur et le destinataire doivent utiliser des espaces de noms d’identité compatibles. Les politiques de fusion doivent être configurées pour unifier correctement les profils. Des règles de liaison d’identités doivent être établies pour garantir une résolution précise des profils. | [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Définition et segmentation de l’audience | Obligatoire | Les audiences Source doivent être définies et évaluées avant de pouvoir être partagées via [!DNL Segment Match]. Les audiences doivent être créées à l’aide de [!DNL Segment Builder] ou [!DNL Audience Composition] une fois l’évaluation des lots terminée. Seules les audiences évaluées par lots sont éligibles au partage de [!DNL Segment Match]. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que la valeur d’achat de durée de vie, le score d’engagement ou l’affinité du produit peuvent créer des segments plus précis à partager. Des segments d’entrée de meilleure qualité conduisent à une collaboration d’audience plus précieuse. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Les politiques de consentement et de conservation des données garantissent que les segments partagés respectent les réglementations de confidentialité. Les politiques d’expiration des jeux de données permettent de gérer le cycle de vie des données d’audience reçues. L’application du consentement empêche le partage des profils qui se sont désinscrits. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Inclus | Les politiques de gouvernance des données doivent être évaluées avant de partager des segments pour garantir leur conformité. Les libellés des champs d’identité et des attributs de profil déterminent ce qui peut être partagé. L’application de la gouvernance empêche l’inclusion de données non autorisées dans les partages de segment. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | La surveillance du processus de partage de [!DNL Segment Match], des tâches d’estimation de chevauchement et des flux de données d’activation permet de détecter rapidement les échecs. Les alertes peuvent être configurées pour les échecs de partage ou les taux de correspondance inattendus. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Recommandé | La mesure des performances des campagnes qui utilisent des audiences correspondantes valide la valeur de la collaboration. [!DNL Customer Journey Analytics] l’analyse peut comparer les performances des campagnes d’audience correspondantes aux populations témoins. | Présentation de [CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Real-Time CDP]

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 1 : sélection et préparation du segment | Évaluez l’appartenance à un segment à l’aide de l’évaluation par lots pour générer les audiences qui seront partagées via [!DNL Segment Match] |
| Composition de l’audience | Phase 1 : sélection et préparation du segment | Vous pouvez éventuellement composer des audiences dérivées (classer, fractionner, exclure, enrichir) pour créer des segments plus ciblés à partager |
| Application du consentement et de la gouvernance | Phase 2 : correspondance entre configuration et gouvernance | Appliquez les politiques d’utilisation des données et les préférences de consentement avant de partager des segments pour garantir la conformité |
| Activation d’audience | Phase 5 : Audience Activation correspondant | Publier les audiences correspondantes reçues par le biais de [!DNL Segment Match] vers des destinations externes à des fins de ciblage ou de suppression |
| Configuration de la destination | Phase 5 : Audience Activation correspondant | Configurer des connexions à des destinations externes où les audiences correspondantes seront activées |

## Conditions préalables

- Les organisations d’expéditeur et de destinataire ont [!DNL Real-Time CDP] configurées avec des droits [!DNL Segment Match]
- [!DNL Segment Match] est activé pour les organisations ou les sandbox participant à la collaboration
- Une connexion de partenaire a été établie entre les organisations d’expéditeur et de destinataire dans l’interface utilisateur de [!DNL Segment Match]
- Les deux organisations utilisent des espaces de noms d’identité compatibles (par exemple, ont configuré les e-mails hachés)
- Les audiences Source ont été définies et évaluées avec des populations différentes de zéro
- Les politiques de gouvernance des données sont configurées et les libellés d’utilisation des données sont appliqués aux jeux de données et aux champs pertinents
- Les utilisateurs des deux côtés disposent des autorisations nécessaires pour gérer les connexions, partages et flux [!DNL Segment Match]
- Les champs de consentement sont renseignés sur les profils pour activer le filtrage basé sur le consentement avant partage

## Options de mise en œuvre

Les options suivantes décrivent différentes approches pour mettre en œuvre la collaboration avec les audiences avec [!DNL Segment Match]. Sélectionnez l’option qui correspond le mieux à la structure organisationnelle et aux exigences de collaboration.

### Option A : Partage direct de segments (un à un)

Cette option est préférable pour les partenariats bilatéraux entre deux organisations spécifiques, telles qu’un annonceur et un éditeur, ou deux marques dans le cadre d’un accord de co-marketing.

**Fonctionnement :**

Dans un partage de segment direct un-à-un, l’organisation expéditrice sélectionne une ou plusieurs audiences évaluées, initie un partage avec une organisation partenaire spécifique, et le destinataire accepte le partage. L’estimation de chevauchement s’exécute automatiquement pour afficher aux deux parties le pourcentage et le volume des profils correspondants avant que le partage ne soit finalisé.

L’expéditeur définit les espaces de noms d’identité à utiliser pour la correspondance et sélectionne les segments à partager. Le destinataire examine le partage entrant, l’accepte et l’audience correspondante devient disponible dans sa liste d’audiences pour l’activation en aval. Seul le chevauchement des identités hachées est échangé : aucune donnée d’informations d’identification personnelles ou d’attributs de profil sous-jacente ne dépasse les limites organisationnelles.

Cette approche est simple et permet aux deux parties d&#39;exercer un contrôle total. L’expéditeur choisit exactement ce qu’il souhaite partager et avec qui, et le destinataire a la possibilité d’accepter ou de refuser chaque partage.

**Considérations principales :**

- Nécessite une configuration de connexion partenaire explicite entre les deux organisations
- Les deux organisations doivent convenir des espaces de noms d’identité à mettre en correspondance
- L’estimation du chevauchement offre de la transparence avant l’engagement
- Chaque partage doit être géré et surveillé individuellement

**Avantages :**

- Workflow bilatéral simple et bien compris
- Transparence complète par l’estimation du chevauchement avant partage
- Contrôle granulaire : l’expéditeur choisit exactement les segments à partager
- Confidentialité garantie : seuls les identifiants hachés sont utilisés pour la correspondance
- Le récepteur peut accepter ou refuser des actions de manière sélective

**Limitations :**

- Ne se met pas à l’échelle efficacement lors de la collaboration simultanée avec de nombreux partenaires
- Chaque partenariat nécessite une configuration et une gestion de connexion distinctes
- La configuration de partage doit être répétée pour chaque nouveau segment

**Experience League:**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Dépannage de la correspondance de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Option B : distribution de segments multi-partenaires (un-à-plusieurs)

Cette option est idéale pour les organisations qui doivent partager des segments avec plusieurs partenaires simultanément, comme un réseau de médias de détail qui partage des segments basés sur les achats avec plusieurs annonceurs de marque, ou une société holding qui distribue des segments aux marques filiales.

**Fonctionnement :**

Dans un modèle de distribution de type « un à plusieurs », l&#39;organisation expéditrice établit des connexions [!DNL Segment Match] avec plusieurs organisations partenaires et partage des segments identiques ou différents avec chacune d&#39;elles. L’expéditeur gère un portefeuille de connexions de partenaires et peut partager de manière sélective différents segments d’audience avec différents partenaires en fonction de la relation et du cas d’utilisation.

Chaque connexion de partenaire fonctionne indépendamment : l’estimation du chevauchement, l’acceptation du partage et l’activation sont gérées par partenaire. L’expéditeur peut contrôler les segments que chaque partenaire reçoit, ce qui permet des stratégies de collaboration différenciées (par exemple, les partenaires premium reçoivent des segments plus granulaires, les partenaires standard en reçoivent des plus larges).

Cette approche utilise le même mécanisme de [!DNL Segment Match] sous-jacent que l’option A, mais l’applique à grande échelle avec un cadre opérationnel pour gérer plusieurs partenariats simultanés.

**Considérations principales :**

- Nécessite des processus opérationnels robustes pour gérer plusieurs partenariats
- Les politiques de gouvernance doivent tenir compte du partage des mêmes segments avec plusieurs parties externes
- Chaque partenaire peut utiliser différents espaces de noms d’identité, ce qui nécessite une configuration flexible
- Les taux de chevauchement varient selon les partenaires et nécessitent une évaluation par partenaire

**Avantages :**

- Évolue la collaboration en matière d’audiences à travers un écosystème de partenaires
- Stratégies de partage différenciées par partenaire
- Gestion centralisée de tous les partages de segments sortants d’une organisation
- Chaque partenariat maintient une gouvernance indépendante et des contrôles du consentement

**Limitations :**

- La complexité opérationnelle augmente avec chaque partenaire supplémentaire
- La surveillance et le dépannage doivent être effectués par partenaire
- Révision de la gouvernance requise pour chaque nouvelle connexion de partenaire
- Les partenaires ne voient pas les données des uns et des autres ni l’état de partage

**Experience League:**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Option C : fédération d’audiences entre sandbox

Cette option est idéale pour les grandes entreprises disposant de plusieurs sandbox [!DNL Experience Platform] (par exemple, des sandbox régionaux, des sandbox spécifiques à une marque ou des sandbox spécifiques à un environnement) qui doivent partager des segments d’audience entre des frontières internes sans déplacer les données brutes.

**Fonctionnement :**

Plutôt que de partager des audiences entre des organisations distinctes, la fédération d’audiences entre sandbox utilise des [!DNL Segment Match] pour partager des segments d’audience entre les sandbox d’une même organisation. Cela permet à une équipe marketing mondiale de créer un segment dans un sandbox central et de le partager avec des sandbox régionaux, ou permet à des sandbox spécifiques à une marque de partager des listes de suppression entre elles.

Le workflow reflète le partage de segment direct (option A), mais fonctionne dans les limites de l’organisation. Les connexions entre sandbox sont établies par le biais de [!DNL Segment Match] et les segments sont partagés à l’aide du même processus de correspondance sécurisé par la confidentialité. Le sandbox de réception obtient l’audience correspondante en tant que nouvelle audience pouvant être activée via ses propres destinations configurées localement.

Cette approche est particulièrement utile lorsque les exigences en matière de résidence des données empêchent le déplacement des données client brutes entre les régions, mais que la collaboration au niveau de l’audience est autorisée.

**Considérations principales :**

- Nécessite [!DNL Segment Match] droit qui prend en charge le partage entre sandbox
- Les espaces de noms d’identité doivent être cohérents entre les sandbox
- Les politiques de fusion dans chaque sandbox peuvent résoudre les profils différemment, ce qui peut affecter les taux de correspondance
- Les politiques de gouvernance s’appliquent indépendamment par sandbox

**Avantages :**

- Permet la collaboration avec les audiences sans déplacer les données brutes entre les limites du sandbox
- Prend en charge les exigences de résidence des données et de conformité régionale
- Exploite l’infrastructure d’identité organisationnelle existante
- Révision de la gouvernance plus simple, car le partage a lieu au sein de la même organisation.

**Limitations :**

- Nécessite une configuration cohérente des espaces de noms d’identité dans les sandbox
- Les taux de correspondance dépendent de la cohérence de la politique de fusion entre les sandbox
- Ne répond pas aux besoins de collaboration interorganisationnelle
- Il peut être nécessaire d’utiliser l’outil Sandbox pour synchroniser le schéma et la configuration

**Experience League:**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : Partage Direct De Segments | Option B : Distribution Multi-Partenaires | Option C : Fédération Entre Sandbox |
| --- | --- | --- | --- |
| Idéal pour | Partenariats bilatéraux | Collaboration à l’échelle des écosystèmes | Partage interne entre sandbox |
| Complexité | Faible | Élevée | Moyenne |
| Nombre de partenaires | 1 | Plusieurs | Sandbox internes |
| Frais généraux de gouvernance | Faible | Élevée (évaluation par partenaire) | Medium (dans l’organisation) |
| Gestion opérationnelle | Simple | Nécessite un framework de gestion des partenaires | Modéré |
| Prise en charge de la résidence des données | NR | Dépend de la localisation du partenaire | Fort |
| Requiert | Configuration de la connexion des partenaires | Connexions de plusieurs partenaires | [!DNL Segment Match] entre sandbox |

### Choisir la bonne option

Utilisez les conseils de décision suivants pour sélectionner l’approche d’implémentation appropriée :

1. **Collaborez-vous avec une organisation externe ou au sein de votre propre organisation ?**
   - Organisation externe : passer à la question 2.
   - Au sein de votre propre organisation (entre sandbox) : choisissez **Option C** (Fédération entre sandbox).

2. **Avec combien de partenaires externes allez-vous collaborer ?**
   - Un partenaire : choisissez **Option A** (partage direct de segments).
   - Partenaires multiples : choisissez **Option B** (Distribution multi-partenaires).

3. **Avez-vous des contraintes de résidence des données qui empêchent le déplacement des données brutes entre les régions ?**
   - Oui : choisissez l’option **Option C** que les partenaires soient internes ou externes ; utilisez le partage entre sandbox pour conserver la localisation des données.

## Phases de mise en œuvre

Les phases suivantes décrivent le processus de mise en œuvre de bout en bout de la collaboration des audiences avec [!DNL Segment Match].

### Phase 1 : sélection et préparation des segments

**Fonction d’application :** [!DNL Real-Time CDP] : évaluation de l’audience, [!DNL Real-Time CDP] : composition de l’audience

Cette phase implique de définir et d’évaluer les segments d’audience qui seront partagés via [!DNL Segment Match]. Les segments sources doivent être entièrement évalués avec des populations non nulles avant de pouvoir être sélectionnés pour le partage. Cette phase couvre également la composition facultative de l’audience pour affiner les segments avant le partage.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : approche de la définition de l’audience**
>
>Comment les audiences sources à partager doivent-elles être créées ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Créateur de segments (règles de segment) | Définitions d’audience standard basées sur les attributs de profil, les événements ou l’appartenance à un segment | Prend en charge l’évaluation par lots, en flux continu et Edge ; plus flexible pour la définition de critères |
>| Composition de l’audience | Audiences dérivées nécessitant des opérations de classement, de partage, d’exclusion ou d’enrichissement sur des segments existants | Ne prend en charge que l’évaluation par lots ; limité à 10 zones de travail de composition par sandbox |
>| Composition d’audience fédérée | Audiences créées à partir de requêtes d’entrepôt de données externe sans ingérer de données dans [!DNL Experience Platform] | Exige un droit de [!DNL Federated Audience Composition] ; les données restent dans l&#39;entrepôt |

>[!NOTE]
>
>**Décision : méthode d’évaluation de l’audience**
>
>[!DNL Segment Match] requiert des audiences évaluées par lots. Comment l’évaluation doit-elle être planifiée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Lot planifié (quotidien) | Cas d’utilisation standard où l’actualisation quotidienne de l’audience est suffisante | Calendrier d’évaluation par défaut ; plus simple à gérer |
>| Lot à la demande | Le partage ad hoc a besoin d’un emplacement où vous souhaitez partager immédiatement l’audience la plus récente | Nécessite un déclenchement manuel ; utile pour les collaborations sensibles au temps |
>| Planning personnalisé | Exigences de calendrier spécifiques alignées sur les fenêtres d’activation des partenaires | Configurer un planning cron personnalisé, plus complexe mais précis |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle (par [!DNL Segment Builder]) ou Composer l’audience (par [!DNL Audience Composition])

**Détails de configuration clés :**

- Définissez des critères d’audience à l’aide des attributs de profil, des événements comportementaux et/ou de l’appartenance à un segment
- Assurez-vous que l’audience utilise une politique de fusion compatible avec les espaces de noms d’identité utilisés pour [!DNL Segment Match]
- Vérifiez que la population de l’audience n’est pas nulle après l’évaluation.
- Appliquez des règles de suppression pour exclure les profils qui ne doivent pas être partagés (par exemple, les profils qui se sont opposés au partage des données)

**Là où les options divergent :**

**Pour L’Option A (Partage De Segment Direct) :**
Préparez les segments spécifiques que vous avez l’intention de partager avec votre partenaire unique. Privilégiez la qualité plutôt que la quantité : organisez des segments qui apportent une valeur incontestable au partenariat.

**Pour L’Option B (Distribution Multi-Partenaires) :**
Préparez un portfolio de segments pouvant être partagé avec différents partenaires. Pensez à créer des segments spécifiques aux partenaires si différents partenaires ont besoin de définitions d’audience différentes. Utilisez des conventions de nommage cohérentes pour gérer les segments dans les partenariats.

**Pour L’Option C (Fédération Entre Sandbox) :**
Assurez-vous que les audiences sources dans le sandbox d’envoi utilisent des espaces de noms d’identité qui existent dans le sandbox de réception. Vérifiez que les politiques de fusion sont alignées sur les sandbox.

**Documentation Experience League :**

- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Méthodes d’évaluation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2 : configuration de la correspondance et de la gouvernance

**Fonction d’application :** [!DNL Real-Time CDP] : application du consentement et de la gouvernance

Cette phase établit la connexion [!DNL Segment Match] entre les organisations ou les sandbox, configure les espaces de noms d’identité utilisés pour la correspondance et s’assure que les politiques de gouvernance des données permettent le partage. L’application de la gouvernance agit comme un point de contrôle de politique qui doit être effacé avant le partage des données de segment.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : espace de noms d’identité pour la correspondance**
>
>Quel espace de noms d’identité sera utilisé pour faire correspondre les profils entre l’expéditeur et le destinataire ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| E-mail haché (SHA-256) | Les deux organisations collectent des adresses e-mail et peuvent les hacher de manière cohérente | Clé de correspondance la plus courante : taux de correspondance élevé pour les cas d’utilisation des clients. Les deux parties doivent utiliser le même algorithme de hachage. |
>| Numéro de téléphone haché | L’adresse électronique n’est pas disponible de manière cohérente, mais les numéros de téléphone le sont | Couverture inférieure aux e-mails sur de nombreux marchés ; utile pour les audiences qui privilégient les appareils mobiles |
>| Espace de noms personnalisé (par exemple, identifiant de fidélité haché) | Les organisations partagent un ID de programme de fidélité ou d’abonnement commun | Taux de correspondance les plus élevés pour les bases de clients partagées connues ; nécessite une infrastructure d’ID partagés préexistante |
>| Plusieurs espaces de noms | L’optimisation du taux de correspondance est essentielle et les deux organisations disposent de plusieurs identifiants cohérents | Augmente les taux de correspondance mais ajoute de la complexité ; chaque espace de noms doit être configuré indépendamment |

>[!NOTE]
>
>**Décision : examen de la gouvernance des données**
>
>Quels contrôles de gouvernance doivent être effectués avant le partage ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Évaluation de la gouvernance standard | Cas d’utilisation standard avec des libellés et des politiques d’utilisation des données standard | Évaluez l’action marketing « Exporter vers un tiers » par rapport aux libellés du jeu de données ; résolvez les violations avant de la partager |
>| Gouvernance améliorée avec le filtrage du consentement | Partage avec des partenaires externes où le consentement doit être explicitement vérifié | Ajouter le filtrage basé sur le consentement pour exclure les profils sans partager le consentement (par exemple, consentements.share.val = &#39;n&#39;) ; plus strict mais plus sûr |
>| Révision de la gouvernance interne | Partage entre sandbox au sein de la même organisation | Des exigences de gouvernance plus légères puisque les données restent dans les limites de l’organisation ; vérifiez toujours les libellés d’utilisation des données |

**Navigation dans l’interface utilisateur :** Client > Audiences > Correspondance de segments > Connexions de partenaires

**Détails de configuration clés :**

- Établir une connexion de partenaire en échangeant des identifiants de connexion entre les organisations d&#39;expéditeur et de destinataire
- Configurez les espaces de noms d’identité qui seront utilisés pour la correspondance des deux côtés
- Exécutez l’évaluation de la politique de gouvernance des données par rapport à l’action marketing associée au partage de segments
- Vérifiez que les champs de consentement sont renseignés sur les profils et que les profils sans partage de consentement sont exclus
- Consultez les libellés d’utilisation des données sur les jeux de données et les champs de schéma inclus dans le partage

**Là où les options divergent :**

**Pour L’Option A (Partage De Segment Direct) :**
Établir une connexion de partenaire unique. Configurez des espaces de noms d’identité avec votre partenaire spécifique. L&#39;examen de la gouvernance est axé sur la relation bilatérale.

**Pour L’Option B (Distribution Multi-Partenaires) :**
Établir et gérer plusieurs connexions de partenaires. Chaque partenaire peut nécessiter un examen distinct de la gouvernance. Documentez l’approbation de la gouvernance pour chaque partenariat. Envisagez de créer une liste de contrôle de gouvernance pour rationaliser l’intégration des partenaires.

**Pour L’Option C (Fédération Entre Sandbox) :**
Établissez des connexions sandbox à sandbox au sein de l’organisation. La gouvernance est généralement plus simple, car le partage se produit en interne. Assurez-vous que les espaces de noms d’identité sont cohérents entre les sandbox.

**Documentation Experience League :**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Application des politiques](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### Phase 3 : chevauchement des estimations

**Fonction d’application :** [!DNL Real-Time CDP] : évaluation de l’audience (pour estimer le chevauchement)

Cette phase exécute l’estimation du chevauchement entre les segments de l’expéditeur et la base de profils du destinataire. L’estimation du chevauchement fournit aux deux parties le volume et le pourcentage de correspondance attendus avant de s’engager à partager l’intégralité du segment, ce qui permet de prendre des décisions éclairées sur la valeur de la collaboration.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : seuil de chevauchement pour la poursuite**
>
>Quel est le taux de chevauchement minimal qui justifie la poursuite de la part de segment complète ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Pas de seuil minimum | Partenariats exploratoires ou lorsqu’un chevauchement apporte une valeur ajoutée | Convient aux collaborations initiales où vous testez la relation |
>| Seuil bas (1-5%) | Collaboration à grande échelle avec les audiences où même un petit chevauchement représente un volume important | Fréquent pour les relations éditeur-annonceur avec une large base d’audiences |
>| Seuil Medium (5-20%) | Partenariats types pour lesquels un chevauchement significatif est attendu | Typique pour les collaborations de co-marketing ou de même secteur |
>| Seuil élevé (20 %+) | Partenariats pour lesquels une forte harmonisation des audiences est une condition préalable | Commun pour les coalitions de fidélité ou les partenariats de marque étroitement intégrés |

**Navigation dans l’interface utilisateur :** Client > Audiences > Correspondance des segments > Partages > Chevauchement des estimations

**Détails de configuration clés :**

- Sélectionner les segments à inclure dans l’estimation du chevauchement
- Examinez le rapport de chevauchement affichant le nombre et le pourcentage de profils correspondants
- Partagez les résultats de l’estimation du chevauchement avec les parties prenantes des deux côtés pour approbation
- Documentez les mesures de chevauchement comme référence pour mesurer l’efficacité de la collaboration
- Si le chevauchement est inférieur au seuil acceptable, pensez à ajuster les définitions de segment ou la configuration de correspondance d’identités avant de continuer

**Documentation Experience League :**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Phase 4 : partage des audiences

**Fonction d’application :** [!DNL Real-Time CDP] : évaluation d’audience (pour l’exécution de partage)

Cette phase exécute le partage de segment réel de l’expéditeur au destinataire. L’expéditeur lance le partage pour les segments sélectionnés et le destinataire accepte le partage entrant. Une fois acceptée, l’audience correspondante apparaît dans la liste des audiences du destinataire en tant que nouvelle audience disponible pour l’activation en aval.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : Partager la direction**
>
>Quel est le modèle de partage pour cette collaboration ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Partage unidirectionnel (expéditeur/destinataire) | Partenariat asymétrique dans lequel une seule partie fournit des données d’audience | Modèle le plus simple ; l’expéditeur partage, le destinataire active ; courant dans les relations annonceur-éditeur |
>| Partage bidirectionnel | Les deux parties bénéficient du partage d’audiences | Les deux organisations agissent simultanément en tant qu&#39;expéditeur et destinataire ; requiert deux configurations de partage ; commun dans les partenariats de co-marketing |

>[!NOTE]
>
>**Décision : partage du rythme d’actualisation**
>
>À quelle fréquence l’audience partagée doit-elle être actualisée avec l’appartenance au segment mise à jour ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Partage unique | Tester la collaboration ou pour une campagne spécifique avec une audience fixe | Plus simple : pas de maintenance continue ; l’audience devient obsolète au fil du temps |
>| Partage récurrent (aligné avec l’évaluation par lots) | Partenariats permanents où l&#39;audience change et doit être tenue à jour | Nécessite la surveillance de l’état d’actualisation ; plus courant pour les collaborations de production |

**Navigation dans l’interface utilisateur :** Client > Audiences > Correspondance de segments > Partages > Créer un partage (expéditeur) ou Accepter le partage (destinataire)

**Détails de configuration clés :**

- L’expéditeur sélectionne les segments à partager et lance le partage avec le partenaire configuré
- Le destinataire examine les détails du partage entrant (noms de segment, taille estimée, espaces de noms d’identité utilisés)
- Le destinataire accepte le partage pour créer l’audience correspondante dans son sandbox
- Vérifiez que l’audience correspondante apparaît dans la liste des audiences du destinataire avec la population attendue
- Vérifiez que l’audience correspondante est correctement étiquetée pour le suivi de la gouvernance

**Là où les options divergent :**

**Pour L’Option A (Partage De Segment Direct) :**
Exécutez un seul partage avec votre partenaire. Surveillez le statut du partage et vérifiez l’audience correspondante côté récepteur.

**Pour L’Option B (Distribution Multi-Partenaires) :**
Exécuter des partages pour chaque partenaire indépendamment. Suivre le statut des partages dans tous les partenariats. Envisagez d’échelonner le lancement du partage pour gérer la charge de traitement.

**Pour L’Option C (Fédération Entre Sandbox) :**
Exécutez le partage entre sandbox. L’audience correspondante apparaît dans la liste des audiences du sandbox de réception. Vérifiez que le sandbox de réception dispose des configurations de destination nécessaires pour l’activation en aval.

**Documentation Experience League :**

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Dépannage de la correspondance de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Phase 5 : activation des audiences correspondantes

**Fonction d’application :** [!DNL Real-Time CDP]: Configuration de destination, [!DNL Real-Time CDP]: Audience Activation

Cette phase active l’audience correspondante (côté récepteur) vers des destinations externes pour le ciblage, la suppression ou une utilisation en aval. L’audience correspondante est traitée comme toute autre audience dans le sandbox du destinataire et peut être activée via le workflow d’activation de destination standard.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : type de destination pour l’audience correspondante**
>
>Où l’audience correspondante doit-elle être activée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Destinations Advertising (Google, Meta, Trade Desk) | Utilisation des audiences correspondantes pour le ciblage ou la suppression des publicités | Nécessite une connexion et une authentification de destination ; soumis à des limites de débit et des exigences de format spécifiques à la destination |
>| Destinations de stockage dans le cloud (S3, Azure, GCS) | Exportation des audiences correspondantes sous forme de fichiers à utiliser dans des systèmes externes | Prend en charge la personnalisation du format de fichier ; planning d’exportation par lots requis ; flexible pour le traitement en aval |
>| Destinations d’automatisation du CRM/marketing | Enrichir les enregistrements CRM ou déclencher des workflows marketing automatisés avec des données d&#39;audience correspondantes | Nécessite un mappage des champs au schéma CRM ; utile pour l’alignement ventes-marketing. |
>| Destinations Personalization (web, application) | Utilisation de l’appartenance à une audience correspondante pour la personnalisation sur site | Nécessite une évaluation Edge de l’audience correspondante ou de l’activation de diffusion en continu ; la latence varie selon la destination |

>[!NOTE]
>
>**Décision : planning d’activation**
>
>À quelle fréquence l’audience correspondante doit-elle être exportée vers la destination ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Exportation incrémentielle quotidienne | Activation standard avec mises à jour régulières de l’audience | Exporte uniquement les profils modifiés ; volume de données inférieur ; plus courant pour les campagnes en cours |
>| Exportation complète quotidienne | Destinations qui nécessitent un fichier d’audience complet à chaque fois | Volume de données plus élevé ; garantit que la destination a un état d’audience complet ; certaines destinations nécessitent des exportations complètes. |
>| Activation à la demande | Lancements de campagne ad hoc ou activations sensibles au facteur temps | Déclencheur manuel ; contourne la cadence planifiée ; disponible uniquement pour les destinations par lots |

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Catalogue (pour la configuration de la destination) ou Parcourir > Sélectionner la destination > Activer les audiences (pour l’activation)

**Détails de configuration clés :**

- Configurer la connexion de destination avec les informations d’authentification appropriées
- Mappez les attributs de profil de l’audience mappée aux champs de destination (champs d’identité, attributs de profil, appartenance à un segment).
- Configurer le planning d’exportation (incrémentiel ou complet, quotidien ou personnalisé)
- Surveillez le flux de données d’activation pour vérifier que les profils d’audience correspondants sont exportés avec succès
- Vérifiez les mesures d’activation (profils exportés, enregistrements ayant échoué) dans la vue de surveillance de destination

**Là où les options divergent :**

**Pour L’Option A (Partage De Segment Direct) :**
Le destinataire active l’audience correspondante par le biais de son workflow de destination standard. Aucune configuration spéciale n’est nécessaire au-delà de l’activation de destination normale.

**Pour L’Option B (Distribution Multi-Partenaires) :**
Chaque organisation réceptrice active les audiences correspondantes indépendamment par le biais de ses propres destinations. L’expéditeur n’a aucune visibilité sur l’activation côté récepteur.

**Pour L’Option C (Fédération Entre Sandbox) :**
Le sandbox de réception doit avoir ses propres configurations de destination. Les destinations ne peuvent pas être partagées sur plusieurs sandbox. Assurez-vous que le sandbox de réception dispose des connexions de destination nécessaires établies.

**Documentation Experience League :**

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Considérations relatives à la mise en œuvre

Examinez les points suivants avant et pendant l’implémentation pour éviter des problèmes courants et optimiser la collaboration avec vos audiences.

### Mécanismes de sécurisation et limites

- [!DNL Segment Match] utilise des identifiants hachés pour la correspondance ; aucune PII ne dépasse les limites de l’organisation. Voir [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview).
- Seules les audiences évaluées par lots peuvent être partagées via [!DNL Segment Match]. Les segments en flux continu et évalués par Edge doivent être convertis en évaluation par lots avant partage.
- Un maximum de 4 000 définitions de segment par sandbox s’applique aux segments source et reçus. Voir [ Mécanismes de sécurisation de la segmentation ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).
- La précision de l’estimation du chevauchement dépend du volume des identifiants correspondants. Les petits publics peuvent présenter des estimations moins précises.
- Les mécanismes de sécurisation d’activation s’appliquent aux audiences correspondantes de la même manière que toute autre audience : 100 flux de données au maximum par destination. Voir [ Mécanismes de sécurisation de l’activation ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Les audiences composées sont évaluées selon un planning par lot et sont limitées à 10 zones de travail de composition par sandbox. Voir [ Mécanismes de sécurisation de la composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails).

### Pièges courants

- **Hachage d’identité incohérent entre l’expéditeur et le destinataire :** si les deux organisations hachent des adresses e-mail mais utilisent des algorithmes de hachage, des règles de normalisation ou des valeurs Sel différents, les taux de correspondance seront proches de zéro. Les deux parties doivent s’entendre sur la spécification exacte du hachage (par exemple, SHA-256 sur les e-mails tronqués en minuscules) avant d’établir la connexion.
- **Partage des audiences sans révision de la gouvernance :** le lancement d’un partage de segment sans évaluation des politiques d’utilisation des données peut entraîner des violations de conformité. Exécutez toujours l’évaluation des politiques de gouvernance par rapport à l’action marketing « Exporter vers un tiers » avant de partager des segments avec des organisations externes.
- **Taux de correspondance faible en raison d’écarts de couverture d’identité :** si l’audience de l’expéditeur est principalement identifiée par un ECID (cookie anonyme), mais que l’espace de noms correspondant est un e-mail haché, le taux de correspondance sera très faible, car les profils anonymes ne disposent pas d’adresses e-mail. Vérifiez que les audiences sources ont une couverture suffisante de l’espace de noms d’identité correspondant configuré.
- **Oublier d’accepter le partage du côté du destinataire :** l’audience partagée n’apparaît pas dans la liste des audiences du destinataire tant que le partage n’est pas explicitement accepté. Coordonnez-vous avec le destinataire pour garantir une acceptation rapide, en particulier pour les campagnes sensibles au facteur temps.
- **Audiences appariées obsolètes en raison d’un mauvais alignement du planning d’évaluation :** si l’audience source de l’expéditeur est évaluée tous les jours, mais que l’actualisation du [!DNL Segment Match] s’exécute toutes les semaines, l’audience appariée côté destinataire peut ne pas refléter la dernière adhésion. Aligner l’évaluation et partager les cadences d’actualisation.

### Bonnes pratiques

- Établissez un accord formel de partage des données entre les organisations avant de configurer [!DNL Segment Match]. Cela devrait couvrir les cas d’utilisation autorisés, les exigences de gouvernance des données, les obligations de consentement et les procédures de résiliation.
- Utilisez l’estimation de chevauchement comme outil de validation avant chaque campagne majeure : exécutez l’estimation avant de vous engager pour vous assurer que l’audience correspondante atteint les seuils de taille et de qualité minimaux.
- Appliquez des conventions de nommage descriptives aux segments partagés qui incluent le nom du partenaire, le cas d’utilisation et la date (par exemple, « PartnerX_HighValue_Suppression_2026Q1 ») pour maintenir la clarté entre les organisations.
- Surveillez les taux de correspondance au fil du temps. La diminution des taux de correspondance peut indiquer une dégradation de la couverture d’identité, des problèmes de qualité des données ou des changements dans la base de clients du partenaire.
- Segmentez les audiences sources pour exclure les profils sans l’espace de noms d’identité correspondant renseigné. Cela améliore les pourcentages de taux de correspondance et fournit des estimations de chevauchement plus précises.
- Pour les partenariats de partage bidirectionnels, désignez clairement la propriété des plannings de maintenance et d’actualisation des segments afin d’éviter toute confusion quant à l’organisation responsable des mises à jour.

### Décisions de compromis

>[!NOTE]
>
>**Compromis : taux de correspondance par rapport au contrôle de la confidentialité**
>
>L’utilisation d’espaces de noms d’identité supplémentaires (e-mail, téléphone et ID d’appareil hachés) pour la correspondance augmente les taux de correspondance, mais élargit la surface pour une éventuelle ré-identification. L’utilisation de moins d’espaces de noms (e-mail haché uniquement) offre une protection de la confidentialité plus forte, mais peut réduire la taille d’audience correspondante.
>
>- **Les espaces de noms multiples ont la préférence** taux de correspondance plus élevés, audiences correspondantes plus volumineuses, plus utiles pour le ciblage de la campagne
>- **Avantages de l’espace de noms unique :** meilleure posture de confidentialité, révision de gouvernance plus simple, moindre risque de conformité
>- **Recommandation :** commencez par un seul espace de noms (l’e-mail haché est le plus courant) et ajoutez des espaces de noms supplémentaires uniquement si les taux de correspondance sont insuffisants pour le cas d’utilisation. Documentez l’évaluation de l’impact sur la confidentialité pour chaque espace de noms ajouté.

>[!NOTE]
>
>**Compromis : granularité des segments par rapport à la simplicité d’exploitation**
>
>Le partage de nombreux segments granulaires hautement ciblés avec un partenaire offre davantage de flexibilité pour le ciblage des campagnes, mais augmente la complexité opérationnelle pour l’expéditeur et le destinataire. Le partage de segments moins nombreux et plus larges simplifie la gestion, mais réduit la précision du ciblage.
>
>- **Les segments granulaires sont privilégiés :** ciblage précis, campagnes différenciées, pertinence plus élevée.
>- **Des segments étendus sont privilégiés :** gestion simplifiée, moins de partages à surveiller, coûts d’exploitation réduits
>- **Recommandation :** Commencez par un petit nombre de segments à forte valeur ajoutée (2-5) pour un nouveau partenariat. Augmentez la granularité à mesure que le partenariat se développe et que les processus opérationnels sont établis. Utilisez les conventions de nommage et la documentation pour gérer la complexité à mesure que le nombre de segments augmente.

>[!NOTE]
>
>**Compromis : fréquence d’actualisation et coût de traitement**
>
>L’actualisation plus fréquente des audiences partagées garde l’audience correspondante à jour, mais augmente la charge de traitement et peut consommer davantage de capacité de licence. Des actualisations moins fréquentes réduisent les coûts, mais permettent à l’audience correspondante de devenir obsolète.
>
>- **Favoris des actualisations fréquentes :** appartenance actuelle à l’audience, pertinence accrue de la campagne, précision de suppression améliorée.
>- **Rafraîchissements peu fréquents :** coût de traitement réduit, surveillance simplifiée, consommation réduite de licences
>- **Recommandation** l’actualisation quotidienne est appropriée pour la plupart des collaborations en production. Pour les cas d’utilisation urgents (par exemple, ventes flash, campagnes basées sur un événement), envisagez une réévaluation et un partage à la demande immédiatement avant le lancement de la campagne.

## Documentation connexe

Les ressources suivantes fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

### [!DNL Segment Match]

- [Présentation de la Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Dépannage de la correspondance de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentation et audiences

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identité et profil

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Gouvernance des données et consentement

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Application des politiques](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### Destinations et activation

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### Modélisation des données et schéma

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Administration et contrôle d’accès

- [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Surveillance et observabilité

- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Garde-fous

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Tutoriels

- [Créer un schéma](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Activer un jeu de données pour Profil](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
