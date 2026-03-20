---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---
# Modèle de ligne du catalogue de cas d’utilisation

## Format des lignes

Chaque ligne du tableau du catalogue des cas d’utilisation suit ce format exact :

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### Ligne sans icône (à utiliser lorsque l’icône n’est pas encore disponible)

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## Référence du champ

| Champ | Format | Exemple |
| --- | --- | --- |
| industrie | nom du répertoire en majuscules | commerce de détail, services financiers, voyage-hébergement |
| nom-kebab | nom du cas d’utilisation kebab pour l’icône | chariot abandonné, entretien du plomb |
| Texte de remplacement | Casse du titre, court | Panier abandonné, entretien des leads |
| cap-ancre | kebab-case de l’en-tête ## dans la vue d’ensemble | abandonné-panier-récupération-des-e-mails |
| Maturité + Type | Syntaxe des badges | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## Marqueurs d’onglet Secteur dans le catalogue

Le fichier catalogue utilise cette structure d’onglets :

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## Ordonner dans les onglets

Les lignes sont classées par niveau de maturité :

1. **De base** lignes en premier (type=Neutre)
2. **Émergent** deuxième ligne (type=Informatif)
3. **Avancé** dernières lignes (type=Attention)

Au même niveau de maturité, ajoutez de nouvelles lignes à la fin de ce groupe.
