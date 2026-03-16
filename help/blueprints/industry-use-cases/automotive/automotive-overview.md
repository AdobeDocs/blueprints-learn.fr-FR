---
title: Cas d’utilisation pour le secteur automobile
description: Découvrez comment les organisations automobiles utilisent Adobe Experience Platform pour personnaliser le parcours d’achat de véhicules, améliorer la fidélisation du service et fidéliser les propriétaires.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# Cas d’utilisation dans le secteur automobile

Les entreprises du secteur automobile utilisent Adobe Experience Platform pour regrouper les données clients issues des interactions des concessionnaires, de la recherche de véhicules en ligne, des dossiers de service et des systèmes de voitures connectées en une vue unique pour chaque propriétaire. Cette base permet des expériences personnalisées tout au long du cycle de vie de la propriété, depuis la recherche initiale du véhicule jusqu’à l’achat, le service et la fidélité.

## Résumé du cas d’utilisation

| Cas d’utilisation | Description | Impact commercial | Modèle de mise en œuvre |
| --- | --- | --- | --- |
| [Parcours d’achat de véhicule Personalization](#vehicle-purchase-journey-personalization) | Personnalisez le parcours d&#39;achat de véhicules de la recherche à l&#39;achat avec des recommandations pertinentes, des options de financement et des informations sur le concessionnaire. Lorsque les acheteurs potentiels reçoivent des conseils personnalisés à chaque étape, ils passent par le funnel des ventes plus rapidement et avec plus de confiance. | Augmentation de 20 à 30 % des taux de conversion de lead à achat, amélioration du pipeline de ventes | [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Rappels de rendez-vous de service](#service-appointment-reminders) | Envoyez des rappels de service personnalisés en fonction du kilométrage du véhicule, de l’historique du service et des préférences du client. La sensibilisation proactive permet de maintenir les véhicules et d&#39;assurer que les clients retournent chez le concessionnaire plutôt que de chercher des fournisseurs tiers. | Augmentation de 40 à 50 % des taux d&#39;affichage des rendez-vous de service, augmentation des revenus de service | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Campagnes de reprise](#trade-in-value-campaigns) | Proactivement proposer des évaluations de valeur de reprise aux clients qui peuvent être prêts pour la mise à niveau. Atteindre les propriétaires au bon moment dans leur cycle de possession accélère le processus d&#39;achat d&#39;un nouveau véhicule. | Augmentation de 25 à 35 % de l&#39;engagement de reprise, augmentation des ventes de véhicules neufs | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Recommandations relatives aux pièces et aux accessoires](#parts-and-accessories-recommendations) | Recommandez les pièces, accessoires et mises à niveau appropriés en fonction du modèle du véhicule, de la durée de possession et des préférences du client. Les recommandations personnalisées du marché secondaire génèrent des revenus supplémentaires tout en aidant les propriétaires à tirer le meilleur parti de leur véhicule. | Augmentation de 30 à 40 % des achats de pièces et d&#39;accessoires, augmentation du chiffre d&#39;affaires du marché secondaire | [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [Avis de rappel de véhicule](#vehicle-recall-notifications) | Envoyez des notifications de rappel personnalisées avec des options de planification de service et des informations de sécurité. Des communications rapides et claires sur les rappels protègent la sécurité des clients et démontrent l&#39;engagement de la marque envers une prise en charge responsable de la propriété. | Augmentation de 60 à 70 % des taux de rappel, amélioration du respect des normes de sécurité | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Nouvelles campagnes de lancement de modèles](#new-model-launch-campaigns) | Ciblez les clients et clientes qui peuvent être intéressés par de nouveaux lancements de modèle en fonction de leur véhicule actuel, de leurs préférences et de leur historique d’achat. Le ciblage ciblé des audiences maximise l’impact du lancement et crée une dynamique de commande précoce. | Augmentation de 35 à 45 % de l’engagement dans la campagne de lancement, augmentation de l’intérêt pour le nouveau modèle | [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [Offres de financement et d&#39;assurance](#financing-and-insurance-offers) | Présentez des offres de financement et d&#39;assurance personnalisées en fonction du profil de crédit, de la sélection du véhicule et du calendrier d&#39;achat. Des produits financiers sur mesure éliminent les obstacles à l&#39;achat et aident les clients à se sentir confiants dans leurs conditions. | Augmentation de 25 à 35 % des taux d’acceptation du financement, augmentation des recettes par vente | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [Planification du test de conduite](#test-drive-scheduling) | Activez la planification personnalisée des essais au volant avec les recommandations des concessionnaires et la disponibilité des véhicules. Le fait de faciliter la tâche des acheteurs intéressés pour qu&#39;ils prennent le volant accélère le processus d&#39;achat. | Augmentation de 50 à 60 % des taux d’achèvement des tests, amélioration de la conversion des ventes | [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Programmes de fidélité des propriétaires](#owner-loyalty-programs) | Personnalisez les communications, les récompenses et les offres exclusives du programme de fidélité en fonction de l’historique de propriété et du niveau de fidélité. La reconnaissance des propriétaires à long terme renforce le lien émotionnel avec la marque. | Augmentation de 40 à 50 % de l’engagement du programme de fidélité, augmentation des achats répétés | [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Plans de garantie et de service étendu](#warranty-and-extended-service-plans) | Recommandez des plans de garantie et d&#39;extension de service à des moments optimaux en fonction de l&#39;âge, du kilométrage et des habitudes d&#39;achat du véhicule. La sensibilisation opportune capture le chiffre d’affaires avant l’expiration des garanties d’usine. | Augmentation de 20 à 30 % de l’adoption de la garantie étendue, augmentation du chiffre d’affaires du service | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Activation des caractéristiques de la voiture connectée](#connected-car-feature-activation) | Personnalisez les recommandations sur les caractéristiques des voitures connectées en fonction des capacités du véhicule et des préférences technologiques. Aider les propriétaires à découvrir les fonctionnalités inutilisées augmente la satisfaction et renforce la relation numérique. | Augmentation de 35 à 45 % des taux d’activation des fonctionnalités, expérience client améliorée | [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Coordination du réseau de concessionnaires](#dealer-network-coordination) | Activez des recommandations de concessionnaire personnalisées basées sur l’emplacement du client, les préférences et l’inventaire des concessionnaires. Connecter les clients avec le concessionnaire approprié améliore l&#39;expérience d&#39;achat et de service. | Augmentation de 30 à 40 % des taux d&#39;engagement des concessionnaires, amélioration de la coordination des ventes | [Web/App Personalization pour visiteurs connus](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Considérations techniques par cas d’utilisation

### Personnalisation du parcours d’achat de véhicule

- Les données sur l&#39;inventaire des véhicules provenant des systèmes de gestion des concessionnaires doivent être intégrées et actualisées fréquemment afin que les recommandations reflètent la disponibilité réelle chez les concessionnaires à proximité.
- Le comportement de la recherche de clients sur le site web, y compris l’activité de configuration du véhicule, l’utilisation d’outils de comparaison et les téléchargements de brochures, doit être capturé pour identifier précisément les signaux d’intention d’achat.
- Les modèles de notation des leads doivent tenir compte à la fois de l’engagement en ligne et des signaux hors ligne tels que les visites chez les concessionnaires et les demandes téléphoniques pour donner la priorité aux prospects les plus intentionnés.
- Les profils [!DNL Real-Time Customer Data Platform] doivent fusionner des sessions de recherche web anonymes avec des identités de client connues une fois qu’un prospect s’enregistre ou visite un concessionnaire.

### Rappels de rendez-vous de service

- Les données relatives au kilométrage et à la télématique des véhicules provenant des systèmes de voitures connectées ou des enregistrements de service des concessionnaires doivent être transmises aux profils des clients pour déclencher des rappels aux intervalles de service appropriés.
- Les messages de rappel doivent inclure des liens de planification en un clic qui pré-renseignent les informations sur le véhicule du client et les articles de service recommandés afin de minimiser la friction de réservation.
- Les enregistrements d’historique de service doivent être intégrés pour éviter de recommander des services récemment terminés et pour personnaliser le rappel avec les éléments de maintenance spécifiques dus.
- [!DNL Journey Optimizer] moment où les messages sont envoyés doit tenir compte de la capacité de service du concessionnaire et des heures d&#39;ouverture afin de s&#39;assurer que les clients peuvent prendre rendez-vous lorsqu&#39;ils reçoivent le rappel.

### Campagnes de valeur de reprise

- Les données d&#39;évaluation des véhicules provenant de fournisseurs tiers doivent être intégrées et actualisées régulièrement pour s&#39;assurer que les estimations de reprise communiquées aux clients sont exactes et concurrentielles.
- Les modèles de cycle de vie de la propriété doivent prendre en compte des facteurs tels que les dates d’expiration des baux, les délais de remboursement des prêts et la durée moyenne de propriété par segment de véhicule pour identifier la fenêtre de portée optimale.
- Les messages de Campaign doivent référencer de manière dynamique le véhicule actuel du client et suggérer des options de mise à niveau spécifiques qui correspondent à ses préférences et à son budget.
- [!DNL Experience Platform] segments doivent exclure les clients qui ont récemment acheté un véhicule ou qui sont actuellement dans un conflit de service actif afin d’éviter une sensibilisation inopportune.

### Recommandations relatives aux pièces et accessoires

- Les données du catalogue de produits doivent inclure des informations sur la compatibilité des véhicules afin que les recommandations n&#39;affichent que les pièces et accessoires correspondant à l&#39;année, à la marque et au modèle du véhicule spécifique du client.
- Les facteurs saisonniers et régionaux devraient influer sur les recommandations ; les accessoires d&#39;hiver devraient être promus dans les climats plus froids, tandis que les améliorations de performance pourraient trouver davantage d&#39;écho dans les régions comptant des communautés de passionnés actifs.
- Le comportement de navigation sur les pages de pièces et d’accessoires doit être capturé et associé à des profils client pour affiner les recommandations en fonction de l’intérêt exprimé.
- [!DNL Experience Platform] implémentation de Web SDK doit capturer les données de numéro d’identification du véhicule des sessions authentifiées afin de garantir la précision du filtrage de compatibilité.

### Notifications de rappel de véhicule

- Les enregistrements des numéros d’identification des véhicules doivent être conservés avec précision dans les profils client afin que les notifications de rappel parviennent à chaque propriétaire affecté et n’aillent pas aux clients non affectés.
- Les messages de rappel doivent être conformes aux exigences réglementaires en matière de contenu des notifications de sécurité, de calendrier et de confirmation de livraison dans chaque marché applicable.
- La diffusion multicanal (e-mail, message texte, notification push et courrier physique) doit être utilisée pour maximiser la portée, car les communications critiques pour la sécurité nécessitent une assurance de diffusion plus élevée que les messages marketing.
- [!DNL Journey Optimizer] devrait suivre l&#39;état de la réponse au rappel au niveau individuel et transmettre les communications de suivi aux propriétaires qui n&#39;ont pas prévu de service dans un délai défini.

### Nouvelles campagnes de lancement de modèle

- Les segments d’audience des campagnes de lancement doivent tenir compte du modèle de véhicule actuel, de la durée de propriété, des signaux d’intérêt des modèles précédents et de l’adéquation démographique pour identifier les prospects ayant la plus forte propension.
- Le contenu de Launch doit être personnalisé afin de faire référence au véhicule actuel du client et de mettre en évidence des améliorations ou des fonctionnalités spécifiques qui répondent à ses priorités probables.
- Le timing de la campagne doit être coordonné avec les dates d’embargo et les plannings de lancement régionaux afin de garantir que les clients reçoivent les informations au moment approprié pour leur marché.
- [!DNL Real-Time Customer Data Platform] l’activation de l’audience doit synchroniser les segments de lancement avec les plateformes publicitaires pour une prise en charge coordonnée des médias payants, ainsi que la diffusion sur les canaux détenus.

### Offres de financement et d&#39;assurance

- Les règles d’éligibilité des offres financières doivent être soigneusement configurées pour se conformer aux réglementations en matière de prêt, afin de s’assurer que les offres présentées aux clients sont celles pour lesquelles elles peuvent réellement être éligibles.
- L’intégration des données de profil de crédit nécessite un traitement sécurisé et des contrôles d’accès stricts, car les informations financières sont soumises à des exigences réglementaires et de confidentialité accrues.
- La présentation de l&#39;offre doit clairement divulguer les modalités, les taux et les conditions conformément aux règlements sur le financement des consommateurs dans chaque marché applicable.
- [!DNL Journey Optimizer] règles de prise de décision doivent tenir compte du prix du véhicule, de l’acompte et des préférences en matière de durée de prêt pour classer les offres par pertinence plutôt que simplement par taux.

### Planifier le test de conduite

- Les systèmes d&#39;inventaire des concessionnaires doivent être intégrés pour confirmer que le modèle de véhicule et la garniture spécifiques qui intéressent le client sont disponibles pour l&#39;essai à la concession recommandée.
- Les recommandations de concessionnaires en fonction de l&#39;emplacement doivent tenir compte de l&#39;adresse du client, des évaluations des concessionnaires et de la disponibilité actuelle des rendez-vous pour suggérer l&#39;option la plus pratique.
- Les messages de confirmation et de rappel de la conduite d&#39;essai doivent inclure les instructions, les coordonnées du concessionnaire et ce à quoi s&#39;attendre, réduisant ainsi les taux de non-présentation.
- [!DNL Experience Platform] données comportementales devraient permettre d&#39;identifier le moment optimal pour suggérer un essai clinique, en évitant de s&#39;adresser prématurément aux chercheurs en début de carrière qui ne sont pas encore prêts.

### Programmes de fidélité des propriétaires

- Les calculs du niveau de fidélité doivent intégrer plusieurs dimensions de l’engagement, notamment les visites de service, les achats de pièces, les recommandations et la participation à des événements, et pas seulement l’historique d’achat de véhicules.
- Les systèmes de récompense dans les concessionnaires et les centres de services doivent être intégrés afin que les avantages de fidélité puissent être remboursés de manière transparente au point de service.
- Les communications doivent s’adapter en fonction de l’étape du cycle de vie de la propriété, offrant différentes propositions de valeur aux nouveaux propriétaires au cours de leur première année par rapport aux propriétaires à long terme approchant une mise à niveau potentielle.
- [!DNL Journey Optimizer] logique de parcours doit détecter les changements de niveau en temps réel et déclencher des messages de félicitations ou de réengagement lorsque les clients passent d’un niveau de fidélité à un autre.

### Plans de garantie et de service étendu

- Les dates d’expiration et les détails de couverture de la garantie doivent faire l’objet d’un suivi précis dans les profils clients pour déclencher une communication au bon moment, généralement 60 à 90 jours avant l’expiration.
- Le kilométrage et les habitudes d&#39;utilisation des véhicules à partir des données ou des dossiers d&#39;entretien des voitures connectées doivent éclairer les recommandations du plan, car les conducteurs à kilométrage élevé bénéficient d&#39;une couverture différente de celle des propriétaires à faible kilométrage.
- Le contenu de la comparaison des plans doit être clair et dépourvu de jargon, ce qui permet aux clients de comprendre exactement ce qui est couvert et la valeur relative des coûts de réparation potentiels.
- Les segments [!DNL Real-Time Customer Data Platform] doivent faire la distinction entre les clients dont les garanties d’usine arrivent à expiration, ceux dont les plans étendus existants sont sur le point d’être renouvelés et ceux qui n’ont pas de couverture actuelle.

### Activation des caractéristiques des voitures connectées

- Les données de la plateforme de voitures connectées doivent être intégrées pour identifier les caractéristiques disponibles sur chaque véhicule et celles que le propriétaire a déjà activées ou utilisées.
- Le suivi de l’adoption des fonctionnalités doit capturer les événements d’activation, la fréquence d’utilisation et la profondeur d’engagement afin de personnaliser la séquence et le rythme des recommandations de fonctionnalités.
- Les canaux de notification embarqués doivent être coordonnés avec les notifications par e-mail et par application afin de fournir des invites de fonctionnalités au moment le plus pertinent du point de vue contextuel, par exemple en suggérant des fonctionnalités de navigation lorsqu&#39;un voyage sur la route est détecté.
- Les profils [!DNL Experience Platform] doivent stocker les données de configuration technologique du véhicule, y compris les packages installés et les versions logicielles, afin de s&#39;assurer que les recommandations de fonctionnalités sont compatibles avec le véhicule spécifique du propriétaire.

### Coordination du réseau de concessionnaires

- Les flux d&#39;inventaire des concessionnaires doivent être intégrés et actualisés fréquemment pour s&#39;assurer que la disponibilité des véhicules présentée aux clients reflète fidèlement ce qui se trouve sur le lot de chaque concessionnaire.
- La logique d&#39;affectation client-concessionnaire doit tenir compte de la proximité, de la spécialisation du concessionnaire, des préférences linguistiques et de toute relation existante avec le concessionnaire afin de fournir la meilleure correspondance.
- Les règles d&#39;acheminement des leads doivent garantir que lorsqu&#39;un client exprime son intérêt pour l&#39;achat en ligne, la demande atteint rapidement le concessionnaire approprié avec un contexte complet sur l&#39;activité de recherche du client.
- [!DNL Experience Platform] résolution d’identité doit gérer les scénarios dans lesquels un client interagit avec plusieurs concessionnaires, en conservant un profil unifié tout en respectant le point de vue de chaque concessionnaire sur ses propres relations client.
