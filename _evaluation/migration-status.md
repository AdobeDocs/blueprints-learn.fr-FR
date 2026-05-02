---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---
# Statut de migration : plans directeurs pour les modèles de cas d’utilisation

Ce document capture l’état de l’effort de réorganisation du plan directeur afin qu’il puisse être repris proprement entre les sessions.

**Dernière mise à jour :** 2026-04-29

## Où nous en sommes maintenant

**Actuellement en pause le :** `b2b/overview.md` (#1 de 10 de plan directeur de section B2B) - en attente de la décision sur l’opportunité de laisser tel quel, d’ajouter une référence croisée à la nouvelle section Activation B2B et modèles marketing, ou de mettre à jour le tableau pour répertorier tous les plans directeurs + ajouter une référence croisée.

**Pour reprendre :** répondre avec **A** (laisser en l’état, recommandé), **B** (ajouter une référence croisée) ou **C** (mettre à jour le tableau + ajouter une référence croisée). Continuez ensuite avec les #2 de plan directeur (`b2b/b2bactivation.md`).

## Approche de travail

Le schéma de travail actuel, adopté au cours de cette session, est le suivant :

1. **Garder les plans directeurs actifs** — pas d’obsolescence. Chaque plan directeur reste en place sous la forme d’une page axée sur l’architecture.
2. **Ajoutez une astuce de lien croisé** à chaque plan directeur avec un modèle de cas d’utilisation associé/se chevauchant, immédiatement après le H1 :

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Migrer les diagrammes** — si un plan directeur comporte un diagramme d’architecture qui fait défaut au modèle associé, ajoutez une section `## Architecture` au modèle référençant le même SVG via un chemin absolu. La ressource reste à son emplacement d’origine (aucune copie de fichier).
4. **Rogner les étapes d’implémentation** à partir du plan directeur lorsque le motif le couvre. Les sections à supprimer incluent généralement : `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, parfois `## Prerequisites`. Utilisez le jugement par plan directeur.
5. **Parcourez-les une par une** — proposez des modifications par plan directeur, obtenez l’approbation de l’utilisateur, puis appliquez.

### Règles universelles

- Le libellé de l’ASTUCE sur les liens croisés est cohérent : `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- Nouveaux fichiers (modèles de cas d’utilisation créés lors de la migration) **ne pas inclure`exl-id`** — La publication Adobe les affecte.
- Les références d’image dans les fichiers nouvellement créés utilisent des chemins absolus (`/help/blueprints/...`), et non relatifs.
- Les valeurs de `exl-id` existantes dans les pages existantes sont conservées.
- Les redirections dans `redirects.csv` suivent le format `source,dest` avec des chemins d’accès `/en/docs/...` (pas de `.html`).

## Phases A à E (travaux structurels initiaux) — ACHEVÉ

| Phase | Résultat |
| --- | --- |
| A | Création de `B2B Activation & Marketing` catégorie de modèle de cas d’utilisation. Déplacement de 3 modèles existants (`b2b-audience-activation` → `b2b/account-audience-activation`, `buying-group-based-marketing` → `b2b/buying-group-marketing`, `b2b-analytics` → `b2b/account-analytics`). 3 redirections ajoutées. |
| B | Copie de 4 plans directeurs B2B dans `use-case-patterns/b2b/` (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | Copie de 4 plans directeurs non B2B (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | Copie de 2 plans directeurs fractionnés (`audience-sharing-with-target`, `third-party-messaging`). |
| E | Ajout d’une ASTUCE de lien croisé à 9 plans directeurs classés en double. |

Nombre total de modèles de cas d’utilisation après A-E : **26 modèles** dans 6 catégories.

## Présentation section par section (en cours)

La présentation de section applique l’approche de lien croisé, de migration de diagramme ou d’implémentation de rognage à chaque plan directeur individuellement sous la révision de l’utilisateur.

### ✅ Audience &amp; Profile Activation — 8/8 terminé

| # | Plan directeur | Action effectuée |
| --- | --- | --- |
| 1 | `audience-manager.md` | Conseil de lien croisé + diagramme migré vers le motif (`anonymous-visitor-web-personalization`) + étapes d’implémentation de RTCDP supprimées |
| 2 | `enterprise-destinations.md` | Conseil de lien croisé + diagramme migré vers le motif (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Étapes Impl supprimées (99 → 35 lignes) |
| 4 | `customer-activity.md` | Étapes Impl supprimées (51 → 40 lignes) |
| 5 | `data-science.md` | Considérations sur l’Impl supprimées (46 → 40 lignes) |
| 6 | `real-time-lookup.md` | Prérequis + modèles/étapes/considérations impl supprimés (156 → 73 lignes) |
| 7 | `segment-match.md` | **Aucune modification** (l’utilisateur a choisi de laisser tel quel) |
| 8 | `rtcdp-target.md` | Modèles Impl + considérations supprimés (99 → 74 lignes) |

### 🟡 B2B Activation &amp; Marketing — 1/10 en cours

| # | Plan directeur | Etat |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **EN PAUSE** — en attente de la décision A/B/C (voir « Où en sommes-nous maintenant » ci-dessus) |
| 2 | `b2b/b2bactivation.md` | En attente — Phase E dupliquée ; lien croisé ajouté ; révision nécessaire pour le diagramme + rognage impl |
| 3 | `b2b/b2b-account-activation.md` | En attente - Classement par diagramme ; nécessite un lien croisé vers `b2b/account-audience-activation.md` + prise en compte de la migration des diagrammes |
| 4 | `b2b/b2b-buying-group-journeys.md` | En attente — Phase E Dupliquer ; lien croisé ajouté ; révision nécessaire |
| 5 | `b2b/b2b-journeys-with-marketo.md` | En attente — Copie de la phase B ; le motif est une copie ; une coupure en plusieurs étapes est nécessaire |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | En attente — Copie de la phase B ; rognage en plusieurs étapes nécessaire |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | En attente — Page de destination de la section |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | En attente — Copie de la phase B ; rognage en plusieurs étapes nécessaire |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | En attente — Copie de la phase B ; rognage en plusieurs étapes nécessaire |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | En attente — Page Liens uniquement (audit marqué comme Navigation) |

### ⚪ Customer Journey Analytics — 0/5 pas encore démarré

Fichiers : `overview.md`, `b2b-cja.md` (phase E en double, lien croisé ajouté), `cja-rtcdp.md` (groupe 2 - recommander le lien croisé à `customer-analytics-insight-generation`), `cja-ajo.md` (groupe 2 - même), `analysis.md` (groupe 3, éventuellement déplacer vers experience-platform/).

### ⚪ Parcours clients — 0/14 pas encore démarré

Fichiers : `overview.md` ; `journey-optimizer/` (4 fichiers : présentation, parcours [Phase E], campagnes [Phase E], messagerie tierce [Phase D]); `decision-management/` (3 fichiers : présentation, edge [Phase E], hub [Phase E]); `campaign-v8/` (3 fichiers : présentation [Phase C], rtcdp-and-v8, ajo-and-v8); `campaign-v7/` (3 fichiers obsolètes).

### ⚪ Experience Platform — 0/6 pas encore démarré

Fichiers : `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. Tous ont été notés en tant que diagramme uniquement avec 0 signal de motif dans l’audit. **Probablement tous « aucun changement »** : il s’agit d’une architecture fondamentale avec laquelle aucun modèle de cas d’utilisation ne chevauche.

## Fichiers de référence

| Fichier | Objectif |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Tableau d’audit par plan directeur (43 lignes) avec recommandations |
| [rubrique.md](rubric.md) | Rubrique de notation utilisée pour classer les plans directeurs |
| [migration-redirections.csv](migration-redirects.csv) | Redirections intermédiaires à partir de la migration |
| [redirections.csv](../redirects.csv) | Fichier de redirections canoniques (3 lignes ajoutées lors de la phase A) |

## Questions ouvertes non résolues (issues de l’audit)

1. **Edge de gestion des décisions + hub** — actuellement reliés à `offer-decisioning`. Envisagez-vous de consolider en un seul diagramme d’options de déploiement ?
2. **`journey-optimizer-journeys.md`** — signalée comme doublon incertain de `event-triggered-messaging` ; vérifiez la portée avant de la rogner.
3. **`customer-journey-analytics/analysis.md`** — le contenu concerne Experience Platform Query Service, et non CJA ; envisagez d’effectuer une relocalisation vers `experience-platform/`.
4. **Campaign v7 (3 fichiers obsolètes)** — migrer, quitter ou supprimer de la table des matières ?
5. **`customer-success-stories.md`** — page de liens uniquement ; confirmez la classification Navigation .
6. **L’ancre de table des matières** pour la nouvelle section B2B est `{#b2b-patterns}` ; confirmez-la avant toute création de redirection de production.

## Reprise

Ouvrez une nouvelle session Claude Code dans ce référentiel et dites :

> Reprenons la migration des plans directeurs. Lisez `_evaluation/migration-status.md` pour reprendre là où nous en étions.

La prochaine étape concrète : répondre à la décision `b2b/overview.md` (A/B/C). Continuez ensuite avec le #2 de plan directeur (`b2b/b2bactivation.md`) et passez par la section B2B, puis Customer Journey Analytics, Customer Parcours et Experience Platform.
