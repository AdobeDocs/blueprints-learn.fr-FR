---
title: Cas d’utilisation d’assurance
description: Découvrez comment les compagnies d’assurance utilisent Adobe Experience Platform pour personnaliser la gestion des polices, améliorer l’expérience des sinistres et stimuler la fidélisation des clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a082598f-555b-49a4-b201-a55bee793959
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3272'
ht-degree: 0%

---

# Cas d’utilisation d’assurance

Les compagnies d’assurance utilisent Adobe Experience Platform pour unifier les données des titulaires de police dans les systèmes de gestion des polices, de sinistres et d’engagement afin de fournir des communications personnalisées à chaque étape de la relation client. En associant les signaux comportementaux aux informations sur les polices et les sinistres, les assureurs peuvent interagir de manière proactive avec les clients au moyen d&#39;offres pertinentes, de mises à jour de service opportunes et d&#39;un support significatif qui stimule la rétention et la valeur de la durée de vie.

## Campagnes De Renouvellement De Politique

Envoyez des rappels et des offres personnalisés sur le renouvellement des polices en fonction de l’historique des polices, des enregistrements de réclamations et des préférences de couverture de chaque client. Des activités de sensibilisation au renouvellement pertinentes et opportunes réduisent les taux d’expiration des polices et renforcent les relations à long terme avec les clients en permettant aux assurés de comprendre facilement leurs options et de prendre des mesures.

### Impact commercial

Les entreprises qui mettent en œuvre des campagnes de renouvellement de politique personnalisées bénéficient de taux de renouvellement améliorés, ce qui réduit directement l’attrition des clients et protège les recettes de primes récurrentes.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Cette approche crée une séquence de renouvellement temporelle qui progresse à partir de l’avis initial par le biais de rappels progressifs et, si nécessaire, d’un message d’urgence final, en adaptant le rythme et l’offre selon que le titulaire de la police a consulté ou non des contacts précédents. Il s’agit du modèle approprié lorsque le minutage est déterminé par une date de contrat plutôt que par un événement client discret et que l’intention commerciale nécessite un flux séquentiel de plusieurs messages sur 30 jours ou plus avec un embranchement conditionnel basé sur l’engagement ; la messagerie déclenchée par un événement gère les réponses réactives aux événements discrets, mais ne peut pas s’adapter à la logique de planification basée sur le calendrier ou aux dépendances de réaffectation requises pour une campagne de renouvellement.

### Considérations techniques

- Intégrez-la au système de gestion des politiques pour recevoir les événements de date de renouvellement et les détails de la politique actuelle, en veillant à ce que les messages reflètent une couverture exacte et des informations de prime.
- Appliquez des étiquettes de gouvernance des données à toutes les données de police financière et d’identification personnelle pour vous conformer aux réglementations d’assurance de l’État et aux exigences de confidentialité des données.
- Configurez les règles de suppression pour empêcher l’envoi de messages de renouvellement aux souscripteurs qui ont déjà renouvelé leur contrat ou dont les réclamations actives peuvent affecter leurs conditions de renouvellement.
- Coordonnez le timing avec les affectations d’agent ou de courtier afin que les messages directs au client correspondent à toute sensibilisation que l’agent affecté peut également mener.


## Recommandations de produits de ventes croisées

Recommandez des produits d’assurance supplémentaires tels que la couverture vie, habitation ou automobile en fonction des polices existantes, du stade de vie et du profil de risque de chaque client. Des recommandations de produits personnalisées aident les assurés à découvrir les lacunes de couverture et à créer un portefeuille de protection plus complet.

### Impact commercial

Les recommandations personnalisées de ventes croisées entraînent une amélioration des taux de conversion de ventes croisées, ce qui augmente les politiques par foyer et la valeur globale de la durée de vie du client.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). La prise de décision en temps réel évalue la couverture existante, l’étape de vie et les signaux comportementaux de chaque client afin de sélectionner la recommandation de produit la plus pertinente dans le catalogue disponible. C&#39;est le bon modèle lorsque la sélection d&#39;un produit doit tenir compte des règles d&#39;éligibilité, des directives de souscription et des exigences d&#39;adéquation réglementaires - des contraintes qui nécessitent une logique de prise de décision régie plutôt qu&#39;un classement par affinité comportementale seul.

### Considérations techniques

- Intégrer les données de politique de toutes les lignes de produits dans un profil client unifié afin que le moteur de décision ait une vue complète de la couverture existante lors de la sélection de recommandations.
- Configurez les règles d’éligibilité dans le modèle de prise de décision afin d’exclure les produits qu’un client possède déjà ou qui sont en conflit avec les directives de souscription pour leur profil de risque.
- Demandez à vos équipes juridiques et de conformité de vérifier que les règles d’éligibilité des recommandations de produits s’alignent sur les exigences de marketing et d’adéquation de l’assurance publique applicables avant la mise en ligne.
- Coordonnez la sortie de prise de décision avec le portail d’agents afin que les produits recommandés soient visibles pour les agents affectés qui peuvent avoir des conversations directes avec le client.


## Personalization du processus de réclamation

Personnalisez les communications relatives au traitement des demandes, les mises à jour de statut et les ressources d’assistance en fonction du type de demande, des préférences du client et de l’historique des demandes. Une expérience de sinistres transparente et bien communiquée réduit l&#39;anxiété pendant les moments stressants et établit une confiance durable avec les souscripteurs.

### Impact commercial

Les communications personnalisées des réclamations permettent d&#39;obtenir de meilleurs scores de satisfaction des réclamations, de réduire les plaintes et de renforcer la probabilité de renouvellement de la politique après une réclamation.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Le processus de réclamation est une expérience en plusieurs étapes comportant des phases distinctes — dépôt, enquête, rajustement et règlement — qui nécessitent chacune des communications adaptées et un calendrier adaptatif. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur les événements de statut de revendication. Un message déclenché unique ne peut pas s’adapter à la logique de dépendance entre les phases de revendications séquentielles.

### Considérations techniques

- Intégrez-la au système de gestion des réclamations afin de recevoir des événements de changement de statut en temps réel qui font progresser le client tout au long de l’étape de parcours appropriée.
- Concevez une logique d’embranchement du parcours qui adapte le ton et le contenu des messages en fonction du type de réclamation, comme les réclamations pour collision automatique ou pour dommages matériels ou les réclamations en responsabilité.
- Implémentez des règles de suppression lors des enquêtes sur les réclamations actives afin d’empêcher les messages de marketing ou de vente croisée d’atteindre les clients aux moments sensibles.
- Assurez-vous que toutes les données liées aux réclamations qui entrent dans le profil client sont étiquetées avec des restrictions de gouvernance des données appropriées pour empêcher leur utilisation en dehors des communications de service.


## Évaluation et prévention des risques

Fournissez des informations d&#39;évaluation des risques et des conseils de prévention personnalisés en fonction du type de politique, de l&#39;emplacement géographique et des facteurs de risque spécifiques de chaque client. Une formation proactive sur les risques aide les assurés à réduire leur exposition aux pertes, ce qui profite à la fois au client et à l’assureur.

### Impact commercial

La sensibilisation personnalisée à la prévention des risques améliore l’engagement en matière de prévention, ce qui contribue à réduire la fréquence des réclamations et à améliorer la satisfaction des clients.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’éducation à la prévention des risques est plus efficace sous la forme d’un parcours multipoint soutenu qui fournit des conseils pertinents au fil du temps et s’adapte en fonction de l’engagement des clients et des facteurs de risque saisonniers. Il s’agit du modèle approprié lorsque le parcours doit diffuser du contenu sur de longues périodes avec des ajustements de durée saisonniers et un embranchement basé sur l’engagement : les messages déclenchés par un événement ne peuvent pas gérer la planification prédictive ou la cadence à plusieurs étapes nécessaire à une formation continue.

### Considérations techniques

- Intégrez-la à des fournisseurs de données tiers sur les risques pour obtenir des informations sur les conditions météorologiques, les dangers géographiques et les risques liés aux biens, afin d&#39;enrichir les profils clients avec des scores de risque spécifiques à l&#39;emplacement.
- Concevez une logique de parcours saisonnière qui fournit du contenu de prévention pertinent en amont des périodes à haut risque, comme la préparation de la saison des ouragans pour les titulaires de police côtiers ou des conseils météorologiques hivernaux pour les clients en climat froid.
- Appliquer des étiquettes de gouvernance des données pour distinguer les données d&#39;évaluation des risques utilisées pour la formation des clients des données utilisées dans les décisions actuarielles de souscription.
- Coordonner le contenu de la prévention des risques avec la couverture spécifique du preneur d&#39;assurance afin que les recommandations soient pertinentes par rapport aux risques effectivement couverts par la police.


## Notifications de changement de politique

Envoyez des notifications personnalisées sur les modifications de politique, les mises à jour de couverture et les nouvelles options en fonction des préférences de communication et de politique spécifiques de chaque client. Des notifications claires et opportunes permettent aux souscripteurs d’être informés et réduisent la confusion quant à leur statut de couverture.

### Impact commercial

Les notifications personnalisées de changement de politique améliorent les taux d’accusé de réception des notifications, ce qui réduit les demandes du service client et améliore la compréhension globale des titulaires de police.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de changement de politique du système d’administration servent de déclencheurs naturels pour des notifications immédiates et pertinentes via le canal préféré de chaque client ou cliente. Il s’agit du modèle approprié lorsque le déclencheur est un événement système (changement de politique) plutôt que le comportement du client et que la communication requise est immédiate et réactive plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Intégrez-la au système d’administration des politiques afin de capturer en temps réel les événements de changement d’approbation, de modification et de renouvellement, en veillant à ce que les notifications reflètent l’état le plus récent des politiques.
- Collaborez avec votre équipe juridique pour vérifier que les notifications de changement de politique répondent aux exigences applicables prescrites par l’état en matière de délai, de langue et de canal de diffusion avant d’activer les communications automatisées.
- Configurez la logique de priorité des canaux en fonction de l’urgence et du type de changement. Par exemple, les réductions de couverture peuvent justifier des canaux plus immédiats que les mises à jour d’informations.
- Conservez un journal d’audit de diffusion pour toutes les notifications de modification de politique afin de prendre en charge la documentation sur la conformité réglementaire et la résolution des litiges.


## Récupération de devis abandonnés

Réengagez les clients qui ont commencé mais n’ont pas terminé un devis d’assurance avec des messages de suivi personnalisés et des offres personnalisées. La diffusion rapide de la récupération ramène les clients potentiels au processus de devis et résout les obstacles courants à l&#39;achèvement.

### Impact commercial

Les campagnes de récupération des abandons de devis améliorent les taux d’achèvement des devis, convertissent davantage de prospects en assurés et réduisent les coûts d’acquisition des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). L&#39;abandon de devis est un événement comportemental qui déclenche un suivi opportun pendant que l&#39;intérêt et l&#39;intention du prospect sont encore frais. Il s’agit du modèle approprié lorsqu’un comportement client discret (abandon) est le déclencheur et que la réponse requise est un réengagement sensible au temps, plutôt qu’une séquence de maturation à plusieurs étapes ou une prise de décision d’offre complexe.

### Considérations techniques

- Intégrez-la à la plateforme de devis en ligne pour capturer les événements d’abandon ainsi que les détails de devis que le client a déjà fournis, ce qui permet un réengagement personnalisé.
- Configurez des règles de minutage qui équilibrent l’urgence avec le respect : suivi initial en quelques heures, avec un nombre limité de rappels ultérieurs au cours des jours suivants.
- Appliquez les règles de consentement et de confidentialité pour vous assurer que le suivi n’est envoyé qu’aux prospects qui se sont inscrits aux communications marketing, en particulier aux clients qui n’ont pas encore établi de relation de politique.
- Incluez des liens profonds qui renvoient directement le prospect à son devis enregistré au lieu de l’obliger à relancer le processus depuis le début.


## Offres De Produits Basées Sur Les Étapes De Vie

Identifiez les clients qui entrent dans de nouvelles étapes de leur vie (comme le mariage, l’achat d’une maison, la croissance de la famille ou la retraite) et proposez des produits d’assurance adaptés à leurs besoins de protection en constante évolution. Le ciblage des étapes de la vie permet aux assurés d’obtenir la bonne couverture au bon moment.

### Impact commercial

Les offres de produits basées sur les étapes de vie permettent d’améliorer les taux d’adoption des produits aux étapes de vie, approfondissant ainsi les relations client lors des moments clés de la prise de décision.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Les transitions d’étape de vie bénéficient d’une orchestration cross-canal combinée à une prise de décision en temps réel pour sélectionner le produit le plus pertinent et le diffuser via le canal préféré du client au moment optimal. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur plusieurs canaux pour assurer des offres cohérentes tout en tirant parti de la prise de décision pour sélectionner le produit le plus approprié pour l’étape de vie détectée. Une orchestration en plusieurs étapes ne peut pas à elle seule fournir l’évaluation d’éligibilité et d’adéquation en temps réel requise pour les recommandations de produits d’assurance.

### Considérations techniques

- Construire des modèles de détection des étapes de la vie en utilisant des signaux comportementaux tels que les changements d&#39;adresse, les mises à jour des bénéficiaires et les modèles de recherche en ligne, combinés à des événements de changement de politique.
- Configurez le moteur de prise de décision avec des règles d&#39;éligibilité et d&#39;adéquation de produit qui correspondent à chaque étape de vie aux recommandations de couverture appropriées.
- Coordonnez les offres à l’étape de la vie avec l’agent ou le courtier désigné afin qu’il soit prêt à aider le client par une conversation consultative lors de la livraison de l’offre.
- Appliquez des étiquettes de gouvernance des données à toutes les sources de données tierces utilisées pour l’inférence de l’étape de vie afin de garantir la conformité aux réglementations de confidentialité des données et aux pratiques marketing équitables.


## Opportunités de remise et d’épargne

Identifiez et communiquez les opportunités de réduction personnalisées (telles que le regroupement, le chauffeur sécurisé, la fidélité et les remises de facturation sans support papier) en fonction du profil et du comportement de chaque client. Les communications proactives sur l’épargne démontrent la valeur et renforcent la relation prix-valeur.

### Impact commercial

Les communications personnalisées sur les remises et les économies améliorent les taux d&#39;utilisation des remises, la satisfaction des clients et le taux de perte lié aux prix.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Real-Time Decisioning évalue l’éligibilité de chaque client aux remises disponibles et sélectionne l’opportunité d’épargne la plus performante à présenter au bon moment. C&#39;est le bon modèle lorsque la sélection des remises doit tenir compte des limites de cumul, des restrictions réglementaires et des calculs actuariels précis — des contraintes qui nécessitent une logique de prise de décision régie plutôt que de simples contrôles d&#39;éligibilité.

### Considérations techniques

- Intégrez-les aux systèmes de notation et de facturation de la politique afin de calculer en temps réel l’éligibilité précise aux remises et les montants d’économies potentielles pour chaque client.
- Configurez des règles de prise de décision qui tiennent compte des limites de cumul des remises et assurez-vous que les montants d’épargne communiqués sont précis sur le plan actuariel et approuvés par l’équipe de tarification.
- Appliquer des règles réglementaires spécifiques aux États pour les communications sur les remises, car certains États ont des restrictions sur la façon dont les remises d&#39;assurance peuvent être commercialisées et appliquées.
- Suivez les résultats de l’adoption des remises pour affiner en permanence le modèle de prise de décision et donner la priorité aux messages d’épargne qui trouvent le plus d’écho auprès des différents segments de clientèle.


## Prévention de la fraude liée aux réclamations

Utilisez la détection intelligente des fraudes pour identifier les schémas de réclamations suspectes et personnaliser les communications d&#39;enquête tout en préservant la confiance des clients. Une prévention efficace de la fraude protège les souscripteurs honnêtes en maintenant des primes équitables et en veillant à ce que les réclamations légitimes soient traitées rapidement.

### Impact commercial

Les programmes intelligents de prévention des fraudes permettent d&#39;améliorer les taux de détection des fraudes, de réduire les paiements frauduleux et de réduire les coûts globaux des réclamations.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de notation du risque de fraude déclenchent des communications appropriées sur les enquêtes et des ajustements du processus en temps réel, ce qui garantit que les demandes signalées reçoivent une attention immédiate. Il s’agit du modèle approprié lorsqu’un événement dérivé du système (score de risque de fraude) est le déclencheur et que l’action requise est un ajustement immédiat des processus internes avec une communication client attentive, plutôt qu’un parcours à plusieurs étapes ou un scénario de prise de décision.

### Considérations techniques

- Intégrez les scores de risque de fraude du système d’analyse des réclamations au profil client tout en appliquant des étiquettes de gouvernance des données strictes pour empêcher l’affichage des données d’enquête de fraude dans les communications avec les clients.
- Concevez des voies de communication qui conservent un ton professionnel et respectueux pour les clients dont les réclamations sont en cours d’examen, en préservant la relation quel que soit le résultat de l’enquête.
- Mettez en œuvre des contrôles d’accès basés sur les rôles pour vous assurer que les indicateurs de fraude ne sont visibles que par les équipes d’enquête autorisées et ne sont jamais affichés dans les vues standard de l’agent ou du service client.
- Coordonnez-vous avec le service de résolution d’identité [!DNL Adobe Experience Platform] pour détecter des motifs sur les profils associés, tels que des adresses partagées ou des numéros de téléphone liés à plusieurs réclamations suspectes.


## Programmes de mieux-être et de prévention

Personnalisez les communications du programme de bien-être, les rappels de participation et les notifications de récompense pour les clients des assurances santé et vie en fonction de leurs objectifs et de leur niveau d’engagement. Les programmes actifs de mieux-être améliorent les résultats de santé des assurés et permettent d&#39;établir une clientèle plus forte et plus engagée.

### Impact commercial

Les communications personnalisées des programmes de mieux-être et de prévention entraînent une amélioration des taux de participation aux programmes, contribuant ainsi à de meilleurs résultats en matière de santé et à une réduction de la fréquence des réclamations.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Les programmes de bien-être sont des expériences d’engagement soutenu avec des jalons, des défis et des récompenses qui nécessitent une orchestration adaptative en fonction de l’activité et des progrès de chaque participant. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux à long terme et à messages multiples avec un embranchement basé sur l’engagement et des ajustements de synchronisation adaptatifs : la messagerie déclenchée par un événement ne peut pas gérer la logique complexe des jalons ou le besoin d’ajuster le rythme des communications en fonction du suivi continu des activités.

### Considérations techniques

- Intégrez aux flux de données des appareils portables et des applications de santé en utilisant l’ingestion par flux [!DNL Adobe Experience Platform], en appliquant des étiquettes de gouvernance des données claires pour distinguer les données de bien-être des données de souscription ou de réclamations.
- Mettre en œuvre des mécanismes de consentement distincts pour la collecte de données sur le mieux-être afin de s&#39;assurer que les participants comprennent comment leurs données sur les activités de santé sont utilisées et peuvent se désinscrire sans affecter leur politique.
- Concevez une logique de parcours qui ajuste l&#39;intensité du programme et la fréquence de communication en fonction du niveau d&#39;engagement de chaque participant afin de prévenir la fatigue et d&#39;encourager une participation soutenue.
- Demandez à vos équipes juridiques et de conformité d’examiner les structures d’incitation au bien-être et les programmes de réduction premium pour assurer la conformité aux réglementations d’assurance d’État applicables avant le lancement.


## Coordination des agents et des courtiers

Activez la communication et la coordination personnalisées entre les clients et leurs agents ou courtiers attribués en fonction des besoins de la politique, de l’historique du service et des préférences. Une meilleure coordination crée une expérience transparente où les clients se sentent soutenus par un conseiller compétent qui comprend leur relation complète.

### Impact commercial

Une coordination efficace des communications entre les agents et les courtiers améliore l’engagement des agents, ce qui renforce les relations avec la clientèle et accroît la rétention, grâce à des interactions de conseil fiables.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). La coordination des agents s’effectue de préférence par le biais d’activations par lots planifiées, qui fournissent aux agents des listes de contacts avec les clients, des points de discussion et des actions recommandées selon une cadence régulière. Il s’agit du modèle approprié lorsque l’audience est volumineuse et prédéfinie, que le timing de diffusion est planifié sur une base récurrente plutôt que selon un événement et qu’aucun embranchement ou prise de décision en temps réel n’est nécessaire.

### Considérations techniques

- Intégrez-la au système de gestion des agents afin de maintenir des affectations agent-client précises et de garantir que les communications reflètent la relation correcte, en particulier pendant les transitions d’agent.
- Concevez l’activation des données sur le portail des agents afin que ces derniers reçoivent une vue consolidée des informations sur les clients, des renouvellements à venir et des actions recommandées sans exposer les données comportementales brutes.
- Appliquez des étiquettes de gouvernance des données pour limiter les éléments de données client qui sont partagés avec les partenaires de courtage externes par rapport aux agents captifs, en respectant les limites de partage des données contractuelles et réglementaires.
- Implémentez des boucles de commentaires à partir des interactions de l’agent dans le profil client afin que les informations des conversations téléphoniques ou en personne enrichissent la vue unifiée et améliorent la personnalisation future.


## Intervention En Cas D&#39;Événement Catastrophique

Communiquez de manière proactive avec les clients des zones touchées lors de catastrophes naturelles ou d’événements catastrophiques avec des informations d’assistance personnalisées, des conseils pour le dépôt de réclamations et des ressources d’urgence. L&#39;approche rapide et empathique durant une crise démontre l&#39;engagement de l&#39;assureur à être là quand les clients en ont le plus besoin.

### Impact commercial

Les communications proactives en réponse aux catastrophes permettent d’améliorer les taux de communication client lors des événements, d’accélérer le dépôt des demandes et de renforcer la confiance et la fidélisation à long terme des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les déclarations d’événements catastrophiques servent de déclencheurs hautement prioritaires pour une communication immédiate et personnalisée avec tous les assurés de la zone géographique touchée. Il s’agit du schéma approprié lorsqu’un événement externe hautement prioritaire est le déclencheur et que la réponse requise est une portée géographique immédiate et étendue, avec des informations urgentes, plutôt que des modèles de comportement individuels des clients ou un séquencement complexe.

### Considérations techniques

- Intégrez-les aux services de surveillance des catastrophes et aux flux de déclaration des catastrophes du gouvernement pour déclencher rapidement des communications lorsque des événements sont déclarés pour des zones géographiques spécifiques.
- Créez des segments d’audience géographiques à l’aide des données d’adresse du titulaire de la police et des informations sur l’emplacement des propriétés pour identifier précisément les clients dans la zone affectée sans communiquer de manière excessive avec les clients non affectés.
- Configurez le routage des messages haute priorité qui remplace les règles standard de limitation et de suppression de la fréquence afin de garantir que les informations de sécurité et de réclamation critiques parviennent immédiatement aux clients.
- Précréez des modèles de message et des configurations de parcours pour les types d’événements catastrophiques courants afin que les communications puissent être activées dans les heures qui suivent une déclaration d’événement, sans qu’il soit nécessaire de créer du contenu pendant la crise.


## Personalization de contenu du portail du détenteur de police

Personnalisez l’expérience du portail en libre-service authentifié et de l’application mobile pour les titulaires de police en affichant les informations, outils et ressources de couverture les plus pertinents en fonction de leur comportement de navigation, de leur portefeuille de politiques et de leurs interactions de service récentes. Un portail qui s&#39;adapte au contexte actuel de chaque titulaire de police réduit les frictions et permet aux clients de trouver plus facilement ce dont ils ont besoin au moment où ils en ont besoin.

### Impact commercial

La personnalisation de l’expérience du portail des assurés entraîne des améliorations mesurables de l’exécution des tâches en libre-service et de l’engagement numérique, ce qui réduit le volume de centres de contact entrants et renforce la satisfaction des clients à l’égard du canal numérique.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Des signaux comportementaux provenant de sessions de portail authentifiées (utilisation du calculateur de couverture, vues de documents de politique, contrôles de statut des demandes et engagement par rubrique de FAQ) entraînent un modèle de recommandation qui fait apparaître de manière dynamique le contenu et les outils les plus pertinents pour le contexte actuel de chaque titulaire de police. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par des signaux comportementaux implicites au sein d’une session authentifiée et que l’objectif est le classement de pertinence d’un contenu ou d’un catalogue de ressources, plutôt qu’Offer Decisioning, qui nécessite une éligibilité régie et une approbation actuarielle avant de présenter une offre de produit, ou Cross-canal avec prise de décision, qui est plus approprié lors de la coordination d’une offre de produit sur plusieurs canaux.

### Considérations techniques

- Appliquez les libellés de gouvernance des données aux signaux comportementaux collectés sur le portail des titulaires de police pour distinguer les analyses d’engagement des données d’assurance réglementées et empêcher que les signaux dérivés de l’historique des sinistres ne se retrouvent dans des modèles de personnalisation sans examen actuariel et de conformité explicite.
- Intégrez le modèle comportemental au système de gestion des polices pour vous assurer que le contenu et les recommandations d&#39;outils reflètent le portefeuille de polices actif de chaque titulaire de police (en affichant des outils de couverture automobile pour les titulaires de polices et des ressources immobilières pour les propriétaires) sans exposer les données brutes de la police au modèle de recommandation au-delà de la classification de la gamme de produits.
- Mettez en œuvre des contrôles de conformité spécifiques à l’État pour vous assurer que la personnalisation comportementale ne constitue pas une recommandation d’assurance ou une sollicitation marketing au titre des réglementations nationales applicables, en particulier lorsque les signaux comportementaux peuvent impliquer la détection d’un écart de couverture.
- Coordonnez les signaux de personnalisation du portail avec le portail des agents afin que les agents au service des titulaires de police qui ont démontré un fort comportement de recherche en libre-service reçoivent une vue consolidée de l’engagement numérique du client ainsi que de leur historique de service.
