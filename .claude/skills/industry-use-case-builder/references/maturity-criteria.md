---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---
# Critères d’évaluation de la maturité du cas d’utilisation

## Niveaux de maturité

### Fondamental

**Badge:** `[!BADGE Foundational]{type=Neutral}`

Un cas d’utilisation est **fondamental** lorsqu’il :

- Mappe sur un modèle à une seule étape ou déclenché par un événement (messagerie déclenchée par un événement, activation des messages sortants par lots).
- A des exigences de données simples (type d’événement unique, attributs de profil standard)
- Nécessite peu ou pas de fonctionnalités d’IA/ML
- Utilise la diffusion par canal standard (e-mail, SMS, notification push) sans orchestration complexe
- Dispose de modèles d’implémentation bien établis avec des bonnes pratiques claires.
- Nécessite moins d’intégrations système (généralement 1 à 2 sources de données)

**Modèles standard :** messagerie déclenchée par un événement, activation de messages sortants par lots

**Exemples : récupération de panier abandonné** rappels de rendez-vous, notifications de service, alertes de chute de prix, rappels de paiement de facture

### Émergent

**Badge:** `[!BADGE Emerging]{type=Informative}`

Un cas pratique est **émergent** lorsqu’il :

- Correspond à un modèle de personnalisation ou à plusieurs étapes (Parcours orchestré en plusieurs étapes, Personalization de visiteur connu, recommandation comportementale, Personalization de visiteur anonyme)
- Nécessite la collecte et l’analyse de données comportementales
- Utilise des modèles de recommandation pour la résolution des profils de visiteurs connus
- Implique des séquences de maturation multipoint avec une logique de branchement
- Présente une complexité d’intégration modérée (2 à 4 sources de données).
- Peut nécessiter l’activation de l’audience ou le ciblage basé sur les segments

**Modèles standard :** Parcours orchestré à plusieurs étapes, Personalization web/d’application connu du visiteur, recommandation comportementale, Personalization web de visiteur anonyme, Audience Activation B2B

**Exemples : série de bienvenue** campagnes d’observance des médicaments, tableaux de bord de comptes personnalisés, score des prospects, recommandations de contenu.

### Avancé

**Badge:** `[!BADGE Advanced]{type=Caution}`

Un cas d’utilisation est **Avancé** lorsqu’il :

- Associe à un modèle de prise de décision ou d’orchestration cross-canal (Parcours cross-canal avec prise de décision, Offer Decisioning)
- Nécessite une prédiction ou un score de propension optimisé par l’IA
- Utilise une logique de décision centralisée sur plusieurs canaux simultanément.
- Implique une orchestration complexe avec une prise de décision en temps réel à plusieurs points de parcours
- Présente une complexité d’intégration élevée (plus de 4 sources de données, flux de données en temps réel).
- Nécessite des règles métier sophistiquées, une gestion des priorités et une gouvernance des fréquences

**Modèles standard :** Parcours cross-canal avec prise de décision, Offer Decisioning

**Exemples : prévention de l’attrition** la notation par l’IA, recommandations de produits à un stade de vie, optimisation des ventes croisées, personnalisation du programme de fidélité, offres exclusives VIP

## Processus d’évaluation

1. Identifier le modèle de cas d’utilisation auquel le cas d’utilisation correspond
2. Consultez la liste « Modèles standard » ci-dessus pour une correspondance rapide
3. Si le modèle n’indique pas clairement la maturité, évaluez la complexité des données, les exigences d’IA/ML et la portée de l’intégration
4. Présentez l&#39;évaluation à l&#39;utilisateur avec le raisonnement suivant : « Sur la base de la cartographie des motifs ({pattern}) et {key factors}, je classifierais ceci comme {level} parce que {reasoning}. »
5. Laisser l’utilisateur confirmer ou remplacer avant de continuer
