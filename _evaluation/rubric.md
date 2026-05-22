---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---
# Schéma d’évaluation de plan directeur

Cette rubrique est appliquée à chaque document sous la section « Schémas et plans directeurs d’architecture »
de [TOC.md](../help/blueprints/TOC.md) (lignes 76 à 133) pour recommander si chaque plan directeur doit devenir un
**Modèle de cas d’utilisation**, un **diagramme d’architecture**, les deux (**Partage**) ou être marqué comme
**Dupliquer** d’un modèle existant.

La sortie de l&#39;application de cette rubrique est [blueprint-audit.md](blueprint-audit.md).

## Définitions

- **Modèle de cas d’utilisation** — document décrivant un objectif commercial ou technique spécifique et
en décrivant les approches et les considérations possibles pour atteindre cet objectif.
Forme canonique : `.claude/skills/use-case-pattern-builder/references/pattern-template.md`.
- **Diagramme d&#39;architecture** — Diagramme visuel représentant les fonctionnalités d&#39;un système,
intégrations et flux de données. Narration minimale ; le diagramme est l&#39;artefact.
Exemple canonique : [platform-data-flow.md](../help/blueprints/experience-platform/platform-data-flow.md).

## Notation

Chaque plan directeur est lu de bout en bout et noté par rapport à huit signaux binaires. Chaque signal y contribue
+1 sur le score du modèle ou le score du diagramme.

### Signaux de motif (chacun = +1 Motif)

1. **Définition d’objectifs commerciaux** — Définit les revenus, la rétention, l’acquisition, la génération de pistes, les coûts
réduction, expérience client ou résultat commercial similaire.
2. **KPI ou mesures de succès** — nomme explicitement les mesures, les taux de conversion, les taux de correspondance, le retour sur investissement ou
des mesures de résultats similaires.
3. **Plusieurs options de mise en œuvre ou niveaux de maturité** — présente l’option A / l’option B, de base ou
des alternatives avancées ou comparables que le lecteur ou la lectrice choisit entre.
4. **Liste de contrôle de préparation requise** — répertorie les éléments qui doivent être en place avant l’implémentation.
5. **Étapes de mise en œuvre narratives > ~30 lignes** — conseils pratiques sur la mise en œuvre, non
juste un bref aperçu.

### Signaux du diagramme (chacun = +1 Diagramme)

&#x200B;6. **Image de l’architecture/du flux de données présente** — `.svg`, `.png` ou `.jpg` montrant la topologie du système,
flux de données ou flèches d’intégration.
&#x200B;7. **topologie d’intégration système à système, forme de déploiement ou mécanismes de sécurisation** — décrit comment
les composants se connectent, selon l’emplacement des données, les modèles de déploiement (edge par rapport au hub) ou les limites de capacité.
&#x200B;8. **L’audience est l’architecte des solutions** — le cadrage utilise le déploiement, SDK, Edge, hub ou similaire
une terminologie axée sur l’architecte plutôt que sur le marketeur (campagnes, parcours,
audiences).

## Logique de recommandation

Appliquez d’abord les règles de remplacement. Si aucun remplacement ne se déclenche, dérivez la recommandation des scores.

### Règles de remplacement (priorité la plus élevée)

1. **Le fichier est nommé`overview.md`** → recommandation = `Navigation`. Exclus de la migration ; le
La page est une page de destination de style Table des matières qui sera révisée une fois les fichiers enfants réglés.
2. **Un modèle équivalent existe déjà dans`help/blueprints/use-case-patterns/`** →
recommandation = `Duplicate`. L’action de migration consiste à simplifier le plan directeur pour obtenir une version pure
Diagramme d’architecture et ajoutez un lien croisé « Voir modèle de cas d’utilisation » au modèle existant.
Enregistrez le chemin d’accès du modèle existant dans la colonne `duplicate_of`.
3. **Le fichier est en `experience-platform/` et n’a pas de signal d’objectif commercial (#1)** → par défaut
   `Diagram` indépendamment des autres scores. Ce dossier est le niveau de présentation de l’architecture.

### Recommandation basée sur les scores (lorsque aucun remplacement ne se déclenche)

| Score du motif | Score du diagramme | Recommandation | Raisonnement |
| --- | --- | --- | --- |
| 3 ≥ | ≤ 1 | `Pattern` | Signaux de motif forts, signaux de diagramme faibles → migrer vers le motif. |
| ≤ 1 | 2 ≥ | `Diagram` | Signaux de motif faibles, focus visuel/topologique dominant → conserver sous forme de diagramme. |
| 3 ≥ | 2 ≥ | `Split` | Le contenu enrichi du motif et un diagramme significatif → extraire le motif réduisent l’original au diagramme et interconnectent. |
| 2 | 2 | `Split` | Attache à force modérée → division. |
| 2 | ≤ 1 | `Pattern` | Apprentissage du motif, aucune valeur de diagramme significative. |
| ≤ 1 | ≤ 1 | `Diagram` | Léger dans l’ensemble : probablement une page d’architecture minimale existante. |

## Comment appliquer la rubrique

Pour chaque fichier Markdown de plan directeur de la portée :

1. Lire le fichier complet de bout en bout.
2. Marquez chacun des huit signaux présents/absents.
3. Appliquez des règles de remplacement dans l’ordre. Si l&#39;on déclenche, c&#39;est la recommandation.
4. Sinon, calculez le score du modèle et le score du diagramme, puis recherchez la recommandation.
5. Pour des recommandations `Pattern` et `Split`, proposez :
   - `proposed_pattern_category` — l&#39;un des suivants :
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`, `conversational-experience` ou une nouvelle catégorie intitulée `(new) <name>`.
   - `proposed_pattern_title` — un titre court et orienté vers l&#39;action suivant le modèle existant
style de dénomination.
6. Pour des recommandations `Diagram` et `Split`, proposez :
   - `proposed_diagram_title` : généralement le titre existant supprimé du cadre d’entreprise.
7. Capturez les doublons trouvés en comparant la portée du plan directeur au catalogue de modèles existant
en `duplicate_of`.
8. Enregistrez les questions ouvertes, le contenu technique unique qui mérite d’être préservé ou le risque de migration en `notes`.

## Catalogue des modèles de cas d’utilisation existants (pour la détection des doublons)

| Catégorie | Modèles |
| --- | --- |
| audience-building-activation | audience-activation-to-destinations, audience-collaboration-correspondance-segment, b2b-activation-audience, transfert d’événement |
| personnalisation | anonymous-visitor-web-personalization, known-visitor-web-app-personalization, offer-decisioning, comportemental-recommendation |
| campaign-management-orchestration | activation de messages sortants par lots, messagerie déclenchée par un événement, parcours orchestré à plusieurs étapes, parcours cross-canal avec prise de décision, marketing basé sur un groupe d’achats |
| analyse | customer-analytics-insight-generation, b2b-analytics |
| conversational-experience | brand-concierge-conversational-experience |
