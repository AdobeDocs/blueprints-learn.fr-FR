---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---
# Guide de style de l’icône du cas d’utilisation

## Présentation

Les icônes de cas d’utilisation servent d’identifiants visuels dans le tableau du catalogue de cas d’utilisation. Ils doivent être immédiatement reconnaissables à une largeur d&#39;affichage de 40 px tout en conservant leur qualité à leur résolution native de 1 024 x 1 024.

## Spécifications techniques

| Propriété | Valeur |
| --- | --- |
| Dimensions | 1 024 x 1 024 pixels |
| Format | PNG (RGB 8 bits ou RGBA) |
| Taille du fichier | 900KB - 1,4 Mo standard |
| Taille d’affichage | Largeur de 40 px dans les tables de catalogue |
| Dénomination | `icon-{kebab-case-name}.png` |
| Chemin de stockage | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## Instructions de style visuel

### Composition
- **Sujet central unique** — Chaque icône doit comporter une métaphore visuelle claire qui représente le concept du cas d’utilisation
- **Composition centrée** — Le sujet principal doit être centré avec un espace équilibré
- **Pas de texte** — Le texte est illisible à 40 px ; utilisez uniquement une métaphore visuelle
- **Pas de scènes complexes** — Évitez les compositions à plusieurs éléments, les fonds contenant de nombreux objets ou les scènes narratives
- **Silhouettes en gras** — La forme de l&#39;icône doit être reconnaissable même comme une silhouette minuscule

### Couleur et ton
- **Palette propre et moderne** — Utilisez des couleurs professionnelles adaptées à l&#39;entreprise
- **Cohésion de l’industrie** — Les icônes d’une même industrie doivent avoir l’impression d’appartenir au même secteur
- **Contraste élevé** — Assurez-vous que le sujet principal se démarque clairement du fond
- **Évitez les couleurs au néon ou trop saturées** — Gardez la palette raffinée et professionnelle

### Style
- **Moderne et professionnel** — Lignes épurées, finition polie
- **Rendu cohérent** — Toutes les icônes doivent provenir du même système de conception
- **3D ou plat est acceptable** — Mais restez cohérent dans un secteur industriel vertical
- **Éviter le photoréalisme** — Style illustré ou rendu préféré pour la cohérence
- **Pas de logos de marque ni d&#39;images de marque** — Utilisez des métaphores visuelles génériques

### Test De Lisibilité De Petite Taille
Avant de terminer, mettez l’image à l’échelle mentalement pour qu’elle atteigne 40 pixels :
- Pouvez-vous identifier le sujet principal ?
- Le contraste entre le premier plan et l’arrière-plan est-il suffisant ?
- Existe-t-il de petits détails qui se transformeraient en bruit visuel ?
- La forme se lit-elle clairement sans couleur (en cas d’accessibilité) ?

## Exemples de métaphore visuelle par secteur

### Grande distribution
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Panier abandonné | Panier avec articles |
| Recommandations de produit | Boîte cadeau ou produits organisés |
| Vente Croisée | Articles d’achat connectés |
| Série de bienvenue | Carte ou cadeau de bienvenue |
| Baisse De Prix | Balise de prix avec flèche vers le bas |

### Automobile
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Rappels de service | Calendrier de clé ou de service |
| Achat de véhicule | Voiture avec clés |
| Reprise | Flèches d&#39;échange de voitures |
| Voiture Connectée | Voiture avec connexion digitale |

### services de santé
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Rappel de rendez-vous | Calendrier avec stéthoscope |
| Observance du traitement | Flacon de pilule ou ordonnance |
| Soins Préventifs | Bouclier avec symbole de santé |

### Services Financiers
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Formation de leads | Graphique de croissance du semis |
| Prévention de l’attrition | Bouclier ou symbole de rétention |
| Stade de la vie | Jalons de la vie |

### B2B
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| ABM | Cible avec création |
| Score du lead | Jauge ou thermomètre de mesure |
| Renouvellement de contrat | Document avec symbole d&#39;actualisation |

### Voyage et hébergement
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Abandon de panier | Valise ou réservation |
| Programme de fidélité | Carte de fidélité ou badge étoile |
| Rappels de réservation | Calendrier avec avion/hôtel |

### Assurance
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Renouvellement de la politique | Document avec flèches de renouvellement |
| Processus de réclamation | Presse-papiers avec coche |
| Vente Croisée | Documents de politique connectés |

### Médias et divertissement
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Nouveau contenu | Bouton de lecture ou projecteur |
| Recommandations de contenu | Liste de lecture sélectionnée ou contenu étoilé |
| Résiliation d’abonnement | Carte d’abonnement endommagée |

### Télécommunications
| Cas d’utilisation | Métaphore visuelle |
| --- | --- |
| Optimisation du plan | Barres de signalisation avec engrenage |
| Mise à niveau de l’appareil | Téléphone avec flèche vers le haut |
| Prévention de l’attrition | Bouclier avec signal |

## Modèle d’invite de génération d’image

Utilisez ce modèle comme point de départ, en personnalisant l’objet et les détails de chaque cas d’utilisation :

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### Conseils de personnalisation de l’invite

- **Soyez précis sur le sujet** — « Un panier rouge vif avec deux boîtes-cadeaux colorées à l&#39;intérieur » vaut mieux qu&#39;un « panier »
- **Spécifier le traitement d&#39;arrière-plan** — « sur un arrière-plan bleu doux » ou « sur un arrière-plan blanc clair avec une ombre subtile »
- **Mentionner l&#39;éclairage** — « éclairage studio doux » ou « lumière ambiante douce » permet d&#39;obtenir une cohérence
- **Ajouter des modificateurs de style** — « minimaliste », « géométrique », « isométrique » ou « conception plate » pour orienter l’esthétique
- **Inclure les invites négatives si pris en charge** — « pas de texte, pas de filigrane, pas de bordure, pas d’éléments photoréalistes »

## Inventaire des icônes existantes

### Par secteur

**Vente au détail (9 icônes) :**
icône-panier-abandonné, icône-inventaire-urgence, icône-chute-prix, icône-recommandations-produit, icône-pages-catégorie, icône-série-bienvenue, icône-réapprovisionnement, icône-post-achat, icône-vente-croisée-montée en gamme

**Automobile (12 icônes) :**
icon-service-reminders, icon-rappel-notifications, icon-test-drive, icon-model-launch, icon-trade-in, icon-parts-accessoires, icon-garantie, icon-connector-car, icon-dealer-network, icon-véhicule-achat, icon-financement, icon-owner-loyalty

**Services financiers (6 icônes) :**
icon-lead-nurturing, icon-account-dashboard, icon-product-recommendation, icon-churn-prevention, icon-life-stage

**Soins de santé (4 icônes) :**
icône-rendez-vous-rappel, icône-post-visite, icône-soins-préventifs, icône-médication-observance

**Assurance (3 icônes) :**
icône-politique-renouvellement, icône-revendications-processus, icône-vente croisée

**Médias et divertissement (3 icônes) :**
icon-new-content, icon-content-recommendations, icon-subscription-churn

**Télécommunications (3 icônes) :**
icon-plan-optimization, icon-device-upgrade, icon-churn-prevention

**Voyage et hébergement (12 icônes) :**
icon-cart-abandon-du-panier, icon-booking-reminders, icon-season-campaigns, icon-personalised-homepage, icon-high-intent, icon-post-réservation-upsell, icon-win-back, icon-dynamic-itinerary, icon-recent-browsed, icon-group-booking, icon-exit-intent, icon-loyalty-program

**B2B (11 icônes) :**
icon-webinar-demo, icon-abm, icon-lead-scoring, icon-content-personalization, icon-event-registration, icon-trial-conversion, icon-customer-onboarding, icon-concurrent-replace, icon-case-study, icon-Contract-renouvellement, icon-upsell-expansion
