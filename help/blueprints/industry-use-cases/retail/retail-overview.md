---
title: Cas d’utilisation de vente au détail
description: Découvrez comment les organisations de vente au détail utilisent Adobe Experience Platform pour personnaliser les expériences d’achat, récupérer les paniers abandonnés et fidéliser les clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 89a5b6b5-bb71-4154-bb3b-f6dbbbef13eb
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '7216'
ht-degree: 0%

---

# Cas d’utilisation de vente au détail

Les organisations de vente au détail utilisent Adobe Experience Platform pour unifier les données client des magasins en ligne, des emplacements physiques et des programmes de fidélité en une vue unique de chaque acheteur. Cette base permet des expériences d’achat personnalisées, une sensibilisation opportune qui récupère les revenus perdus et des stratégies de fidélité qui font revenir les clients.

## Recommandations de produits personnalisées

Afficher des recommandations de produits personnalisées sur la page d’accueil, les pages de catégorie et les pages de détails du produit en fonction de l’historique de navigation, de l’historique d’achat et du comportement similaire du client. Lorsque les acheteurs voient des produits adaptés à leurs intérêts, ils passent plus de temps à les explorer et sont beaucoup plus susceptibles d’acheter.

### Impact commercial

Les détaillants bénéficient de taux de clic publicitaire et de taux de conversion améliorés lorsqu’ils proposent des recommandations personnalisées au lieu de listes de produits statiques.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des modèles de recommandation pilotés par l’IA qui apprennent en permanence des interactions des clients pour faire apparaître les produits les plus pertinents pour chaque individu. Il s’agit du modèle approprié lorsque le jeu d’articles est volumineux et qu’il change en permanence, et que la sélection est déterminée par une affinité comportementale, plutôt que par un ensemble limité d’offres régies par des règles d’éligibilité.

### Considérations techniques

- Les données du catalogue de produits doivent être ingérées et tenues à jour, y compris les attributs, les images, le prix et la disponibilité des produits, afin de garantir que les recommandations reflètent ce que les clients peuvent réellement acheter.
- Les signaux comportementaux tels que les consultations de produits, les événements d’ajout au panier et les achats doivent circuler en temps quasi réel pour que les recommandations restent actualisées au cours d’une seule session de navigation.
- Les modèles de recommandation nécessitent une stratégie de démarrage à froid pour les nouveaux visiteurs qui ne disposent pas d’un historique de navigation, revenant généralement à des produits tendance ou à meilleures ventes.
- Les performances de chargement de page doivent être surveillées attentivement, car les appels de personnalisation ne doivent pas ajouter de latence notable à l’expérience d’achat.


## Récupération d’e-mails de panier abandonné

Envoyez automatiquement des rappels par e-mail personnalisés aux clients qui ont abandonné leur panier, y compris les articles exacts laissés et les offres pertinentes pour encourager l’achèvement. L&#39;abandon de panier est l&#39;une des plus grandes sources de perte de revenus dans le commerce de détail, et un suivi rapide peut permettre de récupérer une part importante de ces ventes.

### Impact commercial

Les programmes de récupération de panier efficaces améliorent les taux de récupération de panier et peuvent générer un chiffre d’affaires incrémentiel significatif en fonction du volume du magasin.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond à un événement d’abandon de panier en temps réel, en envoyant un rappel en temps opportun pendant que le degré d’intention d’achat est toujours élevé. Il s’agit du modèle approprié lorsqu’une action client discrète est le déclencheur et que la réponse requise est un message unique et sensible au temps, plutôt qu’une séquence à plusieurs étapes ou une sélection d’offres dynamique.

### Considérations techniques

- La détection de l’abandon de panier nécessite de définir un seuil d’inactivité (généralement entre 30 et 60 minutes) avant de déclencher le premier rappel, ce qui évite d’envoyer des messages aux clients qui font toujours des achats.
- Le contenu de l’e-mail doit extraire dynamiquement les images, les prix et la disponibilité actuels des produits du catalogue au moment de l’envoi, car les articles peuvent être vendus ou leur prix peut changer entre l’abandon et la livraison.
- Les règles de limitation de la fréquence doivent empêcher les clients de recevoir plusieurs e-mails d’abandon de panier en peu de temps, en particulier s’ils abandonnent leur panier fréquemment.
- Les listes de consentement et de suppression doivent être vérifiées avant l’envoi, et les clients qui ont effectué leur achat par un autre canal doivent être exclus en temps réel.


## Campagnes d’urgence basées sur les stocks

Déclenchez des alertes en temps réel et des campagnes lorsque l’inventaire des produits est faible, ce qui crée une urgence et encourage l’achat immédiat. Les acheteurs qui constatent qu’il ne reste que quelques articles sont incités à agir rapidement plutôt que de retarder leur décision.

### Impact commercial

Les campagnes d’urgence à faible stock améliorent la conversion des produits en vedette tout en contribuant à réduire le surstock en accélérant la vente d’articles dont le mouvement est lent.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond aux événements de seuil d’inventaire, activant automatiquement la messagerie d’urgence lorsque les niveaux de stock tombent en dessous des limites définies. Il s’agit du modèle approprié lorsque le déclencheur est un événement système plutôt qu’un comportement du client et que la communication requise est immédiate et réactive plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Les flux d’inventaire doivent s’intégrer à la plateforme de données client en temps quasi réel afin que les messages d’urgence reflètent les niveaux de stock réels plutôt que les données obsolètes.
- Les niveaux de seuil doivent être configurés par catégorie de produit, car un seuil de « stock faible » pour un produit à volume élevé diffère considérablement d&#39;un seuil pour un article de luxe.
- Les messages doivent être véridiques et conformes aux réglementations de protection des consommateurs ; afficher une fausse rareté peut nuire à la confiance de la marque et peut enfreindre les normes publicitaires sur certains marchés.
- Les canaux de messagerie et d’e-mail sur site doivent être coordonnés afin qu’un client qui a déjà acheté ne continue pas à recevoir des notifications d’urgence pour le même produit.


## Recommandations relatives aux ventes croisées et aux ventes incitatives

Affichez les produits de vente croisée et de montée en gamme pertinents au passage en caisse, dans les e-mails et sur les pages de produits en fonction des modèles d’achat et des relations entre les produits. Suggérer des alternatives complémentaires ou premium au bon moment augmente la taille du panier sans obliger les clients à rechercher eux-mêmes des articles connexes.

### Impact commercial

Des stratégies de vente croisée et de montée en gamme bien exécutées augmentent la valeur moyenne des commandes et le chiffre d’affaires par transaction, contribuant ainsi à renforcer l’économie globale du panier.

### Mise en œuvre

Utilisez le modèle [](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Cette approche utilise une logique de décision centralisée pour évaluer toutes les offres disponibles et sélectionner la meilleure option de vente croisée ou de vente incitative pour chaque client et contexte. Il s’agit du modèle approprié lorsque la sélection des offres doit tenir compte de la marge, de la disponibilité des stocks et des règles de relation avec les produits, des contraintes commerciales qui nécessitent une logique de prise de décision régie plutôt qu’un classement par affinité comportementale seul.

### Considérations techniques

- Les données relatives aux relations de produit, y compris les associations et les chemins de mise à niveau « fréquemment achetés ensemble », doivent être conservées et régulièrement actualisées pour refléter les schémas d’achat actuels.
- La logique de classement des offres doit tenir compte de la marge, de la pertinence et des niveaux de stock afin que les options les plus rentables et disponibles apparaissent en premier.
- Les recommandations de ventes croisées lors du passage en caisse doivent être chargées rapidement et ne pas perturber le flux d’achat ; les suggestions lentes ou intrusives peuvent en fait réduire la conversion.
- [!DNL Journey Optimizer] règles de décision doivent inclure des offres de secours afin que chaque client éligible reçoive une recommandation, même si l’option la mieux classée n’est pas disponible.


## Nouvelle série de bienvenue clients

Automatisez une série de bienvenue multi-e-mails pour les nouveaux clients avec des recommandations de produits personnalisées, des storytelling de marque et des offres spéciales. Les premières interactions après l’adhésion d’un client définissent sa relation à long terme avec la marque, ce qui fait de cette série l’un des programmes à fort impact qu’un retailer peut exécuter.

### Impact commercial

Une série de bienvenue bien conçue stimule l’engagement des nouveaux clients et améliore de manière significative la valeur tout au long de la durée de vie en renforçant rapidement l’affinité avec la marque.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [Ce parcours de support multipoint guide les nouveaux clients à travers une séquence d’introduction à la marque, de découverte de produits et de messages d’incitation, en s’adaptant en fonction de leur engagement. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur les événements d’engagement. Un message déclenché unique ne peut pas s’adapter à la logique de dépendance entre les étapes.

### Considérations techniques

- Le déclencheur d’entrée de parcours doit capturer de manière fiable les événements de création de nouveaux clients à partir de toutes les sources d’enregistrement, notamment le web, les applications mobiles, les points de vente en magasin et les places de marché tierces.
- Les étapes d’attente entre les e-mails doivent être configurées en fonction des données d’engagement. Les clients qui ouvrent et cliquent peuvent recevoir le message suivant plus tôt, tandis que les clients moins engagés bénéficient d’un espacement plus important.
- Les recommandations de produits dans les e-mails de bienvenue doivent refléter ce que le client a parcouru ou acheté lors de sa première visite, et non les best-sellers génériques.
- Les clients qui effectuent un achat au cours de la série de bienvenue doivent se brancher sur un flux post-achat plutôt que de continuer à recevoir des messages axés sur l’acquisition.


## Alertes de chute de prix

Avertissez les clients par e-mail ou notification push lorsque les produits de leur liste de souhaits ou les articles précédemment consultés chutent dans le prix. Les acheteurs qui ont manifesté de l&#39;intérêt mais n&#39;ont pas acheté sont très réceptifs aux réductions de prix, ce qui en fait l&#39;un des moyens les plus efficaces de convertir la contrepartie en ventes.

### Impact commercial

Les alertes de chute de prix génèrent une amélioration des taux de conversion parmi les destinataires et augmentent de manière mesurable la satisfaction du client en aidant les acheteurs à sentir qu&#39;ils obtiennent la meilleure valeur.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond aux événements de changement de prix des produits, en les comparant aux signaux d’intérêt du client pour fournir des notifications opportunes. Il s’agit du modèle approprié lorsque le déclencheur est un événement du système de catalogue et que la fenêtre de diffusion est sensible au temps. Un parcours prolongé serait trop lent et aucun suivi en plusieurs étapes n’est nécessaire au-delà de la notification initiale.

### Considérations techniques

- La détection des variations de prix nécessite de comparer les prix actuels aux valeurs précédentes dans le flux du catalogue de produits et de déclencher uniquement des alertes pour des réductions significatives plutôt que des fluctuations mineures.
- Les signaux d’intérêt du client (ajouts à des listes de souhaits, consultations de pages de produits, temps passé sur les pages de produits) doivent être stockés et associés efficacement à des milliers de changements de prix quotidiens potentiels.
- Les notifications doivent inclure le prix d’origine, le nouveau prix et le montant des économies pour communiquer clairement la valeur ; les messages vagues « prix réduit » ne suffisent pas pour générer des annonces d’économies spécifiques.
- Les segments [!DNL Real-Time Customer Data Platform] pour les acheteurs sensibles au prix peuvent être utilisés pour prioriser la diffusion des alertes et adapter le ton des messages.


## Rappels de réapprovisionnement

Envoyez des rappels automatisés aux clients pour les produits qu&#39;ils achètent régulièrement, tels que les articles d&#39;abonnement et les consommables, afin d&#39;encourager les achats répétés avant qu&#39;ils n&#39;épuisent leurs stocks. Les rappels proactifs réduisent le risque que les clients passent à un concurrent simplement parce qu&#39;ils ont oublié de passer une nouvelle commande.

### Impact commercial

Les programmes de rappel de réapprovisionnement augmentent les taux d’achat répétés et la fidélisation de la clientèle en permettant aux acheteurs de réapprovisionner facilement les produits dont ils dépendent.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [Ce parcours planifié récurrent utilise les prédictions de fréquence d’achat pour envoyer des rappels à l’heure optimale avant qu’un client ait besoin d’un renouvellement. Il s’agit du modèle approprié en l’absence d’événement déclencheur discret et le timing doit être calculé à partir de modèles de fréquence d’achat qui se recalibrent dynamiquement ; les messages déclenchés par un événement ne peuvent pas gérer la planification prédictive ni les ajustements de timing lorsque les clients réorganisent leurs commandes de manière anticipée ou tardive.

### Considérations techniques

- Le calcul de la fréquence d&#39;achat doit tenir compte des taux de consommation variables selon les catégories de produits ; un rappel pour le café doit arriver selon une cadence différente de celle pour les produits de nettoyage.
- Le parcours doit ajuster sa synchronisation de manière dynamique lorsqu’un client passe une commande plus tôt ou plus tard que prévu, en recalibrant le prochain rappel en fonction des données d’achat mises à jour.
- Les rappels doivent inclure un lien de réapprovisionnement direct ou une option de rachat en un clic pour minimiser les frictions et maximiser la conversion à partir de la notification.
- Les clients qui ont déjà passé une commande par un autre canal (en magasin, service d’abonnement) doivent être supprimés pour éviter d’envoyer des rappels non pertinents.


## Pages de catégorie personnalisées

Personnalisez de manière dynamique les pages de catégories pour afficher les produits les plus pertinents en premier lieu en fonction des préférences, des achats précédents et du comportement de navigation de chaque client ou cliente. Lorsque les acheteurs voient des produits correspondant à leurs goûts en haut de la page, ils découvrent ce qu’ils veulent plus rapidement et convertissent à des taux plus élevés.

### Impact commercial

Les pages de catégories personnalisées améliorent l’engagement des pages de catégories et la découverte de produits, en particulier pour les revendeurs qui disposent de catalogues volumineux.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des stratégies de sélection et des modèles de classement pour réorganiser les produits sur les pages de catégorie en fonction du profil et du comportement en temps réel de chaque visiteur. Il s’agit du modèle approprié lorsque la tâche classe un jeu de produits ouvert et volumineux à l’aide de signaux d’affinité comportementale ; la fonction Offer Decisioning n’est pas appropriée ici, car il n’existe aucune règle d’éligibilité ou contrainte métier limitant les produits qui apparaissent.

### Considérations techniques

- Le classement des produits doit s’exécuter suffisamment rapidement pour éviter les retards de chargement de page ; une personnalisation côté serveur ou une prise de décision basée sur les serveurs Edge est souvent nécessaire pour les pages de catégorie contenant des centaines de produits.
- La logique de personnalisation doit associer les préférences individuelles aux règles de marchandisage, afin de garantir que les produits mis en avant, les nouveaux arrivants et les articles saisonniers bénéficient toujours d’une visibilité appropriée.
- Une infrastructure de tests A/B doit être en place pour mesurer en permanence l’impact sur le chiffre d’affaires des règles de tri personnalisé par rapport aux règles de marchandisage par défaut.
- [!DNL Experience Platform] implémentation de Web SDK doit capturer les interactions de pages de catégories (profondeur de défilement, clics sur les produits, utilisation des filtres) afin d’affiner en permanence les modèles de classement.


## Campagnes De Suivi Après Achat

Envoyez des e-mails après achat avec des conseils d’assistance sur les produits, des suggestions de produits associées, des demandes de révision et des informations sur le programme de fidélité. La période immédiatement après un achat est celle où les clients sont le plus engagés avec la marque, ce qui en fait une fenêtre idéale pour approfondir la relation et encourager l&#39;activité future.

### Impact commercial

Des campagnes post-achat efficaces augmentent les taux de soumission de révisions et améliorent les taux d’achat répétés, transformant les acheteurs uniques en clients fidèles.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [Ce flux post-achat en plusieurs étapes utilise une logique d’embranchement pour adapter les messages de suivi en fonction du type de produit, du segment client et de l’engagement avec les e-mails précédents de la série. Il s’agit du modèle approprié, car le suivi s’étend sur plusieurs jours, dépend des événements de statut d’exécution et des branches en fonction de la catégorie de produits et des événements de retour. Un seul message déclenché ne peut pas prendre en charge la logique conditionnelle requise sur l’ensemble du calendrier post-achat.

### Considérations techniques

- Le parcours doit tenir compte de l’état d’exécution de la commande ; les conseils d’assistance et les demandes de révision ne doivent être envoyés qu’après la livraison du produit et non immédiatement après l’achat.
- Le contenu spécifique au produit (instructions d’entretien, guides d’utilisation, suggestions d’accessoires) nécessite un système de mappage de contenu qui associe chaque catégorie de produit à des documents de suivi pertinents.
- Le moment de la demande de révision doit être optimisé en fonction de la catégorie de produits ; l&#39;électronique peut nécessiter une période d&#39;utilisation plus longue avant une révision significative, tandis que les vêtements peuvent être examinés peu après la livraison.
- Les clients qui effectuent un retour ou un échange doivent être automatiquement supprimés du flux de post-achat standard et redirigés vers un chemin de récupération du service.


## Offres exclusives aux clients de VIP

Identifiez les clients à forte valeur ajoutée et proposez des offres exclusives, un accès anticipé aux ventes et des expériences d’achat personnalisées qui récompensent leur fidélité. Retenir les meilleurs clients est beaucoup plus rentable que d&#39;en acquérir de nouveaux et un traitement exclusif renforce la connexion émotionnelle qui les maintient à dépenser.

### Impact commercial

Les programmes VIP génèrent un engagement fort de la part des clients de premier plan et améliorent considérablement la valeur client tout au long de la durée de vie en réduisant l’attrition parmi les segments les plus rentables.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). [Cette approche associe l’orchestration des parcours à la prise de décision en temps réel pour la sélection des offres, ce qui permet de s’assurer que chaque client VIP reçoit l’offre exclusive la plus pertinente sur chaque canal. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion entre les canaux pour éviter les offres en double et lorsque la sélection d’offres nécessite des règles d’éligibilité et des contraintes métier - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire pour régir l’offre exclusive que chaque VIP reçoit.

### Considérations techniques

- Les critères de segmentation de VIP doivent être clairement définis à l’aide des mesures de récence, de fréquence et de valeur monétaire. De plus, les segments doivent être actualisés suffisamment fréquemment pour capturer les clients récemment qualifiés ou disqualifiés.
- Les offres exclusives doivent être appliquées au point de rachat (web, application, boutique) pour empêcher les clients non VIP d’y accéder, ce qui nécessite l’intégration aux systèmes de promotion et de tarification.
- Les préférences de canal varient considérablement entre les clients à forte valeur ajoutée. Certains préfèrent les e-mails, d’autres répondent aux notifications de l’application ou au publipostage direct. Le parcours doit donc adapter les canaux de diffusion en fonction des engagements passés.
- [!DNL Journey Optimizer] prise de décision doit se coordonner entre les canaux pour empêcher un client VIP de recevoir simultanément la même offre par e-mail, push et SMS.


## Notifications de rupture de stock

Permet aux clients de s’abonner à des notifications lorsque des produits en rupture de stock sont disponibles, puis de les avertir automatiquement par e-mail ou SMS. La capture de la demande pour des produits indisponibles empêche les ventes perdues et donne aux clients une raison de retourner au magasin plutôt que d&#39;acheter auprès d&#39;un concurrent.

### Impact commercial

Les notifications de retour en stock permettent d’atteindre des taux de conversion élevés parmi les abonnés et de réduire significativement les pertes de ventes pour les produits à forte demande qui font l’objet de ruptures de stock temporaires.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche des notifications sur les événements de retour en stock, comparant les mises à jour d’inventaire aux inscriptions aux notifications du client pour fournir des alertes en temps opportun. Il s’agit du modèle approprié, car le déclencheur est un événement de système d’inventaire discret, la diffusion est critique (l’inventaire peut à nouveau se vendre rapidement) et la communication est une notification unique plutôt qu’un parcours continu.

### Considérations techniques

- La surveillance des stocks doit détecter rapidement les événements de réapprovisionnement ; des retards, même de quelques heures, peuvent entraîner la revente du produit avant que les clients avisés aient la chance d&#39;acheter.
- Lorsqu’un produit populaire est réapprovisionné en quantité limitée, les notifications doivent être échelonnées ou hiérarchisées par date d’inscription afin d’éviter d’envoyer des alertes à plus de clients que le stock disponible ne peut en servir.
- Le mécanisme d’abonnement aux notifications doit capturer les préférences de canal (e-mail ou message texte) et respecter les exigences d’opt-in pour chaque canal, en particulier pour les SMS.
- [!DNL Real-Time Customer Data Platform] attributs de profil doivent effectuer le suivi des produits surveillés par chaque client afin d’éviter les notifications en double si le même produit fait l’objet de plusieurs réapprovisionnements.


## Personalization de l&#39;épreuve sociale

Affichez des épreuves de réseaux sociaux personnalisées, y compris des évaluations et des suggestions de type « Les clients qui ont acheté ceci ont également acheté », en fonction du profil et des préférences de chaque client. L’adaptation des épreuves sociales pour refléter les expériences de clients similaires permet de créer de la confiance plus efficacement que les évaluations génériques seules.

### Impact commercial

Les épreuves sociales personnalisées augmentent les taux de conversion et améliorent la confiance des acheteurs, en particulier pour les primo-accédants et les produits à prix plus élevés où l&#39;hésitation à l&#39;achat est la plus grande.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche personnalise le contenu web pour les visiteurs identifiés, en sélectionnant les avis les plus pertinents et les éléments de BAT des réseaux sociaux en fonction du profil, des préférences et du contexte de navigation du client. Il s’agit du modèle approprié lorsque la personnalisation est basée sur les attributs de profil et l’appartenance à un segment plutôt que sur un modèle d’affinité comportementale. La recommandation comportementale n’est pas appropriée ici, car la sélection de l’épreuve sociale dépend de la personne cliente, et non des éléments qu’elle a parcourus.

### Considérations techniques

- Les données de révision et d’évaluation doivent être structurées et balisées par attributs du client (tels que le contexte d’achat, le segment client et le cas d’utilisation de produit) afin de permettre un filtrage et une personnalisation significatifs.
- Les éléments d’épreuve des réseaux sociaux doivent se charger de manière asynchrone pour éviter de bloquer le rendu de la page produit principale, car les données de révision peuvent provenir d’une plateforme de révision tierce avec des temps de réponse variables.
- Les réglementations de confidentialité exigent que toutes les données client utilisées pour faire correspondre les avis aux visiteurs soient traitées en fonction des préférences de consentement. L’affichage de contenu « clients comme vous » implique un profilage qui peut nécessiter la divulgation.
- L&#39;adhésion à l&#39;audience [!DNL Experience Platform] peut être utilisée pour sélectionner les commentaires à mettre en évidence, montrant les commentaires des amateurs de plein air des acheteurs de plein air plutôt que les commentaires génériques les mieux notés.


## Conseillère produit AI

Les détaillants en ligne transportent des milliers de SKU sur des hiérarchies de catégories complexes, ce qui rend difficile pour les acheteurs de trouver le bon produit sans une navigation étendue ou des recherches abandonnées. Un conseiller en produits optimisé par l&#39;IA engage les acheteurs dans un dialogue naturel à plusieurs tours (en posant des questions admissibles sur les besoins, les préférences et le budget), puis restreint l&#39;assortiment à un ensemble organisé de recommandations personnalisées. L’expérience reflète les conseils qu’un associé expérimenté en magasin pourrait fournir, à l’échelle numérique.

### Impact commercial

Les détaillants qui utilisent la découverte conversationnelle guidée constatent une amélioration des taux de conversion et de la valeur moyenne des commandes par rapport à la navigation sans assistance, tout en réduisant le rendement des produits grâce à des décisions d&#39;achat mieux informées.

### Mise en œuvre

Utilisez le modèle [Expérience de conversation ](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Cette approche déploie Product Advisor Agent par rapport à un catalogue de produits structuré, en utilisant AEP Agent Orchestrator et des données de profil client en temps réel pour générer des recommandations de produits personnalisées et sécurisées par la marque grâce à un dialogue naturel. Il s’agit du modèle approprié lorsque l’objectif est une découverte conversationnelle interactive à plusieurs tours pilotée par les besoins exprimés par le client ou la cliente, et qui se distingue des messages déclenchés par un événement, qui sont unidirectionnels et réactifs à une action spécifique, ainsi que des expériences web personnalisées, qui affichent des recommandations de manière passive plutôt que d’engager la conversation avec les clientes et clients. Cela nécessite une configuration d’AEP Agent Orchestrator et de la gouvernance de marque.

### Considérations techniques

- Le catalogue de produits doit être structuré avec des données d’attributs riches (notamment la taille, le matériau, la compatibilité, la disponibilité et le prix), car Product Advisor Agent fonde les recommandations sur le contenu du catalogue et ne peut pas fournir de conseils fiables sur les produits avec des attributs incomplets.
- La recherche de profil client en temps réel via RT-CDP doit être configurée avec une activation Edge afin que l’historique d’achats, le comportement de navigation et les données de niveau de fidélité soient accessibles pendant la conversation en direct sans latence susceptible d’interrompre l’expérience.
- Des mécanismes de sécurisation de la gouvernance de marque doivent être définis pour spécifier la manière dont l’agent gère les articles en rupture de stock, les comparaisons de produits concurrentiels, les allégations de prix promotionnels et les sujets interdits, en veillant à ce que chaque réponse soit conforme aux normes de la marque de vente au détail.
- Les événements de conversation, notamment les signaux d’intention, les interactions de produits et l’acceptation des recommandations, doivent être capturés en tant qu’événements d’expérience XDM et diffusés en continu vers AEP, afin d’enrichir les profils clients avec des données d’affinité de produit qui améliorent la personnalisation future sur tous les canaux.


## Analyse de l’attribution cross-canal

Mesurez la manière dont chaque point de contact marketing (référencement payant, e-mail, réseaux sociaux et promotions en magasin) contribue aux conversions d’achat en ligne et hors ligne. Les détaillants qui s’appuient sur l’attribution Dernière touche sous-évaluent systématiquement les canaux upper-funnel et prennent des décisions d’allocation budgétaire basées sur une image incomplète du chemin d’achat.

### Impact commercial

Les équipes de marketing de vente au détail qui passent de l’attribution Dernière touche à l’attribution Multi-touche ont une vue plus claire des canaux qui génèrent l’intention d’achat, ce qui permet de prendre des décisions de budget plus éclairées et d’améliorer le retour sur investissement des dépenses marketing.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Cette approche connecte les données d’événement en ligne et hors ligne (clics web, engagements par e-mail, transactions de fidélité et enregistrements de point de vente) à Customer Journey Analytics, où les modèles d’attribution peuvent être configurés et comparés sur l’ensemble du chemin d’achat. Il s’agit du modèle approprié lorsque l’objectif est de mesurer et de générer insight sur un parcours multicanal complexe, plutôt que d’activer des audiences ou de déclencher des messages, et lorsque l’analyse nécessite Customer Journey Analytics plutôt qu’un CDP ou un outil d’orchestration de campagnes.

### Considérations techniques

- Les données des transactions de point de vente et d’e-commerce doivent partager un identifiant client cohérent afin que les conversions en magasin et en ligne puissent être regroupées en une seule vue cross-canal dans CJA.
- Plusieurs modèles d’attribution (première touche, dernière touche, linéaire et atténuation temporelle) doivent être configurés dans la vue de données CJA afin que les analystes puissent les comparer côte à côte sans reconstruire l’analyse.
- Les données d’impressions et de clics de médias payants provenant de plateformes publicitaires externes doivent être ingérées par le biais de connecteurs source ou de chargements par lots pour inclure les canaux payants dans le chemin d’attribution avec les canaux propriétaires.
- Les fenêtres de conversion et les périodes de recherche en amont de crédit doivent être définies par type de canal, car la fenêtre d’attribution appropriée pour un clic de référencement payant diffère considérablement de celle d’une campagne par e-mail saisonnière.

## Segmentation et activation de l’audience pour les médias payants

Créez des segments d’audience à forte valeur ajoutée à partir de profils clients unifiés et activez-les sur les destinations de médias achetés telles que Google Ads, Meta et The Trade Desk pour les campagnes d’acquisition et de reciblage. L’unification des données comportementales, transactionnelles et de fidélité permet un ciblage plus précis qui réduit le gaspillage et les dépenses publicitaires et améliore le retour sur investissement de la campagne.

### Impact commercial

Les détaillants qui activent des audiences propriétaires de grande qualité constatent une amélioration des taux de correspondance sur les plateformes de médias payants, une réduction du coût par acquisition et un meilleur rendement sur les dépenses publicitaires par rapport à leur dépendance à l&#39;égard de segments tiers.

### Mise en œuvre

Utilisez le modèle [Audience Activation vers les destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) pour évaluer l’appartenance à l’audience par rapport aux profils unifiés et publier des segments vers des destinations de médias achetés connectées sur une base planifiée ou par diffusion en continu. Il s’agit du modèle approprié lorsque l’exigence principale est la publication de segments dans des systèmes externes plutôt que la messagerie orchestrée ou la prise de décision en temps réel.

### Considérations techniques

- La résolution d’identité sur le web, les appareils mobiles et les données de fidélité est nécessaire pour créer des profils clients complets avant l’activation : les profils fragmentés réduisent la qualité de l’audience et les taux de correspondance.
- Les connecteurs de destination doivent être configurés pour chaque plateforme de médias achetés, avec les indicateurs de consentement appropriés respectés au niveau du profil pour empêcher l’activation des données non consenties.
- La fréquence d’actualisation des segments doit correspondre aux objectifs de la campagne. Les audiences d’acquisition peuvent nécessiter des actualisations quotidiennes, tandis que les audiences de reciblage bénéficient de mises à jour en temps quasi réel pour exclure les acheteurs récents.
- L’analyse des chevauchements entre les audiences d’acquisition et de rétention permet d’éviter toute contamination croisée lorsque les clients existants reçoivent des messages d’acquisition de nouveaux clients.


## Suppression de clients pour les campagnes d’acquisition

Supprimez les clients existants et les convertisseurs récents de l’acquisition et des dépenses en activant les audiences d’exclusion vers des destinations de médias payants, ce qui réduit les dépenses inutiles. La synchronisation continue des listes de suppression garantit que les budgets payés ciblent les nouveaux prospects nets plutôt que les personnes qui ont déjà converti ou qui sont activement engagées.

### Impact commercial

La suppression des clients existants des campagnes d’acquisition réduit les dépenses de médias payantes gaspillées, améliore les mesures de coût par acquisition et empêche les clients existants de recevoir des messages qui ne sont pas pertinents à leur étape de relation.

### Mise en œuvre

Utilisez le modèle [Audience Activation vers les destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) pour publier fréquemment des audiences d’exclusion (acheteurs récents, abonnés actifs, clients à forte valeur ajoutée) vers chaque destination de médias achetés. Il s’agit du modèle approprié lorsque l’objectif est la publication de segments pour la suppression plutôt que d’orchestrer un parcours face au client.

### Considérations techniques

- Les audiences de suppression nécessitent une définition claire de qui exclure - généralement les clients qui ont acheté au cours des 30 à 90 derniers jours, les membres actifs du programme de fidélité et les conversions récentes d’e-mails.
- Les listes d’exclusion doivent être actualisées suffisamment fréquemment pour exclure les acheteurs avant la diffusion des publicités. Les listes de suppression obsolètes provoquent le plus de friction sur la marque dans les périodes de vente au détail à volume élevé.
- La qualité de la correspondance des identités affecte directement la précision de suppression. Une mauvaise correspondance des e-mails ou des identifiants d’appareil entraîne toujours la diffusion des annonces d’acquisition par les clients existants.
- Assurez-vous que les audiences de suppression sont distinctes des audiences de rétention, de sorte que les campagnes de reconquête puissent toujours atteindre les clients obsolètes qui ne doivent pas être supprimés.


## Expériences web personnalisées pour les visiteurs et visiteuses connus

Diffusez des bannières principales personnalisées, des recommandations de produits et du contenu promotionnel aux visiteurs authentifiés du site en fonction de leur profil en temps réel, de leur appartenance à un segment et de leur historique comportemental. Lorsque les clients récurrents voient des expériences personnalisées en fonction de leur statut de fidélité, de leur historique d’achat et de leurs préférences, les taux d’engagement et de conversion s’améliorent considérablement par rapport aux expériences de page d’accueil générique.

### Impact commercial

Les détaillants qui effectuent des personnalisations pour des visiteurs connus constatent une amélioration significative des mesures d’engagement, notamment le temps passé sur le site, les pages par session et le taux de conversion, avec le plus grand impact sur les membres du programme de fidélité qui visitent fréquemment.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour offrir des expériences personnalisées basées sur les profils au chargement de la page à l’aide de l’appartenance à un segment en temps réel et des attributs de profil. Il s’agit du modèle approprié lorsque l’expérience doit être pilotée par des données de profil liées à l’identité plutôt que par des signaux de session uniquement, et lorsque les décisions de contenu ne nécessitent pas de classement d’offre complexe ou de contraintes commerciales.

### Considérations techniques

- L’authentification doit se produire avant l’activation de la personnalisation pilotée par les profils. Le site web a besoin d’un mécanisme pour identifier le visiteur et résoudre son ECID sur un profil connu.
- Les recherches de profils en temps réel doivent être effectuées dans les limites du budget de latence du chargement de page, nécessitant généralement une évaluation des profils déployés Edge plutôt que des appels d’API côté serveur sur le chemin de rendu critique.
- Les variations de contenu doivent être conçues pour tous les segments d’audience qui seront ciblés, y compris une expérience par défaut pour les visiteurs qui ne correspondent à aucune règle de personnalisation.
- Les décisions Personalization doivent être consignées pour analyse, ce qui permet de tester A/B les variations de contenu et d’attribuer les améliorations de l’engagement à des segments spécifiques.


## Personalization Web de visiteur anonyme

Personnalisez le contenu pour les visiteurs et visiteuses non identifiés du site Web à l’aide de signaux comportementaux en session, tels que les pages consultées, les catégories de produits parcourues et la source de référence. Comme la majorité du trafic web de vente au détail est anonyme, la personnalisation pour les visiteurs non reconnus étend considérablement la portée de la personnalisation sur site au-delà du segment authentifié.

### Impact commercial

Les détaillants qui proposent des expériences personnalisées aux visiteurs anonymes constatent une amélioration des taux d’engagement et de conversion lors de la première visite, avec un impact particulièrement fort sur les visiteurs provenant de sources de campagne spécifiques ou qui parcourent des pages de catégorie à forte intention.

### Mise en œuvre

Utilisez le modèle Personalization Web de visiteur anonyme](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) pour évaluer les signaux comportementaux en session à la périphérie et diffuser des variations de contenu pertinentes sans nécessiter d’authentification. [Il s’agit du modèle approprié lorsque la personnalisation doit fonctionner immédiatement à partir de la première interaction sans dépendre d’un profil persistant, en particulier pour le trafic d’acquisition et les visiteurs qui ne se sont pas encore connectés.

### Considérations techniques

- La personnalisation en session repose sur les données d’événement de diffusion en continu collectées via Edge Network. Les règles d’évaluation Edge doivent être déployées et testées avant que le trafic ne leur soit envoyé.
- Les variations de contenu doivent être conçues autour de comportements en session à signal élevé (source de référence, première page vue, catégorie de produits explorée), plutôt que d’attributs à signal faible qui ne prédisent pas de manière fiable l’intention.
- Les exigences en matière de confidentialité doivent être évaluées avec soin. Certaines juridictions traitent la personnalisation comportementale comme nécessitant le consentement même des visiteurs anonymes.
- Les règles de Personalization pour les visiteurs anonymes doivent être plus simples et plus rapides à évaluer que les règles de visiteurs connus, car les contraintes de latence Edge sont plus strictes.


## Parcours de la série de bienvenue

Orchestrez un parcours de bienvenue en plusieurs étapes pour les nouveaux clients enregistrés, en proposant du contenu d’intégration, une formation sur les produits et un incentives pour le premier achat sur les canaux e-mail et de notification push. Une série de bienvenue bien conçue donne le ton à la relation client et augmente considérablement la probabilité qu&#39;un nouvel inscrit se convertisse à son premier achat.

### Impact commercial

Les programmes de la série de bienvenue entraînent des améliorations significatives des taux d’activation des nouveaux clients et de conversion lors du premier achat, avec le plus grand impact lorsque la série associe un contenu éducatif à un incitatif personnalisé et envoyé en temps opportun.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour concevoir une séquence d’intégration de plusieurs jours avec des étapes d’attente, l’embranchement des canaux en fonction de l’engagement et la suppression lorsque le premier objectif d’achat est atteint. [Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux de communication séquencé et espacé dans le temps avec une logique conditionnelle. Un seul message déclenché est insuffisant pour guider un nouveau client tout au long de l’expérience d’intégration.

### Considérations techniques

- L’entrée de parcours doit être déclenchée par des événements d’enregistrement de compte en temps réel afin que le premier message de bienvenue arrive rapidement lorsque l’intention d’enregistrement est élevée.
- Le parcours doit inclure des conditions de sortie qui suppriment les messages restants lorsqu’un nouveau client effectue son premier achat : la poursuite de la série de bienvenue après l’achat sape la pertinence du message.
- Les préférences de canal doivent être respectées dans . Les étapes de notification push nécessitent l’installation d’applications et l’inclusion push, avec une solution de secours pour les e-mails des clients sans inclusion.
- Personalization dans la série de bienvenue améliore la conversion, mais nécessite suffisamment de données de profil pour être significatif ; les nouveaux profils ont souvent besoin d’une solution de secours pour les produits les plus vendus ou les plus en vogue.


## Récupération de l’abandon de panier

Déclenchez des e-mails et des notifications push en temps réel lorsqu’un client abandonne son panier, avec des rappels de produit personnalisés et des incentives limités dans le temps pour terminer l’achat. L’abandon de panier est l’un des cas d’utilisation les plus rentables de la vente au détail, récupérant des recettes auprès de clients qui ont déjà démontré une forte intention d’achat.

### Impact commercial

Les programmes d’abandon de panier bien exécutés récupèrent une part significative des recettes abandonnées, les taux de récupération étant les plus élevés lorsque le premier message arrive dans l’heure suivant l’abandon et inclut les articles exacts laissés dans le panier.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour répondre à l’événement d’abandon de panier par une communication déclenchée immédiatement pendant que le plan d’achat est toujours actif. Il s’agit du modèle approprié lorsqu’une action client discrète est le déclencheur et que l’exigence principale est une réponse personnalisée en temps opportun, plutôt qu’une séquence de maturation de plusieurs semaines ou une prise de décision d’offre complexe avec des contraintes commerciales.

### Considérations techniques

- La détection d’abandon de panier nécessite un seuil d’inactivité défini (généralement entre 30 et 60 minutes) pour éviter d’envoyer des messages aux clients qui parcourent ou terminent toujours activement le flux de passage en caisse.
- Le contenu de l’e-mail doit générer dynamiquement les images, les prix et l’état des stocks du produit au moment de l’envoi, car les articles peuvent être vendus ou leur prix peut changer entre l’abandon et la diffusion du message.
- La logique de suppression doit exclure les clients qui ont effectué leur achat par un autre canal entre la détection d&#39;abandon et l&#39;envoi du message.
- Les règles de limitation de la fréquence doivent empêcher la répétition des messages d’abandon de panier dans des fenêtres courtes, en particulier pour les clients qui abandonnent généralement leur panier en raison de leur comportement de navigation.


## Parcours d’engagement après achat

Diffusez des communications après achat, notamment la confirmation de commande, les mises à jour d’expédition, les recommandations de ventes croisées et les demandes d’examen par le biais d’un parcours orchestré en plusieurs étapes. La fenêtre de post-achat est l’un des moments les plus chargés d’engagement du cycle de vie du client, ce qui en fait un moment idéal pour fidéliser les clients et leur présenter des produits complémentaires adaptés.

### Impact commercial

Les détaillants disposant de parcours post-achat structurés constatent une amélioration des taux d’achat répétés et des taux de soumission d’avis clients, ce qui contribue à la fidélité à long terme et à la preuve sociale en faveur d’acquisitions futures.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour orchestrer une séquence de communications après achat programmées selon des jalons clés : confirmation de commande, expédition, livraison et suivi après livraison. [Il s’agit du modèle approprié lorsque le cas d’utilisation s’étend sur plusieurs jours avec plusieurs objectifs : un seul message déclenché ne peut pas s’adapter au processus allant de la confirmation transactionnelle à la création de fidélité, en passant par la révision de la sollicitation.

### Considérations techniques

- L’intégration du système de gestion des commandes est nécessaire pour recevoir en temps réel les événements d’achat et d’expédition. Les retards d’ingestion des événements créent des délais inconfortables dans les communications après achat.
- Les recommandations de ventes croisées dans la séquence après achat nécessitent des données de catalogue de produits en temps réel et une inférence de modèle de recommandation au moment du rendu du message pour refléter le stock et la tarification actuels.
- Les messages de demande de révision doivent être conformes aux conditions d’utilisation de la plateforme pour les révisions incitées et doivent être programmés une fois que le client a eu suffisamment de temps pour utiliser le produit.
- La coordination des canaux est importante : les clients ne doivent pas recevoir à la fois des e-mails et des notifications push pour le même jalon, sauf s’ils ont interagi avec le premier canal.


## Campagne de mise à niveau du niveau de fidélité

Identifiez les clients approchant les seuils de fidélité et diffusez des campagnes ciblées les encourageant à atteindre le niveau suivant avec des offres personnalisées basées sur l’historique d’achat et les préférences. Lorsque les clients sont à portée de main d’une mise à niveau de niveau, des messages ciblés avec des incentives personnalisés créent une urgence et favorisent un comportement d’achat incrémentiel.

### Impact commercial

Les campagnes de mise à niveau du niveau de fidélité augmentent le volume des achats incrémentiels et améliorent l’engagement du programme, avec le plus fort impact parmi les membres de niveau intermédiaire qui se rapprochent du seuil suivant et qui ont montré une activité d’achat récente.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer une campagne de proximité au niveau qui rejoint les clients lorsqu&#39;ils atteignent un seuil de dépenses défini sous leur niveau suivant et les guide à travers une séquence de messages d&#39;avantages et d&#39;offres d&#39;incentives. [Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite de surveiller un attribut de profil calculé au fil du temps et d’orchestrer une campagne à plusieurs étapes liée à la progression du client ou de la cliente vers un objectif.

### Considérations techniques

- Les données de la plateforme de fidélité (solde de points, statut de niveau, seuils de niveau) doivent être ingérées et tenues à jour dans le profil client afin que les calculs de proximité du niveau soient précis.
- Les campagnes de mise à niveau de niveau doivent être supprimées pour les clients qui ont déjà atteint le niveau cible ou dont le statut de fidélité a changé depuis l’entrée dans la campagne.
- Les incentives personnalisés dans la campagne de mise à niveau doivent être limités aux offres auxquelles le client est véritablement éligible et qui ne sapent pas la valeur perçue de la structure de niveau.
- La campagne doit inclure des conditions de sortie claires pour les clients qui terminent leur mise à niveau de niveau en milieu de parcours, en passant à un message de félicitations plutôt qu’en poursuivant la séquence de persuasion.


## Orchestration de campagnes cross-canal

Orchestrez des campagnes marketing coordonnées sur les canaux e-mail, SMS, notification push et web avec l’embranchement par parcours, les étapes d’attente et le capping de la fréquence pour optimiser l’engagement sans fatigue. Une orchestration cross-canal coordonnée garantit que les clients reçoivent une expérience de campagne cohérente, quel que soit le canal auquel ils répondent en premier, ce qui élimine les messages en double et les offres en conflit.

### Impact commercial

Les détaillants disposant de fonctionnalités d’orchestration cross-canal enregistrent des taux d’engagement et de conversion de campagne plus élevés que les campagnes à canal unique, tout en réduisant les taux de désabonnement liés à la fatigue du canal due à des messages non coordonnés.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour créer des campagnes qui acheminent les clients par le biais de séquences de canal personnalisées en fonction de leur historique d’engagement, de leurs préférences de canal et de signaux de réponse en temps réel. [Il s’agit du modèle approprié lorsque la campagne nécessite une sélection d’offres régie, un routage des préférences de canal et un embranchement dynamique basé sur l’engagement en parcours, plutôt qu’une séquence fixe envoyée à tous les destinataires de la campagne.

### Considérations techniques

- Les limitations de fréquence globales doivent être configurées sur tous les canaux pour empêcher les clients de recevoir des communications excessives lorsque plusieurs parcours sont exécutés simultanément.
- Les données de préférence de canal doivent être à jour et exploitables. Les profils de préférence obsolètes depuis plusieurs mois achemineront les clients vers les canaux avec lesquels ils n’interagissent plus.
- La logique d’orchestration des parcours doit gérer la rentrée de manière élégante, en empêchant les clients de rejoindre deux fois la même campagne tout en s’assurant qu’ils ne sont pas exclus de véritables nouvelles campagnes.
- Les signaux d’engagement en temps réel (ouvertures d’e-mails, clics sur les liens, sessions web) doivent être renvoyés au parcours pour permettre le changement de canal et la sortie anticipée pour les clients qui ont déjà converti.


## Expérience de conversation Brand Concierge

Déployez un agent conversationnel sécurisé basé sur l’IA sur les propriétés numériques pour fournir des conseils personnalisés sur les produits, une aide à la navigation sur le site et une remise transparente aux agents en direct. Un concierge IA sur site offre un service personnalisé à grande échelle, aidant les acheteurs à découvrir des produits, à comparer des options et à effectuer des achats sans nécessiter l&#39;intervention d&#39;un agent humain pour les requêtes courantes.

### Impact commercial

Les détaillants disposant de capacités de conciergerie IA signalent une amélioration des taux de résolution en libre-service, une réduction du volume d’assistance entrante pour les questions sur le produit et la navigation, et une conversion plus élevée parmi les clients qui utilisent des conseils de conversation avant l’achat.

### Mise en œuvre

Utilisez le modèle [Expérience de conversation ](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md) pour déployer un agent d’IA régi basé sur les données de catalogue de produits, les directives de marque et le contexte du profil client en temps réel. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite une interaction en langage naturel sur un ensemble de produits dynamique volumineux, plutôt qu’un chatbot scripté avec des intentions fixes ou un modèle correspondant à un canal spécifique comme l’e-mail.

### Considérations techniques

- L’agent d’IA doit être fondé sur les données actuelles du catalogue de produits, notamment les descriptions, les spécifications, la disponibilité et les prix, pour fournir des conseils précis. Les données obsolètes des produits donnent lieu à des recommandations incorrectes.
- Les mécanismes de sécurisation de la marque doivent être configurés pour empêcher l’agent de discuter des produits concurrents, de prendre des engagements de prix entrant en conflit avec des promotions ou de répondre à des requêtes hors sujet.
- La logique de remise aux agents actifs nécessite une intégration à la plateforme de service et doit être déclenchée lorsque l’agent d’IA ne peut pas résoudre la requête du client après un nombre défini de tours.
- L’intégration des données de profil permet à l’agent de personnaliser les réponses en fonction de l’historique des achats et du statut de fidélité, mais cela nécessite la résolution de l’identité avant le début de la session de conversation.

## Rappel d’enregistrement avec App Download CTA

Rappelez-leur de s&#39;enregistrer et encouragez-les à télécharger l&#39;application afin d&#39;accéder facilement aux informations. Des rappels d’enregistrement en temps voulu associés à des invites de téléchargement d’application encouragent l’engagement mobile et permettent d’offrir des expériences plus riches sur site.

### Impact commercial

Les détaillants qui combinent les rappels d&#39;enregistrement avec les appels à l&#39;action de téléchargement d&#39;application constatent une augmentation des taux d&#39;adoption des applications et une plus grande interaction en magasin, car les clients qui utilisent l&#39;application mobile ont tendance à interagir plus fréquemment avec les promotions et le contenu du lieu.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour déclencher un rappel d’enregistrement avec le CTA de téléchargement d’application en fonction des données de présence à l’événement ou de réservation. Il s’agit du modèle approprié lorsqu’un seul message opportun doit être envoyé en réponse à un événement ou à un déclencheur de planning connu.

### Considérations techniques

- Les rappels d&#39;enregistrement doivent être programmés en fonction de l&#39;événement ou de la date de visite afin de maximiser l&#39;engagement sans être perçus comme trop tôt ou trop tard.
- Les liens profonds de téléchargement d’application doivent être acheminés vers la boutique d’applications appropriée en fonction de la plateforme de l’appareil du client (iOS ou Android).
- Les clients pour lesquels l’application est déjà installée doivent recevoir une autre variante de message qui ignore le CTA de téléchargement et se concentre sur la fonctionnalité d’enregistrement.

## Campagnes d&#39;anniversaire pour les fans

Ciblez les fans le jour de leur anniversaire avec un message d’anniversaire personnalisé et une offre exclusive. Les campagnes d’anniversaire créent des liens émotionnels avec les fans et génèrent des achats incrémentiels par le biais d’une sensibilisation personnalisée et opportune.

### Impact commercial

Les campagnes d’anniversaire offrent systématiquement des taux d’ouverture et de conversion supérieurs à la moyenne, car elles arrivent à un moment d’importance personnelle, ce qui crée de la bonne volonté et encourage les fans à se traiter avec un achat spécial.

### Mise en œuvre

Utilisez le modèle [Message d’anniversaire déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer un message d’anniversaire personnalisé à la date d’anniversaire du client. Il s’agit du modèle approprié lorsqu’un seul message piloté par un événement est envoyé en fonction d’un déclencheur de date d’attribut de profil.

### Considérations techniques

- La date d’anniversaire doit être capturée dans le profil client et validée afin d’éviter d’envoyer des messages à des dates incorrectes.
- Les offres doivent avoir une période de validité définie (par exemple, la semaine d’anniversaire) pour créer une urgence tout en donnant aux clients un délai raisonnable pour les échanger.
- Les fans dont l&#39;anniversaire n&#39;est pas enregistré doivent être exclus de la campagne plutôt que de recevoir un message générique.

## Campagnes d’anniversaire pour les acheteurs

Ciblez les acheteurs le jour de leur anniversaire avec un message d’anniversaire personnalisé et une offre exclusive. Les campagnes d’anniversaire renforcent la fidélité à la marque en reconnaissant personnellement les clients et en encourageant un achat festif.

### Impact commercial

Les offres d’anniversaire personnalisées génèrent des taux d’échange plus élevés que les promotions génériques, car elles s’alignent sur un moment où les acheteurs sont déjà enclins à effectuer des achats discrétionnaires pour eux-mêmes.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour déclencher un message d’anniversaire et une offre en fonction de l’attribut de profil de date de naissance de l’acheteur. Il s’agit du modèle approprié lorsqu’un seul message personnalisé doit être diffusé à une date de calendrier spécifique liée au profil client.

### Considérations techniques

- La date d’anniversaire doit être stockée en tant qu’attribut de profil et doit être collectée lors de l’enregistrement ou de l’inscription au programme de fidélité.
- La personnalisation de l’offre doit tenir compte de l’historique des achats et des préférences de l’acheteur pour présenter des suggestions de produits pertinentes avec la remise d’anniversaire.
- Une logique de suppression en double est nécessaire pour les clients qui apparaissent dans plusieurs systèmes afin d’éviter d’envoyer plusieurs messages d’anniversaire.

## Campagnes de promotion de la journée de jeu

Ciblez les fans pour acheter des billets pour un jeu à venir avec des promotions et des offres personnalisées. Les promotions de jour de jeu stimulent les ventes de billets en atteignant la bonne audience avec une messagerie opportune et spécifique à l&#39;événement.

### Impact commercial

Les promotions ciblées de la journée de jeu améliorent les taux de vente des billets en rejoignant les fans avec des offres pertinentes basées sur les préférences de leur équipe, leur présence passée et la proximité du lieu.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pour envoyer des messages promotionnels aux audiences de fans segmentées avant les jeux à venir. Il s’agit du modèle approprié lorsqu’un lot de messages personnalisés doit être envoyé à un segment d’audience préconfiguré selon un calendrier précis.

### Considérations techniques

- Les données de planning des parties doivent être intégrées pour déclencher des promotions au bon moment avant chaque événement.
- La segmentation de l’audience doit tenir compte de l’affinité de l’équipe, de la proximité géographique et des schémas de fréquentation passés pour maximiser la pertinence.
- Les clients qui ont déjà acheté des billets pour le jeu promu doivent être supprimés des messages d’acquisition et peuvent plutôt recevoir des offres de mise à niveau ou des modules complémentaires.

## Campagnes de promotion de produit

Ciblez les acheteurs pour qu’ils achètent des produits au cours d’une campagne de promotion continue. Les campagnes promotionnelles génèrent des recettes en connectant les bons clients aux offres opportunes alignées sur les promotions actives.

### Impact commercial

Les campagnes de promotion de produits ciblées surpassent les promotions à large portée en se concentrant sur les acheteurs les plus susceptibles de convertir, en réduisant le gaspillage promotionnel et en améliorant le retour sur les dépenses marketing.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pour envoyer des messages promotionnels à des segments d’audience qualifiés pendant les fenêtres de campagne actives. Il s’agit du modèle approprié lorsqu’un lot planifié de messages promotionnels personnalisés doit atteindre une audience définie au cours d’une campagne limitée dans le temps.

### Considérations techniques

- Les dates de début et de fin de la promotion doivent être gérées pour vous assurer que les messages ne sont envoyés que pendant la fenêtre de promotion active.
- La segmentation de l’audience doit exploiter l’historique d’achat, le comportement de navigation et l’affinité du produit pour cibler les acheteurs les plus susceptibles d’interagir avec les produits promus.
- Le capping de la fréquence doit être appliqué pour éviter la lassitude des promotions, en particulier lorsque plusieurs campagnes s’exécutent simultanément.

## Abandon de panier

Réengagez les clients qui abandonnent leur panier avec des rappels personnalisés et des incentives pour terminer l’achat. La récupération après abandon de panier est l’un des cas d’utilisation les plus rentables du marketing de détail.

### Impact commercial

Les campagnes de récupération après abandon de panier récupèrent un pourcentage significatif du chiffre d’affaires perdu en réengageant les acheteurs au moment où l’intention d’achat est la plus élevée, avec des rappels et des incitations personnalisés.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour déclencher un message de récupération lorsqu’un événement d’abandon de panier est détecté. Il s’agit du modèle approprié lorsqu’un seul message en temps réel doit être envoyé en réponse à un événement comportemental, tel que laisser des articles dans le panier sans terminer le passage en caisse.

### Considérations techniques

- La détection de l’abandon de panier nécessite un seuil d’inactivité défini (généralement entre 30 et 60 minutes) pour distinguer l’abandon réel des clients qui parcourent toujours le site.
- Le contenu du panier doit être transmis dans la payload d’événement pour activer les rappels de produit personnalisés dans le message de récupération.
- Les clients qui effectuent leur achat entre l’événement d’abandon et l’envoi du message doivent être supprimés pour éviter les messages non pertinents.
