---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 7%

---
# Audit de plan directeur et recommandations

La présente vérification applique la [grille d&#39;évaluation](rubric.md) à tous les documents
la section « Schémas et plans directeurs de l’architecture » du [TOC.md](../help/blueprints/TOC.md) (lignes 76 à 133), et
recommande si chaque plan directeur doit devenir un cas d’utilisation **motif**, une architecture
**Diagramme**, les deux (**Fractionner**), ou être marqué comme **Dupliquer** d’un modèle existant.

Il s’agit d’un audit uniquement ; aucun contenu n’a été déplacé. La liste d’attente de migration (actions A-D par lots)
sera rédigé comme un plan de suivi distinct une fois que les recommandations auront été examinées.

## Résumé

**Nombre total de documents contrôlés :** 43

| Recommandation | Nombre | Action |
| --- | --- | --- |
| Modèle | 8 | Créer un nouveau modèle de cas d’utilisation ; rogner l’original sur un diagramme. |
| Dupliquer | 9 | Le modèle existant couvre toute la portée. Simplifiez le plan directeur en un diagramme et un lien croisé. |
| Partage | 2 | Extraire le contenu du modèle ; réduire l’original à un diagramme ; relier les deux. |
| Diagramme | 16 | Conserver en tant que diagramme d’architecture ; supprimer la narration si nécessaire. |
| Navigation | 8 | Page de destination de la section (overview.md ou links-only) ; à revoir après l’arrivée des migrations. |

### Étalonnage des témoins

Les 6 fichiers `experience-platform/` notés Modèle=0, Diagramme=3 → unanimement **Diagramme**.
La rubrique est calibrée ; les résultats des autres sous-domaines peuvent être considérés comme fiables.

### Nouvelle catégorie de modèle de cas d’utilisation : Activation et marketing B2B

Une nouvelle `use-case-patterns/b2b/` de catégorie (libellé d’affichage **Activation et marketing B2B**, ancre de table des matières)
La `{#b2b-patterns}` proposée) hébergera tous les modèles spécifiques au B2B. Le libellé reflète le existant
la sous-section « Activation et marketing B2B » dans la zone des diagrammes d’architecture de [TOC.md](../help/blueprints/TOC.md),
donnant aux lecteurs une symétrie visuelle entre les deux sections.

Lorsqu’elle est entièrement remplie, la catégorie contient des modèles **7** :

| Origine | Action | Chemin cible |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **Déplacer** modèle existant | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **Déplacer** modèle existant | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **Déplacer** modèle existant | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **Auteur nouveau** (ligne Modèle d’audit) | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **Auteur nouveau** (ligne Modèle d’audit) | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **Nouvel auteur** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **Nouvel auteur** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **État de transition initial — point de contrôle de coordination du rédacteur.** L’« activation et le marketing B2B » existants> la sous-section dans la zone architecture-diagrammes de [TOC.md](../help/blueprints/TOC.md) (lignes 95 à 106) **reste intacte> pendant la transition**. Chaque conversion de plan directeur et déplacement de modèle existant requiert> approbation du rédacteur propriétaire avant la migration du contenu. Le nouveau modèle de cas d’utilisation `b2b/`> coexiste avec la section de plan directeur existante lorsque la migration s’effectue page par page, avec> des liens croisés entre eux.

Lorsque les relocalisations et les nouveaux schémas ont tous atterri :

- [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns` section gagnera un `B2B Activation & Marketing{#b2b-patterns}`
(emplacement à déterminer avec le rédacteur).
- [&#128279;](../help/blueprints/use-case-patterns/overview.md) recevra une table de catégorie B2B.
- Les modèles déplacés seront supprimés de `audience-building-activation`,
  `campaign-management-orchestration` et `analysis` tableaux de présentation ; leurs anciennes URL sont conservées
actif via les redirections dans [migration-redirections.csv](migration-redirects.csv).

### Doublons identifiés (9)

La portée du plan directeur est déjà couverte par un modèle de cas d’utilisation existant. L’action de migration est
**simplifiez le diagramme d’architecture + la liaison croisée**.

| Plan directeur | Modèle existant |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> Remarque : `decision-management-edge.md` et `decision-management-hub.md` correspondent tous deux au même> modèle de `offer-decisioning.md` existant. Envisagez de consolider les deux plans directeurs en un seul.> diagramme d’options de déploiement ou ajout du modèle existant avec le déploiement edge-vs-hub> variantes. Indicateur pour la révision du rédacteur.

### Modèles à créer (8 nouveaux + 2 à partir de Fractionnements = 10 au total)

| Plan directeur de Source | Catégorie proposée | Titre du modèle proposé |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | Recherche de profil en temps réel pour l’assistance et les ventes |
| `audience-activation/data-science.md` | audience-building-activation | Ingestion de modèles de science des données pour l’enrichissement des profils |
| `audience-activation/real-time-lookup.md` | personnalisation | Accès au profil Edge pour Web/Mobile Personalization |
| `b2b/b2b-journeys-with-marketo.md` | **b2b** (nouveau) | Parcours de compte B2B avec intégration de données Marketo |
| `b2b/ajo-b2b-paid-media-controller.md` | **b2b** (nouveau) | Orchestration de médias payants B2B via une logique de partage de cascade |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **b2b** (nouveau) | Réception des demandes de campagne et création automatisée de programmes |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **b2b** (nouveau) | Workflow De Révision Et D’Approbation Des Ressources De Campagne |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Orchestration par lots et messagerie transactionnelle de Campaign v8 |
| `audience-activation/rtcdp-target.md` *(Split)* | personnalisation | Partage d’audiences en temps réel avec Adobe Target |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *(Split)* | campaign-management-orchestration | Intégration de la messagerie tierce à Journey Optimizer |

### Nouvelle catégorie de modèle proposée

- **`b2b/`** (libellé d’affichage **Activation et marketing B2B**) : consultez la section dédiée ci-dessus. Le
Les modèles Marketo + Workfront (`intake-and-create`, `review-and-approve-blueprint`) sont acheminés.
ici plutôt que dans une catégorie `marketing-resource-management` distincte, puisqu’ils représentent
Opérations marketing B2B en pratique. La nouvelle catégorie regroupe 7 modèles au total : 3 déplacés
à partir de catégories existantes et de 4 plans directeurs nouvellement créés.

### Redirections de la migration

Chaque modification d’URL introduite par cette migration ajoute une ligne au canonique
[`redirects.csv`](../redirects.csv) à la racine du référentiel (format : `source,dest`). Confirmé
les redirections sont évaluées dans [migration-redirections.csv](migration-redirects.csv) et fusionnées dans
fichier canonique lorsque chaque déplacement correspondant se produit.

**Confirmé (3 entrées, en cours d’évaluation) :** déplacement de modèles existants vers `b2b/`. Voir
[migration-redirections.csv](migration-redirects.csv).

**En attente — ajouté lorsqu’un plan directeur est *supprimé* (et non lorsqu’il est réduit à un diagramme) :** si un
Le plan directeur de la ligne Motif, Fractionner ou Dupliquer est ensuite entièrement supprimé. Ajoutez une redirection à partir du .
URL de plan directeur vers l’URL de modèle canonique. Approche de migration par défaut (simplification du diagramme)
maintient l’URL du plan directeur active et **ne nécessite pas** ces redirections. Répertoriés ci-dessous pour
exhaustivité si un plan directeur est complètement retiré :

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

Lors de la conversion de l’une des lignes ci-dessus en lignes de redirection actives, mettez en forme en séparant les lignes par des virgules `source,dest`
avec des chemins d’accès `/en/docs/...` complets (pas de suffixe `.html`), correspondant au modèle existant dans ;
[`redirects.csv`](../redirects.csv).

### Politique de création de redirection (règle durable)

Pour chaque étape de migration, suivez ces règles :

1. **Fichier déplacé ou renommé** → ajouter une redirection depuis l’ancienne URL vers la nouvelle URL.
2. **Fichier supprimé** (plan directeur remplacé, aucun diagramme conservé) → ajouter la redirection depuis l’URL supprimée vers
URL de remplacement canonique.
3. **Fichier simplifié en place** (URL inchangée) → aucune redirection.
4. **l’ancre de table des matières renommée** (par exemple, modification de l’en-tête de section) → ajouter des redirections pour chaque page sous
cette ancre, puisque l’URL change.

### Questions ouvertes pour le rédacteur

1. **Edge de gestion des décisions ou hub** : les deux correspondent au même existant. `offer-decisioning.md`
motif. Consolidez en un seul diagramme avec des variantes de déploiement ou traitez-les comme des diagrammes distincts.
les diagrammes qui se rejoignent tous les deux sur le même motif ?
2. **Journey Optimizer parcours ou messagerie déclenchée par un événement** — l&#39;agent a marqué ce duplicata
classification comme incertaine. Vérifiez l’alignement de la portée avant de réduire le plan directeur.
3. **`customer-journey-analytics/analysis.md`** — le contenu concerne en fait Experience Platform
Query Service et non CJA. Envisagez de déplacer vers `experience-platform/` dossier . (Une redirection
serait ajoutée si tel est le cas ; voir [migration-redirections.csv](migration-redirects.csv).)
4. **Campaign v7 (obsolète)** — trois fichiers v7 obsolètes ont été classés comme Diagramme /
Navigation. Confirmez s’il faut migrer, laisser en l’état ou supprimer entièrement de la table des matières.
5. **`customer-success-stories.md`** — page de référence liens uniquement (non `overview.md`).
Classé en tant que navigation. Confirmer ou reclasser.
6. **ancre de table des matières de la section B2B** — `{#b2b-patterns}` proposée. Autres modèles utilisés par les sous-sections
   `-patterns` le suffixe (`{#personalization-patterns}`, `{#analysis-patterns}`,
   `{#campaign-orchestration-patterns}`). Confirmez ou sélectionnez une autre ancre avant la création de redirections.
7. **Placement de la section B2B dans la table des matières** — proposé sous `+ Use Case Patterns{#use-case-patterns}`.
Ordre parmi les frères (création et activation d’audience, Personalization, gestion de campagne)
&amp; Orchestration, Analysis, B2B Activation &amp; Marketing, Conversational Experience) est le
appel de l&#39;écrivain.
8. **Coordination propriétaire-rédacteur** - chaque conversion de plan directeur et chaque déplacement de modèle existant
nécessite l’approbation du rédacteur avant le déplacement du contenu. La table d’audit est l’état cible, et non un
plan de séquencement ; le séquencement s’effectue dans un plan de migration de suivi après la coordination.

## Table d&#39;audit

| chemin | titre | résumé | type_dominant | recommandation | offer_pattern_category | offer_pattern_title | offer_diagram_title | duplicate_of | pattern_score | diagram_score | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Schémas d’architecture d’Adobe Experience Cloud | Architecture d’entreprise montrant comment les applications et services Experience Cloud s’intègrent à AEP Foundation. | Diagramme | Diagramme |  |  | Présentation de l’architecture d’Experience Cloud |  | 0 | 3 | Remplacer 3 (aucun objectif commercial). Trois diagrammes complémentaires (marketing, intégration, paysage d’entreprise). Population témoin : comme prévu. |
| help/blueprints/experience-platform/platform-applications.md | Diagrammes d’architecture de Adobe Experience Platform et des applications | Diagrammes d’architecture montrant la manière dont Experience Platform est lié à d’autres applications Experience Cloud. | Diagramme | Diagramme |  |  | AEP et architecture des applications |  | 0 | 3 | Remplacer 3. Deux diagrammes de présentation/détaillés ; aucun guide d’implémentation. Liens croisés vers des documents d’apprentissage sur les intégrations. Population témoin : comme prévu. |
| help/blueprints/experience-platform/platform-data-flow.md | Diagrammes de l’architecture de flux de données Adobe Experience Platform | Diagramme d’architecture des flux de données présentant les chemins d’ingestion et de sortie dans et hors d’Experience Platform. | Diagramme | Diagramme |  |  | Architecture des flux de données AEP |  | 0 | 3 | Remplacer 3. Diagramme de flux de données unique avec référence aux documents de collecte de données. Artefact d&#39;architecture pure. Population témoin : comme prévu. |
| help/blueprints/experience-platform/guardrails.md | Experience Platform et garde-fous d’application | Contraintes système, attentes en matière de performances et mécanismes de sécurisation de la latence pour AEP et les applications. | Diagramme | Diagramme |  |  | Mécanismes de sécurisation et latences dans AEP et les applications |  | 0 | 3 | Remplacer 3. Diagramme de latence et tableaux de référence. Orienté architecte (périphérie ou hub). Documentation sur les contraintes, et non sur la procédure à suivre. Population témoin : comme prévu. |
| help/blueprints/experience-platform/deployment/websdk.md | Diagramme d’architecture d’Experience Platform Web SDK et Edge Network | Architecture de déploiement Web SDK et Edge Network présentant les flux de collecte de données. | Diagramme | Diagramme |  |  | Déploiement de Web SDK et d’Edge Network |  | 0 | 3 | Remplacer 3. Deux diagrammes (flux et séquence). Référence des tutoriels, mais pas de procédure dans le document. Centré sur l’architecte. Population témoin : comme prévu. |
| help/blueprints/experience-platform/deployment/appsdk.md | Diagramme de l’architecture de déploiement du SDK spécifique à l’application | Chemins d’intégration SDK spécifiques à une application et diagramme d’architecture de collecte de données. | Diagramme | Diagramme |  |  | Déploiement SDK spécifique à l’application |  | 0 | 3 | Remplacer 3. Diagramme de déploiement unique avec narration minimale. Artefact d&#39;architecture pure. Population témoin : comme prévu. |
| help/blueprints/audience-activation/advertising-activation.md | Audience Activation vers les destinations sociales et Advertising | Activez les audiences vers les réseaux publicitaires Facebook et Google via RTCDP avec la configuration des identités et des destinations. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | Le modèle existant couvre cette portée. Remplacement de doublon. Action : simplifier pour obtenir un diagramme et un lien croisés purs. |
| help/blueprints/audience-activation/audience-manager.md | Basé sur l’appareil - Ciblage d’audience anonyme avec Audience Manager | Activation d’audience anonyme à l’aide d’Audience Manager ou de RTCDP pour le ciblage basé sur les appareils sur plusieurs canaux. | Diagramme | Diagramme |  |  | Ciblage d’audience basé sur un appareil anonyme |  | 1 | 2 | Un récit minimal. Diagramme d’architecture présent, topologie du système affichée. Aucun cadre d’objectif commercial ; SDK de déploiement et concepts de hub/edge. |
| help/blueprints/audience-activation/customer-activity.md | Accès au profil en temps réel pour les scénarios d’assistance et de vente | Activez le contexte client en temps réel de l’assistance et des agents de vente via l’API de recherche de profil. | Modèle | Modèle | audience-building-activation | Recherche de profil en temps réel pour l’assistance et les ventes |  |  | 3 | 1 | Définit les résultats commerciaux (contexte de l’agent). Comporte une liste de contrôle des prérequis ; étapes d’implémentation > 30 lignes. Cas d’utilisation unique : accès au profil de hub (pas de personnalisation Edge). Distinct des modèles de personnalisation existants. |
| help/blueprints/audience-activation/data-science.md | Plan directeur sur la data science personnalisée pour l’enrichissement de profil | Ingérez des scores de modèle de machine learning dans RTCDP pour enrichir les profils à des fins de personnalisation et de segmentation. | Modèle | Modèle | audience-building-activation | Ingestion de modèles de science des données pour l’enrichissement des profils |  |  | 3 | 1 | Définit les résultats commerciaux (enrichissement pour la personnalisation). Comporte des cas d’utilisation et des considérations ; considérations d’implémentation > 30 lignes. Concentrez-vous sur les workflows de science des données, pas sur la messagerie/activation. |
| help/blueprints/audience-activation/enterprise-destinations.md | Activation d’audiences et de profils vers des destinations d’entreprise | Diffusez en continu ou par lots les modifications de profil et d’audience vers le stockage dans le cloud et les applications d’entreprise pour les ventes, l’assistance et les analyses. | Diagramme | Diagramme |  |  | Activation d’audiences et de profils d’entreprise |  | 1 | 2 | Aucun cadre d’objectifs commerciaux. Conseils de mise en œuvre fragmentés. Diagramme d’architecture + topologie du système pour le stockage dans le cloud/les applications d’entreprise. Visuellement dominant. |
| help/blueprints/audience-activation/real-time-lookup.md | Accès au profil Edge en temps réel pour les Personalization web et mobiles | Accédez au profil unifié Edge en millisecondes pour une personnalisation web et mobile en temps réel. | Modèle | Modèle | personnalisation | Accès au profil Edge pour Web/Mobile Personalization |  |  | 5 | 2 | Infrastructure commerciale solide (personnalisation à faible latence). Deux modèles d’implémentation (SDK web ou API Edge). Les nombreuses étapes et prérequis (>30 lignes). KPI implicites (latence, débit). |
| help/blueprints/audience-activation/rtcdp-target.md | Personalization client connu avec Target | Partagez des audiences et des profils RTCDP avec Adobe Target pour une personnalisation web et mobile des visiteurs connus. | Mixte | Partage | personnalisation | Partage d’audiences en temps réel avec Adobe Target | Architecture d’intégration de Target | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | Chevauche le modèle de visiteur connu existant, mais a une portée plus étroite (Target uniquement). Trois modèles d’intégration. Diagrammes d’architecture + déploiement Edge pris en compte. Motif contenu + diagramme substantiel → Fractionner. |
| help/blueprints/audience-activation/segment-match.md | Audience Collaboration avec correspondance de segments | Activez la collaboration sécurisée des audiences partenaires via la correspondance de segments avec des contrôles de confidentialité. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | Le modèle existant couvre exactement cela. Remplacement de doublon. Contenu unique à conserver dans le diagramme : configuration détaillée de RBAC/consentement/gouvernance et workflow de publicité programmatique. |
| help/blueprints/b2b/overview.md | Plans directeurs B2B Analytics, Activation et Marketing | Page de navigation répertoriant les plans directeurs de l’analyse B2B, de l’activation des audiences, des groupes d’achats, de Marketo et de Workfront. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : fichier nommé overview.md. Exclu de la migration. |
| help/blueprints/b2b/b2bactivation.md | Plan directeur de l’activation de profil et de l’audience B2B | Activez les audiences B2B basées sur un compte sur les canaux web, e-mail et publicitaires à l’aide des données de compte et de profil. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | Remplacer 2 : un modèle équivalent existe. Le plan directeur est un sous-ensemble plus étroit axé sur l’architecture. |
| help/blueprints/b2b/b2b-account-activation.md | Activation du compte B2B vers des destinations Advertising et des destinations de fichiers | Comptes B2B Target via des destinations LinkedIn et de stockage dans le cloud à l’aide de la création et de l’activation d’audiences de compte. | Diagramme | Diagramme |  |  | Audience Activation du compte B2B |  | 1 | 2 | Cadre commercial minimal, aucun indicateur de performance clé, narration minimale. Diagramme d’architecture présent ; topologie LinkedIn/de stockage dans le cloud décrite. Conserver sous forme de diagramme. |
| help/blueprints/b2b/b2b-buying-group-journeys.md | Plan directeur de marketing et de gestion des Parcours basé sur les groupes d’achats | Concevez des parcours de compte qui qualifient les prospects en groupes d’achat avec des rôles et des intérêts de solution définis. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | Remplacer 2 : un modèle équivalent existe. Le plan directeur comprend un contenu de modèle riche, mais le modèle existant est plus complet. |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | Parcours B2B utilisant le plan directeur des données Marketo | Déployez Journey Optimizer B2B edition avec les données Marketo pour orchestrer les parcours des groupes d’achats et l’engagement des comptes. | Modèle | Modèle | b2b | Parcours de compte B2B avec intégration de données Marketo |  |  | 4 | 1 | Un encadrement solide des affaires. KPI répertoriés ; options d’implémentation multiples ; considérations approfondies (> 30 lignes). Différencié du modèle existant par la profondeur d’intégration des données Marketo (configuration XDM, combinaison d’identités, blocage de champ). Itinéraires vers la nouvelle catégorie b2b/ . |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B - Account Journey Orchestration - Paid Media Controller | Orchestrez des campagnes média payantes B2B à l’aide de la logique de cascade pour affecter des comptes aux campagnes et activer les destinations. | Modèle | Modèle | b2b | Orchestration de médias payants B2B via une logique de partage de cascade |  |  | 4 | 2 | Un encadrement solide des affaires. KPI explicites ; options d’implémentation multiples ; conditions préalables ; narration de >30 lignes. Distinct du modèle existant de groupe d&#39;achat (se concentre sur la priorisation des médias payants, et non sur l&#39;éducation). Itinéraires vers la nouvelle catégorie b2b/ . |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Vue d’ensemble du plan directeur d’intégration de Marketo Engage et Workfront | Présentation de la planification des campagnes vers l’automatisation de l’exécution à l’aide de Marketo Engage et Workfront avec Fusion. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : fichier nommé overview.md. Exclu de la migration. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | Plan directeur d’ingestion et de création | Automatisez la réception des demandes de campagne marketing B2B jusqu’à leur création à l’aide des formulaires Workfront et du modèle de programme Marketo Engage. | Modèle | Modèle | b2b | Réception des demandes de campagne et création automatisée de programmes |  |  | 4 | 1 | Un encadrement commercial solide sur la vitesse de la campagne. KPI implicites (réduction des erreurs/reprises) ; étapes de workflow > 30 lignes ; liste de contrôle de préparation. Routes vers la nouvelle catégorie b2b/ (les opérations Marketo+Workfront sont principalement B2B). |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | Révision et approbation du plan directeur | Intégrez les workflows de vérification et d’approbation Workfront aux ressources de messagerie Marketo Engage à l’aide de l’automatisation Fusion. | Modèle | Modèle | b2b | Workflow De Révision Et D’Approbation Des Ressources De Campagne |  |  | 3 | 2 | Analyse approfondie de la conformité et de la précision ; indicateurs de performance clés implicites (vitesse d’approbation) ; narratif > 30 lignes ; section de planification des workflows. Itinéraires vers la nouvelle catégorie b2b/ . |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | Histoires de succès client | Liens vers des études de cas client et des webinaires présentant les résultats de l’intégration de Marketo et de Workfront. | Navigation | Navigation |  |  |  |  |  |  | Contenu minimal (6 hyperliens). Pas de structure d’entreprise, d’indicateurs clés de performance, d’architecture ou de narration. Traité comme navigation. Le rédacteur doit confirmer. |
| help/blueprints/customer-journey-analytics/overview.md | Plans directeurs de Customer Journey Analytics | Unifiez et analysez les données et le comportement des clients à partir de divers canaux pour créer des vues basées sur le parcours. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : overview.md. Page de destination de style table des matières. Exclu de la migration. |
| help/blueprints/customer-journey-analytics/b2b-cja.md | Plan directeur B2B Customer Journey Analytics | Rapports et analyses CJA basés sur les comptes pour les organisations B2B utilisant le compte comme modèle de données principal. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | Remplacement 2 : le modèle équivalent couvre l’analyse au niveau du compte B2B avec CJA B2B edition. Action : simplifier en diagramme, relier. |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | Plan directeur de Customer Journey Analytics avec Real-time Customer Data Platform | Créez et publiez des audiences de CJA vers RTCDP à des fins de ciblage et de personnalisation. | Diagramme | Diagramme |  |  | Intégration de la publication d’audiences CJA à RTCDP |  | 1 | 3 | Forte concentration sur l’architecture (intégration système à système, forme du déploiement). Un récit minimal. Contenu unique : mécanismes de sécurisation de la latence de publication des audiences CJA. |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Plan directeur de Customer Journey Analytics avec Journey Optimizer | Analysez les données de diffusion et d’interaction d’AJO dans CJA ; publiez les audiences CJA dans AJO. | Diagramme | Diagramme |  |  | Intégration et analyse CJA-vers-AJO |  | 1 | 3 | Forte concentration sur l’architecture. Un récit minimal. Contenu unique : modèle bidirectionnel de partage de données CJA-AJO. |
| help/blueprints/customer-journey-analytics/analysis.md | Plan directeur pour l’analyse des données et la Data Intelligence | Utilisez Experience Platform Query Service pour effectuer une analyse exploratoire des données du lac de données. | Diagramme | Diagramme |  |  | Intégration d’Experience Platform Query Service et de l’outil BI |  | 1 | 3 | Couvre Query Service, non spécifique à CJA. Peut être mal placé dans le dossier CJA ; envisagez de vous déplacer vers experience-platform/. Une audience architecte forte (PostgreSQL, outils BI). |
| help/blueprints/customer-journeys/overview.md | Plans directeurs du parcours client | Plateformes marketing modernes prenant en charge les parcours orientés événement et les campagnes lancées par la marque sur l’ensemble des canaux. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : overview.md. Table des matières pour les sous-catégories de parcours ; décrit le positionnement de Journey Optimizer et de Campaign. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Plans directeurs Journey Optimizer | Orchestration des profils 1:1 basée sur les événements et communications de marque basées sur l’audience sur l’ensemble des canaux. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : overview.md. Page de destination avec onglets de cas d’utilisation et modèles d’intégration. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer - Messages déclenchés et plan directeur Adobe Experience Platform | Workflows pilotés par des événements en temps réel offrant des expériences personnalisées en plusieurs étapes basées sur le comportement des clients. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | Remplacer 2 avec avertissement : agent marqué comme probablement en double, mais incertain. Vérifiez l’alignement de la portée avant de réduire l’étendue. Les considérations d’architecture peuvent être uniques (fraîcheur de profil, durée de qualification du segment) et mériter d’être conservées dans le diagramme. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer - Orchestration des campagnes | Communications à plusieurs étapes basées sur l’audience planifiées sur les canaux sortants : e-mail, SMS, notification push, courrier. | Modèle | Dupliquer |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | Remplacer 2 : modèle équivalent. Diagrammes d’architecture multiples ; à conserver sous forme de diagramme. Contenu unique : détails sur l’architecture de la base de données relationnelle, du portail d’audience et du profil maigre. |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Journey Optimizer - Plan directeur de la messagerie tierce | Démontre l’intégration de Journey Optimizer à des systèmes de messagerie tiers pour les communications orchestrées. | Mixte | Partage | campaign-management-orchestration | Intégration de la messagerie tierce à Journey Optimizer | Architecture de messagerie tierce |  | 2 | 2 | Scinder les scores →. Diagramme (topologie système à système) et contenu de modèle (étapes d’implémentation, contraintes d’intégration : authentification du porteur, aucune adresse IP statique, limites de débit). Les deux valent la peine d’être préservés. |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | Plans directeurs de la gestion des décisions | Diffusez des offres personnalisées sur les parcours des clients via une bibliothèque d’offres et un moteur de décision centralisés. | Navigation | Navigation |  |  |  |  |  |  | Remplacement 1 : overview.md. Décrit les composants de gestion des décisions et les approches de déploiement Edge par rapport au hub. |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | Plan directeur de la gestion des décisions sur Edge | Proposez des offres personnalisées dans des expériences web et mobiles en temps réel avec une latence inférieure à la seconde sur le réseau Edge. | Mixte | Dupliquer |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Remplacement 2 : mappe vers Offer Decisioning. variante de déploiement d’Edge — envisagez de consolider avec le plan directeur du hub en un seul diagramme d’options de déploiement. |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | Plan directeur de la gestion des décisions sur le hub | Diffusez des offres personnalisées sur plusieurs canaux, notamment des kiosques, des expériences assistées par un agent et des diffusions sortantes. | Mixte | Dupliquer |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Remplacement 2 : mappe vers Offer Decisioning. Variante de déploiement Hub : envisagez de consolider le plan directeur Edge en un seul diagramme d’options de déploiement. |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Plan directeur de Campaign v8, Campaign et Platform | Plateforme de gestion de campagnes par lots nouvelle génération avec fonctionnalités ETL, de segmentation et de messagerie transactionnelle. | Modèle | Modèle | campaign-management-orchestration | Orchestration par lots et messagerie transactionnelle de Campaign v8 | Modèles de déploiement de l’architecture de Campaign v8 |  | 4 | 3 | Approche technique distincte (Campaign v8 natif, et non AJO). Diagrammes d’architecture multiples ; structure métier ; KPI implicites dans les mécanismes de sécurisation (lot de 20 millions de msg/h, temps réel de 1 million/h). Aucun équivalent dans le catalogue de modèles existant. Remarque : les scores sont considérés comme Fractionner également — proposer le modèle, mais le rédacteur peut souhaiter conserver le diagramme. |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Modèle d’intégration de Real-Time CDP avec Adobe Campaign v8 | Présente l’intégration des audiences et des profils RTCDP à Campaign v8 pour des conversations personnalisées. | Diagramme | Diagramme |  |  | RTCDP - Échange d&#39;audiences et de profils Campaign v8 |  | 1 | 2 | Plan directeur du connecteur d’intégration, et non cas d’utilisation autonome. Diagramme + brèves conditions préalables/mécanismes de sécurisation. Orienté architecte. |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Journey Optimizer avec plan directeur Adobe Campaign v8 | Présente l’orchestration d’AJO avec les messages transactionnels de Campaign v8 pour des expériences 1:1. | Diagramme | Diagramme |  |  | Journey Optimizer - Intégration des messages transactionnels de Campaign v8 |  | 1 | 2 | Connecteur d’intégration. Diagramme + étapes d’implémentation + contraintes techniques (4 000 msg/5 min de ralentissement, initié par l’événement uniquement). Lien croisé vers des modèles AJO et Campaign v8. |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Plan directeur de Campaign v7 | Obsolète : messagerie par lots, intégration, remarketing, publipostage direct, messagerie transactionnelle simple. | Navigation | Navigation |  |  |  |  |  |  | PRODUIT OBSOLÈTE (liens de frontMATTER vers v8). Contenu minimal (diagramme d’architecture uniquement). Ne migrez pas. |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Real-Time CDP avec modèle d’intégration de Campaign v7 et de Campaign Standard | Présente l’intégration de RTCDP et du profil client en temps réel à Campaign v7/Standard pour des conversations personnalisées. | Diagramme | Diagramme |  |  | RTCDP - Échange d&#39;audiences et de profils Campaign v7/Standard |  | 1 | 2 | OBSOLÈTE. Connecteur d’intégration. Diagramme + étapes d’implémentation complètes. Ne migrez pas vers un nouveau modèle ; laissez-le en l’état. |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Plan directeur Journey Optimizer avec Adobe Campaign v7 | Présente l’orchestration d’AJO avec les messages transactionnels de Campaign v7 pour des expériences 1:1. | Diagramme | Diagramme |  |  | Journey Optimizer - Intégration des messages transactionnels de Campaign v7 |  | 1 | 2 | OBSOLÈTE. Connecteur d’intégration. Diagramme + étapes d’implémentation + contraintes. Ne migrez pas ; laissez-le en l’état. |
