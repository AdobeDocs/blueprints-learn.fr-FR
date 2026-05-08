---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---
# Mécanismes de sécurisation de l’étendue : page Architecture et page Modèle de cas d’utilisation

Le site de plans directeurs sépare les **pages de diagramme d’architecture** des **pages de modèle de cas d’utilisation** car elles répondent à différents besoins du lecteur. Ce document définit l’élément qui doit être placé à l’emplacement approprié et comment gérer le contenu qui glisse au-delà des limites.

## La distinction fondamentale

- Les **pages de diagramme d’architecture** sont des références visuelles de niveau supérieur. Ils répondent : *« Comment ces systèmes s&#39;intègrent-ils ? Où sont les points d&#39;intégration ? Quelle est la forme du flux de données ? »* Les lecteurs viennent ici pour s&#39;orienter.
- Les **pages de modèles de cas d’utilisation** sont des guides de mise en œuvre. Ils répondent : *« Comment puis-je créer cette fonctionnalité ? Quelles sont les fonctions impliquées ? Quels indicateurs de performance clés mesurent le succès ? Quelles sont mes options d’implémentation* Les lecteurs viennent ici lorsqu’ils ont un cas d’utilisation et qu’ils doivent l’envoyer.

## Appartient à une page d’architecture

| Catégorie | Exemples |
| --- | --- |
| Architecture de niveau supérieur | Diagrammes de présentation d’AEP et des applications, de la structure marketing d’Experience Cloud, de la topologie hub vs edge |
| Flux de données système | Chemins d’ingestion en temps réel ou par lots, synchronisation des profils entre le hub et le edge, flux de recherche ou d’activation |
| Points d’intégration | Où AEP s’intègre à AJO, CJA, Target, Campaign, Marketo, Workfront ; limites de SDK ; surfaces d’API |
| Topologie de déploiement | Déploiement de Web SDK par rapport à Mobile SDK, transfert côté serveur, placement de nœuds Edge |
| Architecture de l’application | La structure interne d’une application unique (AJO, CJA, RTCDP) au niveau du système |
| Conseils pour utiliser les modèles de cas | « Cette architecture prend en charge les modèles X, Y, Z » avec des liens : la page d’architecture ne duplique **pas** contenu |

## N’appartient PAS à une page d’architecture

Si vous vous trouvez à rédiger l’un des documents suivants, redirigez-vous vers une page de modèle de cas d’utilisation (utilisez les compétences `use-case-pattern-builder` ) :

| Catégorie | Pourquoi c&#39;est ailleurs |
| --- | --- |
| KPI et formules de mesure | Les modèles de cas d’utilisation mesurent les résultats, contrairement aux pages d’architecture |
| Objectifs commerciaux, impact sur l’entreprise | Le contenu KBO vit sous `/help/blueprints/business-objectives/` ; les modèles le référencent |
| Exemples de cas d’utilisation tactiques | « Rappel d’abandon de panier », « Héros de page d’accueil personnalisée », etc. - il s’agit de contenu de modèle |
| Chaînes de fonctions (`A > B > C > D`) | Le concept de chaîne de fonction fait partie du modèle de modèle de cas d’utilisation |
| Histoires personnelles | « Maria, la spécialiste marketing, veut... » les scénarios de style appartiennent aux modèles et non aux références d’architecture |
| Options de mise en œuvre | Les conseils de mise en œuvre à options multiples (idéal pour les utilisateurs, fonctionnement, avantages, limites) sont une construction de modèle |
| Tables de fonctions de base/annexes | Il s’agit de sections de page de motifs |
| Listes de contrôle prérequises par cas d’utilisation | Les modèles effectuent le suivi ; les pages d’architecture renvoient à des modèles à la place |

## Expressions de déclenchement à surveiller

Si l’utilisateur ou l’utilisatrice fournit l’une de ces expressions lors de la description de la nouvelle page, interrompez et vérifiez à nouveau la portée :

- « KPI »
- « impact commercial » / « résultats commerciaux »
- « cas d’utilisation tactiques » / « exemples de scénarios »
- « chaîne de fonction »
- « options d’implémentation »
- « idéal pour »
- « avantages et limites »
- « conditions préalables »
- « personnes » / « parties prenantes »
- « mesure »

Ces actions n’excluent pas automatiquement la page, mais indiquent que l’utilisateur peut souhaiter une page de modèle de cas d’utilisation, et non une page d’architecture. Confirmez l’intention avant de procéder à la génération.

## Que faire lorsque le contenu dérive

1. **Identifier la dérive.** Pointez sur la section ou la puce qui a traversé la frontière.
2. **Proposez deux options à l’utilisateur :**
   - Supprimez la section de la page d’architecture (la plus courante : maintient la page d’architecture concentrée).
   - Arrêtez puis passez à `use-case-pattern-builder` pour ce contenu (lorsque l’utilisateur souhaite réellement une page de modèle).
3. **Attendez la confirmation.** Ne réécrivez pas ou ne déposez pas de contenu en silence.
4. **Si vous conservez du contenu axé uniquement sur l’architecture**, remplacez le contenu profond par une seule puce sous `## Use case patterns supported` lien vers le modèle approprié (existant ou à créer).

## Cas Edge

- **La page est une moitié d’architecture, une moitié de modèle.** Divisez en deux pages : une page d’architecture (cette compétence), une page de modèle de cas d’utilisation (la compétence `use-case-pattern-builder`). Liez-les.
- **La page Architecture décrit un cas d’utilisation unique de bout en bout.** Il s’agit d’un modèle de cas d’utilisation, pas d’une page d’architecture. Rediriger vers `use-case-pattern-builder`.
- **La page Architecture doit afficher des exemples de flux de données pour un scénario spécifique.** Acceptable si le scénario est uniquement indicatif et que la majeure partie de la page reste au niveau de l’architecture du système. Conservez l’exemple dans un paragraphe et liez-le au modèle approprié pour obtenir plus de détails.

## Test rapide

Avant de générer, demandez-vous *« Si un lecteur ou une lectrice arrive sur cette page en s’attendant à une référence d’architecture de niveau supérieur, en obtiendra-t-il une ou obtiendra-t-il une présentation de cas d’utilisation à moitié terminée ? »* Dans ce dernier cas, la page appartient à `use-case-pattern-builder`.
