---
title: Cas d’utilisation de vente au détail
description: Découvrez comment les organisations de vente au détail utilisent Adobe Experience Platform pour personnaliser les expériences d’achat, récupérer les paniers abandonnés et fidéliser les clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2590'
ht-degree: 0%

---


# Cas d’utilisation de vente au détail

Les organisations de vente au détail utilisent Adobe Experience Platform pour unifier les données client des magasins en ligne, des emplacements physiques et des programmes de fidélité en une vue unique de chaque acheteur. Cette base permet des expériences d’achat personnalisées, une sensibilisation opportune qui récupère les revenus perdus et des stratégies de fidélité qui font revenir les clients.

## Recommandations de produits personnalisées

Afficher des recommandations de produits personnalisées sur la page d’accueil, les pages de catégorie et les pages de détails du produit en fonction de l’historique de navigation, de l’historique d’achat et du comportement similaire du client. Lorsque les acheteurs voient des produits adaptés à leurs intérêts, ils passent plus de temps à les explorer et sont beaucoup plus susceptibles d’acheter.

### Impact commercial

Les détaillants constatent généralement une augmentation de 20 à 30 % des taux de clics publicitaires et une amélioration de 15 à 25 % des taux de conversion lorsqu’ils diffusent des recommandations personnalisées plutôt que des listes de produits statiques.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des modèles de recommandation pilotés par l’IA qui apprennent en permanence des interactions des clients pour faire apparaître les produits les plus pertinents pour chaque individu.

### Considérations techniques

- Les données du catalogue de produits doivent être ingérées et tenues à jour, y compris les attributs, les images, le prix et la disponibilité des produits, afin de garantir que les recommandations reflètent ce que les clients peuvent réellement acheter.
- Les signaux comportementaux tels que les consultations de produits, les événements d’ajout au panier et les achats doivent circuler en temps quasi réel pour que les recommandations restent actualisées au cours d’une seule session de navigation.
- Les modèles de recommandation nécessitent une stratégie de démarrage à froid pour les nouveaux visiteurs qui ne disposent pas d’un historique de navigation, revenant généralement à des produits tendance ou à meilleures ventes.
- Les performances de chargement de page doivent être surveillées attentivement, car les appels de personnalisation ne doivent pas ajouter de latence notable à l’expérience d’achat.


## Récupération d’e-mails de panier abandonné

Envoyez automatiquement des rappels par e-mail personnalisés aux clients qui ont abandonné leur panier, y compris les articles exacts laissés et les offres pertinentes pour encourager l’achèvement. L&#39;abandon de panier est l&#39;une des plus grandes sources de perte de revenus dans le commerce de détail, et un suivi rapide peut permettre de récupérer une part importante de ces ventes.

### Impact commercial

Les programmes de récupération de panier efficaces offrent un taux de récupération de panier de 25 à 35 % et peuvent générer un chiffre d’affaires mensuel supplémentaire de 100 000 $ à 500 000 $ en fonction du volume du magasin.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond à un événement d’abandon de panier en temps réel, en envoyant un rappel en temps opportun pendant que le degré d’intention d’achat est toujours élevé.

### Considérations techniques

- La détection de l’abandon de panier nécessite de définir un seuil d’inactivité (généralement entre 30 et 60 minutes) avant de déclencher le premier rappel, ce qui évite d’envoyer des messages aux clients qui font toujours des achats.
- Le contenu de l’e-mail doit extraire dynamiquement les images, les prix et la disponibilité actuels des produits du catalogue au moment de l’envoi, car les articles peuvent être vendus ou leur prix peut changer entre l’abandon et la livraison.
- Les règles de limitation de la fréquence doivent empêcher les clients de recevoir plusieurs e-mails d’abandon de panier en peu de temps, en particulier s’ils abandonnent leur panier fréquemment.
- Les listes de consentement et de suppression doivent être vérifiées avant l’envoi, et les clients qui ont effectué leur achat par un autre canal doivent être exclus en temps réel.


## Campagnes d’urgence basées sur les stocks

Déclenchez des alertes en temps réel et des campagnes lorsque l’inventaire des produits est faible, ce qui crée une urgence et encourage l’achat immédiat. Les acheteurs qui constatent qu’il ne reste que quelques articles sont incités à agir rapidement plutôt que de retarder leur décision.

### Impact commercial

Les campagnes d’urgence à faible stock entraînent généralement une augmentation de 30 à 40 % de la conversion pour les produits présentés, tout en contribuant à réduire le surstock en accélérant la vente d’articles dont le mouvement est lent.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond aux événements de seuil d’inventaire, activant automatiquement la messagerie d’urgence lorsque les niveaux de stock tombent en dessous des limites définies.

### Considérations techniques

- Les flux d’inventaire doivent s’intégrer à la plateforme de données client en temps quasi réel afin que les messages d’urgence reflètent les niveaux de stock réels plutôt que les données obsolètes.
- Les niveaux de seuil doivent être configurés par catégorie de produit, car un seuil de « stock faible » pour un produit à volume élevé diffère considérablement d&#39;un seuil pour un article de luxe.
- Les messages doivent être véridiques et conformes aux réglementations de protection des consommateurs ; afficher une fausse rareté peut nuire à la confiance de la marque et peut enfreindre les normes publicitaires sur certains marchés.
- Les canaux de messagerie et d’e-mail sur site doivent être coordonnés afin qu’un client qui a déjà acheté ne continue pas à recevoir des notifications d’urgence pour le même produit.


## Recommandations relatives aux ventes croisées et aux ventes incitatives

Affichez les produits de vente croisée et de montée en gamme pertinents au passage en caisse, dans les e-mails et sur les pages de produits en fonction des modèles d’achat et des relations entre les produits. Suggérer des alternatives complémentaires ou premium au bon moment augmente la taille du panier sans obliger les clients à rechercher eux-mêmes des articles connexes.

### Impact commercial

Des stratégies de vente croisée et de montée en gamme bien exécutées augmentent la valeur moyenne des commandes de 25 à 75 $ et augmentent le chiffre d&#39;affaires par transaction de 10 à 15 %.

### Mise en œuvre

Utilisez le modèle [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Cette approche utilise une logique de décision centralisée pour évaluer toutes les offres disponibles et sélectionner la meilleure option de vente croisée ou de vente incitative pour chaque client et contexte.

### Considérations techniques

- Les données relatives aux relations de produit, y compris les associations et les chemins de mise à niveau « fréquemment achetés ensemble », doivent être conservées et régulièrement actualisées pour refléter les schémas d’achat actuels.
- La logique de classement des offres doit tenir compte de la marge, de la pertinence et des niveaux de stock afin que les options les plus rentables et disponibles apparaissent en premier.
- Les recommandations de ventes croisées lors du passage en caisse doivent être chargées rapidement et ne pas perturber le flux d’achat ; les suggestions lentes ou intrusives peuvent en fait réduire la conversion.
- [!DNL Journey Optimizer] règles de décision doivent inclure des offres de secours afin que chaque client éligible reçoive une recommandation, même si l’option la mieux classée n’est pas disponible.


## Nouvelle série de bienvenue clients

Automatisez une série de bienvenue multi-e-mails pour les nouveaux clients avec des recommandations de produits personnalisées, des storytelling de marque et des offres spéciales. Les premières interactions après l’adhésion d’un client définissent sa relation à long terme avec la marque, ce qui fait de cette série l’un des programmes à fort impact qu’un retailer peut exécuter.

### Impact commercial

Une série de bienvenue bien conçue génère un taux d’engagement de 40 à 50 % parmi les nouveaux clients et améliore de manière significative la valeur sur toute la durée de vie en renforçant rapidement l’affinité de la marque.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce parcours de support multipoint guide les nouveaux clients à travers une séquence d’introduction à la marque, de découverte de produits et de messages d’incitation, en s’adaptant en fonction de leur engagement.

### Considérations techniques

- Le déclencheur d’entrée de parcours doit capturer de manière fiable les événements de création de nouveaux clients à partir de toutes les sources d’enregistrement, notamment le web, les applications mobiles, les points de vente en magasin et les places de marché tierces.
- Les étapes d’attente entre les e-mails doivent être configurées en fonction des données d’engagement. Les clients qui ouvrent et cliquent peuvent recevoir le message suivant plus tôt, tandis que les clients moins engagés bénéficient d’un espacement plus important.
- Les recommandations de produits dans les e-mails de bienvenue doivent refléter ce que le client a parcouru ou acheté lors de sa première visite, et non les best-sellers génériques.
- Les clients qui effectuent un achat au cours de la série de bienvenue doivent se brancher sur un flux post-achat plutôt que de continuer à recevoir des messages axés sur l’acquisition.


## Alertes de chute de prix

Avertissez les clients par e-mail ou notification push lorsque les produits de leur liste de souhaits ou les articles précédemment consultés chutent dans le prix. Les acheteurs qui ont manifesté de l&#39;intérêt mais n&#39;ont pas acheté sont très réceptifs aux réductions de prix, ce qui en fait l&#39;un des moyens les plus efficaces de convertir la contrepartie en ventes.

### Impact commercial

Les alertes de chute de prix génèrent un taux de conversion de 20 à 30 % parmi les destinataires et augmentent de manière mesurable la satisfaction des clients en aidant les acheteurs à sentir qu’ils obtiennent la meilleure valeur.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond aux événements de changement de prix des produits, en les comparant aux signaux d’intérêt du client pour fournir des notifications opportunes.

### Considérations techniques

- La détection des variations de prix nécessite de comparer les prix actuels aux valeurs précédentes dans le flux du catalogue de produits et de déclencher uniquement des alertes pour des réductions significatives plutôt que des fluctuations mineures.
- Les signaux d’intérêt du client (ajouts à des listes de souhaits, consultations de pages de produits, temps passé sur les pages de produits) doivent être stockés et associés efficacement à des milliers de changements de prix quotidiens potentiels.
- Les notifications doivent inclure le prix d’origine, le nouveau prix et le montant des économies pour communiquer clairement la valeur ; les messages vagues « prix réduit » ne suffisent pas pour générer des annonces d’économies spécifiques.
- Les segments [!DNL Real-Time Customer Data Platform] pour les acheteurs sensibles au prix peuvent être utilisés pour prioriser la diffusion des alertes et adapter le ton des messages.


## Rappels de réapprovisionnement

Envoyez des rappels automatisés aux clients pour les produits qu&#39;ils achètent régulièrement, tels que les articles d&#39;abonnement et les consommables, afin d&#39;encourager les achats répétés avant qu&#39;ils n&#39;épuisent leurs stocks. Les rappels proactifs réduisent le risque que les clients passent à un concurrent simplement parce qu&#39;ils ont oublié de passer une nouvelle commande.

### Impact commercial

Les programmes de rappel de réapprovisionnement offrent un taux de renouvellement des achats de 30 à 40 % et améliorent considérablement la fidélisation des clients en permettant aux acheteurs de réapprovisionner facilement les produits dont ils dépendent.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce parcours planifié récurrent utilise les prédictions de fréquence d’achat pour envoyer des rappels à l’heure optimale avant qu’un client ait besoin d’un renouvellement.

### Considérations techniques

- Le calcul de la fréquence d&#39;achat doit tenir compte des taux de consommation variables selon les catégories de produits ; un rappel pour le café doit arriver selon une cadence différente de celle pour les produits de nettoyage.
- Le parcours doit ajuster sa synchronisation de manière dynamique lorsqu’un client passe une commande plus tôt ou plus tard que prévu, en recalibrant le prochain rappel en fonction des données d’achat mises à jour.
- Les rappels doivent inclure un lien de réapprovisionnement direct ou une option de rachat en un clic pour minimiser les frictions et maximiser la conversion à partir de la notification.
- Les clients qui ont déjà passé une commande par un autre canal (en magasin, service d’abonnement) doivent être supprimés pour éviter d’envoyer des rappels non pertinents.


## Pages de catégorie personnalisées

Personnalisez de manière dynamique les pages de catégories pour afficher les produits les plus pertinents en premier lieu en fonction des préférences, des achats précédents et du comportement de navigation de chaque client ou cliente. Lorsque les acheteurs voient des produits correspondant à leurs goûts en haut de la page, ils découvrent ce qu’ils veulent plus rapidement et convertissent à des taux plus élevés.

### Impact commercial

Les pages de catégorie personnalisées entraînent une augmentation de 25 à 35 % de l’engagement des pages de catégorie et améliorent considérablement la découverte de produits, en particulier pour les détaillants disposant de catalogues volumineux.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des stratégies de sélection et des modèles de classement pour réorganiser les produits sur les pages de catégorie en fonction du profil et du comportement en temps réel de chaque visiteur.

### Considérations techniques

- Le classement des produits doit s’exécuter suffisamment rapidement pour éviter les retards de chargement de page ; une personnalisation côté serveur ou une prise de décision basée sur les serveurs Edge est souvent nécessaire pour les pages de catégorie contenant des centaines de produits.
- La logique de personnalisation doit associer les préférences individuelles aux règles de marchandisage, afin de garantir que les produits mis en avant, les nouveaux arrivants et les articles saisonniers bénéficient toujours d’une visibilité appropriée.
- Une infrastructure de tests A/B doit être en place pour mesurer en permanence l’impact sur le chiffre d’affaires des règles de tri personnalisé par rapport aux règles de marchandisage par défaut.
- [!DNL Experience Platform] implémentation de Web SDK doit capturer les interactions de pages de catégories (profondeur de défilement, clics sur les produits, utilisation des filtres) afin d’affiner en permanence les modèles de classement.


## Campagnes De Suivi Après Achat

Envoyez des e-mails après achat avec des conseils d’assistance sur les produits, des suggestions de produits associées, des demandes de révision et des informations sur le programme de fidélité. La période immédiatement après un achat est celle où les clients sont le plus engagés avec la marque, ce qui en fait une fenêtre idéale pour approfondir la relation et encourager l&#39;activité future.

### Impact commercial

Les campagnes post-achat efficaces augmentent les taux de soumission de révisions de 15 à 20 % et génèrent un taux d’achat répété de 10 à 15 %, transformant les acheteurs uniques en clients fidèles.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce flux post-achat en plusieurs étapes utilise une logique d’embranchement pour adapter les messages de suivi en fonction du type de produit, du segment client et de l’engagement avec les e-mails précédents de la série.

### Considérations techniques

- Le parcours doit tenir compte de l’état d’exécution de la commande ; les conseils d’assistance et les demandes de révision ne doivent être envoyés qu’après la livraison du produit et non immédiatement après l’achat.
- Le contenu spécifique au produit (instructions d’entretien, guides d’utilisation, suggestions d’accessoires) nécessite un système de mappage de contenu qui associe chaque catégorie de produit à des documents de suivi pertinents.
- Le moment de la demande de révision doit être optimisé en fonction de la catégorie de produits ; l&#39;électronique peut nécessiter une période d&#39;utilisation plus longue avant une révision significative, tandis que les vêtements peuvent être examinés peu après la livraison.
- Les clients qui effectuent un retour ou un échange doivent être automatiquement supprimés du flux de post-achat standard et redirigés vers un chemin de récupération du service.


## Offres exclusives aux clients de VIP

Identifiez les clients à forte valeur ajoutée et proposez des offres exclusives, un accès anticipé aux ventes et des expériences d’achat personnalisées qui récompensent leur fidélité. Retenir les meilleurs clients est beaucoup plus rentable que d&#39;en acquérir de nouveaux et un traitement exclusif renforce la connexion émotionnelle qui les maintient à dépenser.

### Impact commercial

Les programmes VIP génèrent généralement un taux d’engagement de 50 à 70 % de la part des clients de niveau supérieur et améliorent sensiblement la valeur pour la durée de vie du client en réduisant l’attrition parmi les segments les plus rentables.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Cette approche associe l’orchestration des parcours à la prise de décision en temps réel pour la sélection des offres, ce qui permet de s’assurer que chaque client VIP reçoit l’offre exclusive la plus pertinente sur chaque canal.

### Considérations techniques

- Les critères de segmentation de VIP doivent être clairement définis à l’aide des mesures de récence, de fréquence et de valeur monétaire. De plus, les segments doivent être actualisés suffisamment fréquemment pour capturer les clients récemment qualifiés ou disqualifiés.
- Les offres exclusives doivent être appliquées au point de rachat (web, application, boutique) pour empêcher les clients non VIP d’y accéder, ce qui nécessite l’intégration aux systèmes de promotion et de tarification.
- Les préférences de canal varient considérablement entre les clients à forte valeur ajoutée. Certains préfèrent les e-mails, d’autres répondent aux notifications de l’application ou au publipostage direct. Le parcours doit donc adapter les canaux de diffusion en fonction des engagements passés.
- [!DNL Journey Optimizer] prise de décision doit se coordonner entre les canaux pour empêcher un client VIP de recevoir simultanément la même offre par e-mail, push et SMS.


## Notifications de rupture de stock

Permet aux clients de s’abonner à des notifications lorsque des produits en rupture de stock sont disponibles, puis de les avertir automatiquement par e-mail ou SMS. La capture de la demande pour des produits indisponibles empêche les ventes perdues et donne aux clients une raison de retourner au magasin plutôt que d&#39;acheter auprès d&#39;un concurrent.

### Impact commercial

Les notifications de retour en stock atteignent un taux de conversion de 40 à 50 % parmi les abonnés et réduisent de manière significative les pertes de ventes pour les produits à forte demande qui connaissent des ruptures de stock temporaires.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche des notifications sur les événements de retour en stock, comparant les mises à jour d’inventaire aux inscriptions aux notifications du client pour fournir des alertes en temps opportun.

### Considérations techniques

- La surveillance des stocks doit détecter rapidement les événements de réapprovisionnement ; des retards, même de quelques heures, peuvent entraîner la revente du produit avant que les clients avisés aient la chance d&#39;acheter.
- Lorsqu’un produit populaire est réapprovisionné en quantité limitée, les notifications doivent être échelonnées ou hiérarchisées par date d’inscription afin d’éviter d’envoyer des alertes à plus de clients que le stock disponible ne peut en servir.
- Le mécanisme d’abonnement aux notifications doit capturer les préférences de canal (e-mail ou message texte) et respecter les exigences d’opt-in pour chaque canal, en particulier pour les SMS.
- [!DNL Real-Time Customer Data Platform] attributs de profil doivent effectuer le suivi des produits surveillés par chaque client afin d’éviter les notifications en double si le même produit fait l’objet de plusieurs réapprovisionnements.


## Personalization de l&#39;épreuve sociale

Affichez des épreuves de réseaux sociaux personnalisées, y compris des évaluations et des suggestions de type « Les clients qui ont acheté ceci ont également acheté », en fonction du profil et des préférences de chaque client. L’adaptation des épreuves sociales pour refléter les expériences de clients similaires permet de créer de la confiance plus efficacement que les évaluations génériques seules.

### Impact commercial

Les épreuves sociales personnalisées augmentent les taux de conversion de 10 à 15 % et améliorent la confiance des acheteurs, en particulier pour les primo-accédants et les produits à prix plus élevés où l&#39;hésitation à l&#39;achat est la plus grande.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche personnalise le contenu web pour les visiteurs identifiés, en sélectionnant les avis les plus pertinents et les éléments de BAT des réseaux sociaux en fonction du profil, des préférences et du contexte de navigation du client.

### Considérations techniques

- Les données de révision et d’évaluation doivent être structurées et balisées par attributs du client (tels que le contexte d’achat, le segment client et le cas d’utilisation de produit) afin de permettre un filtrage et une personnalisation significatifs.
- Les éléments d’épreuve des réseaux sociaux doivent se charger de manière asynchrone pour éviter de bloquer le rendu de la page produit principale, car les données de révision peuvent provenir d’une plateforme de révision tierce avec des temps de réponse variables.
- Les réglementations de confidentialité exigent que toutes les données client utilisées pour faire correspondre les avis aux visiteurs soient traitées en fonction des préférences de consentement. L’affichage de contenu « clients comme vous » implique un profilage qui peut nécessiter la divulgation.
- L&#39;adhésion à l&#39;audience [!DNL Experience Platform] peut être utilisée pour sélectionner les commentaires à mettre en évidence, montrant les commentaires des amateurs de plein air des acheteurs de plein air plutôt que les commentaires génériques les mieux notés.
