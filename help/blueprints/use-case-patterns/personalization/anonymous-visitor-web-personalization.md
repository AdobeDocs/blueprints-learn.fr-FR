---
title: Personalization Web de visiteur anonyme
description: Découvrez comment diffuser du contenu web personnalisé aux visiteurs et visiteuses non identifiés en fonction de signaux comportementaux au cours de la session.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 1%

---


# Personnalisation web des visiteurs anonymes

Ce plan de référence fournit des conseils d’implémentation pour la diffusion de contenu web personnalisé aux visiteurs anonymes (non identifiés) en fonction de signaux comportementaux en session. Il couvre l’ensemble du cycle de vie de la mise en œuvre, de [!DNL Web SDK] configuration et la définition des audiences Edge à la diffusion de contenu et aux rapports de performances, et est conçu pour les architectes de solutions, les technologues marketing et les ingénieurs de mise en œuvre qui travaillent avec [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP).

Utilisez ce plan pour comprendre l’architecture, évaluer les options de mise en œuvre, prendre des décisions de configuration éclairées et rechercher la documentation Experience League appropriée pour chaque phase de mise en œuvre.

Le modèle fonctionne avec des données limitées : uniquement ce qui peut être observé dans la session en cours et tout profil Edge anonyme accumulé à partir de visites précédentes avec le même appareil ou cookie. Cela le rend adapté à la personnalisation en haut de funnel lorsque le visiteur ne dispose d’aucun compte ou ne s’est pas authentifié.

## Présentation du cas d’utilisation

Le Personalization Web de visiteur anonyme répond au besoin de l’entreprise de fournir un contenu pertinent et personnalisé aux visiteurs et visiteuses du site Web qui n’ont pas encore été identifiés (c’est-à-dire qui ne se sont pas connectés, qui n’ont aucune identité connue et qui ne peuvent pas être résolus en un profil client unifié). Malgré ces limitations, une personnalisation significative est possible à l’aide de signaux comportementaux en session : pages vues, temps passé sur le site, profondeur de défilement, source de référence, emplacement géographique, type d’appareil et paramètres de campagne UTM.

Ce modèle utilise les surfaces de canal web d’AJO et les expériences basées sur du code pour modifier le contenu de la page en temps réel. La segmentation d’Edge est la méthode d’évaluation principale, car les décisions doivent être prises avec une latence inférieure à la seconde lorsque le visiteur navigue sur le site. Le [!DNL Web SDK] collecte des signaux comportementaux et les envoie au [!DNL AEP Edge Network], où les règles d’audience évaluées par Edge déterminent la variante de contenu à diffuser.

Contrairement à la personnalisation web/de l’application d’un visiteur connu, qui utilise le profil unifié complet et l’appartenance à un segment, ce modèle est limité aux données observables dans la session en cours et à tout profil Edge anonyme associé à l’ECID du visiteur ([!DNL Experience Cloud ID]). Cette distinction est essentielle pour la planification de l’implémentation : les signaux comportementaux disponibles pour la personnalisation sont limités à ce que le [!DNL Web SDK] capture et à ce qui persiste dans le magasin de profils Edge entre les sessions via l’ECID basé sur les cookies.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Augmenter l’engagement du site web](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Améliorez le temps passé sur le site, les pages par session et l’interaction avec le contenu web par le biais d’expériences pertinentes adaptées aux signaux anonymes des visiteurs.

| KPI |
| --- |
| Temps passé sur la page (web) |
| Engagement |
| Taux de conversion |

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Adapter le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus, même pour les visiteurs qui ne se sont pas encore identifiés.

| KPI |
| --- |
| Engagement |
| Taux de conversion |
| Satisfaction du client (CSAT) |

**[Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire en présentant le contenu le plus pertinent en fonction du contexte comportemental.

| KPI |
| --- |
| Taux de conversion |
| Conversion du lead |
| Coût par lead |

## Exemples de cas d’utilisation tactiques

Les exemples suivants illustrent des scénarios spécifiques où ce modèle peut être appliqué.

- **Test A/B des titres des pages de destination basé sur la source de référence** — Testez différents titres pour les visiteurs provenant de Google, des médias sociaux ou du trafic direct afin d’optimiser l’engagement par le canal d’acquisition
- **Recommandations d’affinité catégorielle basées sur le comportement de navigation** — Affichez les recommandations de produits ou de contenus basées sur les pages consultées au cours de la session en cours pour augmenter les taux de découverte et de conversion
- **Offre de sortie-intention pour les visiteurs sur le point de partir** — Présentez une offre promotionnelle ou un formulaire de capture de piste lorsque des signaux comportementaux indiquent que le visiteur est sur le point d’abandonner le site
- **Bannière promotionnelle géo-ciblée** — Affichez des promotions spécifiques à un emplacement, du contenu de localisateur de magasin ou des offres régionales en fonction de l’emplacement géographique du visiteur
- **Optimisation de la disposition du contenu spécifique à l’appareil** — Adaptez la disposition du contenu, la taille des images et l’emplacement du CTA selon que le visiteur se trouve sur un ordinateur, une tablette ou un appareil mobile
- **Messages de bienvenue pour les nouveaux visiteurs et les visiteurs récurrents** — Différenciez l’expérience des nouveaux visiteurs de celle des visiteurs anonymes récurrents à l’aide de la persistance ECID entre les sessions
- **Recommandations de contenu basées sur les pages consultées de la session en cours** — Faites apparaître de manière dynamique les articles, produits ou ressources associés en fonction des pages que le visiteur a déjà consultées
- **Bannière principale dynamique basée sur les paramètres de campagne UTM** — Personnalisez la bannière principale pour qu’elle corresponde au message ou à la contenu créatif de la campagne de référence

## Indicateurs clés de performance

Utilisez les indicateurs de performance clés suivants pour mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’impression Personalization | Pourcentage de pages vues éligibles pour lesquelles du contenu personnalisé a été diffusé | rapport de campagne AJO : impressions/nombre total de pages vues |
| Taux de clic publicitaire (CTR) | Pourcentage d’impressions de contenu personnalisé qui génèrent un clic | Rapport de campagne AJO : clics/impressions |
| Effet élévateur d’engagement | Augmentation du temps passé sur la page, des pages par session ou de la profondeur de défilement pour le contenu personnalisé par rapport au contenu par défaut | comparaison de l’espace de travail CJA : cohorte personnalisée et contrôle |
| Taux de conversion | Pourcentage de visiteurs et visiteuses exposés à du contenu personnalisé qui effectuent l’action souhaitée | analyse de CJA funnel : impression > interaction > conversion |
| Réduction du taux de rebond | Diminution du nombre de sessions d’une seule page pour les visiteurs qui reçoivent du contenu personnalisé | analyse des sessions CJA : delta de taux de rebond pour les sessions personnalisées par rapport aux sessions par défaut |
| Taux de succès de l’expérience | Pourcentage de tests A/B qui génèrent un résultat gagnant statistiquement significatif | Rapport d’expérience AJO : les expériences atteignent le seuil de confiance |

## Modèle de cas d’utilisation

La section suivante décrit le modèle principal et la chaîne de fonctions pour ce cas d’utilisation.

**Personalization Web de visiteur anonyme**

Diffusez du contenu personnalisé basé sur des signaux comportementaux en session pour les visiteurs et visiteuses non identifiés via le canal web AJO.

**Chaîne de fonctions :** Configuration de surface web > Évaluation des règles comportementales > Diffusion de contenu > Tracking des impressions > Rapports

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** : configuration de la surface de canal web, création de contenu (expériences web et basées sur du code), exécution de campagnes, expérimentation de contenu (tests A/B), prise de décision (sélection de contenu dynamique) et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** : segmentation Edge pour l’évaluation d’audiences en temps réel en fonction de signaux comportementaux en session ; gestion anonyme des profils Edge
- **[!DNL Adobe Experience Platform] (AEP)** : [!DNL Web SDK] pour la collecte de signaux comportementaux, [!DNL Edge Network] pour le routage des données en temps réel et la diffusion de la personnalisation, configuration des trains de données

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Sandbox AJO avec autorisations de canal web configurées. [!DNL Web SDK] autorisations d’implémentation et accès au flux de données accordés à l’équipe d’implémentation. Les utilisateurs et utilisatrices dotés de rôles qui permettent la configuration des canaux web, la gestion des audiences et l’exécution des campagnes. | [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schéma d’événement d’expérience capturant des signaux comportementaux web (pages vues, clics, profondeur de défilement, données de référence, paramètres UTM). Le schéma doit inclure des groupes de champs d’interaction web standard et être activé pour que le profil Edge prenne en charge l’évaluation en temps réel. Un jeu de données correspondant doit être créé et activé pour Profil. | [&#x200B; Présentation du système XDM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Sources et collecte de données | Obligatoire | [!DNL Web SDK] doit être implémenté sur toutes les propriétés web de target avec un flux de données configuré pour acheminer les données vers [!DNL AEP Edge Network]. Les services [!DNL Adobe Experience Platform] et [!DNL Adobe Journey Optimizer] doivent être activés pour le flux de données. Il s’agit d’une dépendance critique : sans [!DNL Web SDK], aucune collecte de signaux comportementaux ni diffusion d’expérience n’est possible. | [Présentation du SDK web](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Configuration des identités et des profils | Obligatoire | ECID ([!DNL Experience Cloud ID]) configuré comme espace de noms d’identité principal pour les visiteurs anonymes. La politique de fusion Edge doit être configurée avec `isActiveOnEdge: true` pour résoudre les données de profil anonymes en périphérie. Une seule politique de fusion peut être active sur le serveur Edge par sandbox. | [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Définition et segmentation de l’audience | Obligatoire | Segments d’audience évalués par Edge définis en fonction de signaux comportementaux en session. La segmentation d’Edge est obligatoire pour la latence d’évaluation de la sous-seconde. Les règles de segmentation ne doivent utiliser que des expressions de règle de segmentation éligibles à Edge (vérifications d’attributs simples et appartenance à un segment : aucune requête de série temporelle ni agrégation complexe). | [segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Sans objet | Valeur limitée pour les visiteurs anonymes, car il n’y a qu’un minimum de données de profil historiques à agréger. Peut devenir applicable si le profil Edge accumule des données comportementales significatives provenant de visites anonymes antérieures sur plusieurs sessions. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | L’expiration des profils anonymes doit être configurée pour que les profils Edge anonymes gèrent le stockage et respectent les exigences de confidentialité. Les profils ECID uniquement peuvent être définis pour expirer entre 14 et 365 jours. Les politiques de consentement des cookies doivent être appliquées à la collecte de données comportementales. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les libellés de gouvernance sur les données comportementales assurent la conformité, en particulier pour le géociblage (libellé géographique sensible S2) et la personnalisation basée sur les appareils. Les libellés empêchent l’utilisation de données comportementales restreintes dans des contextes de personnalisation non autorisés. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | La surveillance des flux de données [!DNL Edge Network] et [!DNL Web SDK] permet de détecter les problèmes de diffusion de personnalisation. Configurez des alertes pour les échecs de flux de données, les erreurs d’ingestion et les anomalies de diffusion Edge. Critique pour les déploiements d’exploitation où les échecs de personnalisation dégradent l’expérience des visiteurs. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Les rapports de performances Personalization font partie de la chaîne de fonctions (phase 5). L’analyse CJA de l’efficacité de la personnalisation des visiteurs anonymes permet une analyse funnel approfondie, une comparaison des cohortes et une mesure de l’impact de la conversion au-delà de ce que fournissent les rapports natifs AJO. | Présentation de [CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer] (AJO)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de canal | Phase 1 : configuration de la surface web | Configurer des surfaces de canal web définissant où le contenu personnalisé sera diffusé sur les propriétés web cibles |
| Création de messages | Phase 3 : création de contenu et création de variantes | Créez des variantes de contenu personnalisées pour les surfaces web à l’aide du concepteur web, de l’éditeur d’expérience basé sur le code ou de modèles de contenu |
| Exécution de la campagne | Phase 4 : configuration de la campagne et de la diffusion | Créer et activer des campagnes web qui lient les audiences, le contenu et la configuration de diffusion |
| Prise de décision. | Phase 3 : création de contenu et création de variantes (option C) | Configurez les politiques de décision, les règles d’éligibilité et les stratégies de classement pour la sélection de contenu dynamique en fonction de signaux comportementaux |
| Expérimentation de contenu | Phase 3 : création de contenu et création de variantes (option B) | Configurez des expériences de contenu A/B et multivariées avec affectation du trafic, mesures de succès et seuils de confiance |
| Rapports et analyse des performances | Phase 5 : Rapports et analyse de la performance | Surveillez les mesures de diffusion de personnalisation, l’efficacité des variantes, les résultats des expériences et l’impact de la conversion |

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 2 : définition de l’audience comportementale | Définissez et évaluez des segments d’audience basés sur les ressources Edge à l’aide de signaux comportementaux en session pour le ciblage de la personnalisation en temps réel |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] [!DNL Web SDK] est implémentée sur toutes les propriétés web de target avec des appels `sendEvent` capturant les pages vues, les clics et les interactions comportementales pertinentes
- [ ] flux de données est configuré dans l’interface utilisateur de collecte de données avec les services [!DNL Adobe Experience Platform] et [!DNL Adobe Journey Optimizer] activés
- [ ] schéma Événement d’expérience existe avec des groupes de champs d’interaction web (pages vues, données de référence, paramètres UTM, contexte de l’appareil) et est activé pour Profil
- [ ] espace de noms d’identité ECID est configuré et désigné comme identité principale sur le schéma d’événement comportemental web
- [ ] politique de fusion Edge est configurée avec `isActiveOnEdge: true` dans le sandbox cible
- [ ] canal web AJO est configuré et accessible dans le sandbox cible
- [ ] Les variantes de contenu (copie, images, CTA) sont conçues et approuvées pour chaque cas d’utilisation de la personnalisation
- [ ] mesures de succès sont définies (ce qui constitue un événement de conversion ou d’engagement pour une mesure).
- [ ] Mécanisme de consentement des cookies est mis en œuvre sur le site web afin de se conformer aux réglementations de confidentialité avant de collecter des données comportementales

## Options de mise en œuvre

Cette section décrit trois approches de mise en œuvre. Sélectionnez l’option qui correspond le mieux à vos besoins de personnalisation.

### Option A : personnalisation web basée sur des règles

**Idéal pour :** personnalisation simple et déterministe : bannières géo-ciblées, titres spécifiques à une source de référence, dispositions spécifiques à un appareil, messages nouveaux ou récurrents destinés aux visiteurs. Choisissez cette option lorsque la variante de contenu peut être déterminée par une logique conditionnelle simple (si condition X, afficher le contenu Y).

**Fonctionnement :**

La personnalisation basée sur des règles utilise des segments d’audience évalués par Edge pour déterminer quelle variante de contenu un visiteur voit. Chaque segment d’audience est mappé à une variante de contenu spécifique par le biais de règles conditionnelles définies dans la campagne. Lorsqu’un visiteur charge une page, le [!DNL Web SDK] envoie des signaux comportementaux au [!DNL Edge Network], qui évalue le profil Edge du visiteur par rapport aux règles d’audience définies en millisecondes. La variante de contenu correspondante est renvoyée dans la réponse [!DNL Edge Network] et rendue sur la page.

Cette approche nécessite de définir des segments d’audience distincts dans RT-CDP (par exemple, « visiteurs à partir de la recherche Google », « visiteurs en Californie », « visiteurs sur appareil mobile ») et de créer des variantes de contenu correspondantes dans AJO. La campagne lie chaque audience à sa variante de contenu à l’aide de règles de contenu conditionnel ou de campagnes distinctes par segment. Aucun classement IA ni partage du trafic n’est impliqué, la relation entre l’audience et le contenu est déterministe.

**Considérations principales :**

- Requiert des critères d’audience bien définis qui peuvent être exprimés en tant qu’expressions de règle de segment éligibles sur Edge
- Les variantes de contenu doivent être précréées pour chaque segment d’audience
- L’ajout de nouvelles règles de personnalisation nécessite la création de segments d’audience et de variantes de contenu
- ne fournit pas de mesure statistique de l’efficacité des variantes de contenu ;

**Avantages :**

- Implémentation et compréhension les plus simples : relation de cause à effet claire entre l’audience et le contenu
- Aucune surcharge d’expérimentation ni aucun fractionnement du trafic requis
- Le comportement déterministe simplifie les tests et l’assurance qualité
- Faible latence, car l’évaluation Edge est purement basée sur des règles
- Fonctionne bien lorsque l’entreprise sait déjà quel contenu est le plus performant pour chaque segment

**Limitations :**

- Aucun mécanisme intégré pour mesurer si la personnalisation améliore les résultats par rapport au contenu par défaut
- Nécessite une prise de décision manuelle concernant le contenu à afficher pour chaque segment
- Ne s’adapte pas ou ne s’optimise pas au fil du temps : règles statiques jusqu’à modification manuelle.
- La mise à l’échelle à de nombreux segments et variantes augmente la complexité de la configuration

**Experience League:**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Option B : personnalisation web basée sur l’expérimentation

**Idéal pour les tests A/B et multivariés** qui testent des variantes d’en-tête, les couleurs de bouton CTA, des variantes de mise en page et des offres promotionnelles, avec une mesure de la signification statistique. Choisissez cette option lorsque vous devez valider la variante de contenu la plus performante avant de vous engager dans une règle de personnalisation permanente.

**Fonctionnement :**

La personnalisation basée sur l’expérimentation utilise l’expérimentation de contenu d’AJO pour affecter de manière aléatoire les visiteurs aux groupes de traitement de contenu et mesurer la variante la plus performante par rapport à une mesure de succès définie. Le trafic est réparti entre les variantes (par exemple, 50/50 pour A/B, 33/33/34 pour A/B/C) et les performances sont suivies jusqu’à ce que la signification statistique soit atteinte.

L’expérience est incorporée dans une campagne web AJO. Lorsqu’un visiteur charge une page, l’[!DNL Edge Network] l’affecte à un groupe de traitement en fonction de l’affectation du trafic configurée. Le visiteur voit systématiquement le même traitement pour la durée de l’expérience (persistance au niveau de la session ou au niveau du visiteur, selon la configuration). Les mesures de succès (clics, conversions, événements d’engagement) sont suivies via [!DNL Web SDK] et signalées dans le rapport d’expérience AJO.

Cette option ne nécessite pas de segments d’audience prédéfinis pour le ciblage : tous les visiteurs (ou un sous-ensemble ciblé) participent à l’expérience. L’objectif est de découvrir quel contenu est le plus performant, et non de cibler des segments connus avec un contenu prédéterminé.

**Considérations principales :**

- Nécessite un volume de trafic suffisant pour atteindre une signification statistique dans un délai raisonnable
- Les expériences utilisent un modèle statistique bayésien avec des intervalles de confiance valides à tout moment
- Un groupe d’exclusion (ne reçoit aucun contenu personnalisé) est recommandé pour mesurer l’effet élévateur incrémentiel
- Une seule expérience peut être active par campagne à la fois
- Les modifications des expériences nécessitent l’arrêt et le redémarrage de la campagne

**Avantages :**

- Mesure statistiquement rigoureuse de l’efficacité des variantes de contenu
- Supprime les conjectures des décisions de personnalisation — la sélection de contenu axée sur les données
- Prend en charge les groupes d’exclusion pour la vraie mesure de portance incrémentielle
- Rapports d’expérience intégrés avec intervalles de confiance et déclaration du gagnant
- Les résultats peuvent éclairer la personnalisation future basée sur des règles (option A) en identifiant les variantes gagnantes

**Limitations :**

- Nécessite un volume de trafic significatif : l’importance des pages à faible trafic peut prendre des semaines
- Le fractionnement du trafic signifie que certains visiteurs voient un contenu sous-optimal pendant la période de test
- Impossible de personnaliser par segment pendant l’expérience (tous les visiteurs ou un sous-ensemble participent de manière égale)
- Maximum de 10 variantes de traitement par expérience
- Aucune optimisation continue : les expériences sont discrètes avec un début et une fin

**Experience League:**

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Option C : personnalisation web basée sur la prise de décision

**Idéal pour :** la sélection de contenu dynamique (recommandations d’affinité de catégorie, offres d’intention de sortie, recommandations comportementales), où une politique de décision évalue les signaux de session et sélectionne le contenu optimal à partir d’un catalogue d’éléments éligibles. Choisissez cette option lorsque la logique de sélection du contenu est trop complexe pour des règles simples, lorsque vous souhaitez une optimisation avec classement par l’IA ou lorsque l’ensemble des éléments de contenu éligibles est volumineux et dynamique.

**Fonctionnement :**

La personnalisation basée sur la prise de décision utilise AJO Decisioning pour évaluer les signaux comportementaux et sélectionner la meilleure variante de contenu pour chaque visiteur à partir d’un catalogue géré d’éléments de contenu (offres). Chaque élément de contenu comporte des règles d’éligibilité (qui remplit les conditions), des représentations (à quoi ressemble le contenu à chaque emplacement) et des contraintes de limitation facultatives (fréquence d’affichage). Une politique de décision associe les emplacements (où le contenu apparaît sur la page) à des collections d’éléments de contenu et applique une stratégie de classement pour sélectionner la meilleure option.

Lorsqu’un visiteur charge une page, l’[!DNL Web SDK] envoie une requête [!DNL Edge Network] qui inclut la portée de décision. Le moteur de prise de décision évalue le profil Edge du visiteur par rapport aux règles d’éligibilité des éléments de contenu, applique la stratégie de classement (en fonction de la priorité, de la formule ou de l’IA) et renvoie l’élément de contenu gagnant. Cela se produit en périphérie avec une latence inférieure à la seconde.

La stratégie de classement détermine l’ordre des éléments de contenu éligibles. Le classement par priorité utilise des valeurs de priorité affectées manuellement. Le classement basé sur une formule utilise une expression personnalisée (par exemple, pondération de la récence des pages vues). Le classement par l’IA utilise un modèle de machine learning qui optimise la mesure de succès sélectionnée au fil du temps, mais qui nécessite au moins 1 000 événements de conversion pour la formation.

**Considérations principales :**

- Nécessite de configurer les composants de prise de décision : emplacements, règles d&#39;éligibilité, éléments de contenu, éléments de secours, collections et politiques de décision
- Les stratégies classées par l’IA nécessitent un volume de conversion suffisant (plus de 1 000 événements) pour entraîner le modèle
- les décisions Edge sont limitées aux attributs de profil disponibles dans le magasin de profils edge
- Les éléments de contenu doivent être gérés et conservés dans la bibliothèque Decisioning
- Le contenu de secours doit être défini dans les cas où aucun élément personnalisé ne se qualifie

**Avantages :**

- Évoluer vers des catalogues de contenu volumineux sans nécessiter de mappage audience-contenu individuel
- Les stratégies classées par l’IA optimisent en permanence la sélection de contenu en fonction des performances observées
- Les règles d’éligibilité et les contraintes de limitation fournissent un contrôle affiné sur la diffusion de contenu
- Prend en charge une logique commerciale complexe qui serait difficile à exprimer en tant que segments ciblés
- Réutilisable sur plusieurs canaux : la même politique de décision peut alimenter la personnalisation web, par e-mail et mobile

**Limitations :**

- Plus grande complexité de mise en œuvre : nécessite la configuration de la pile de composants Decisioning complète
- Le classement par l’IA nécessite un volume de conversion important et du temps pour s’entraîner efficacement
- Les limitations des données de profil Edge limitent la complexité des règles d’éligibilité pour les visiteurs anonymes
- Frais généraux de gestion des éléments de contenu : chaque élément nécessite des représentations, des règles d&#39;éligibilité et une maintenance
- Le débogage de la logique de prise de décision est plus complexe que les approches basées sur des règles

**Experience League:**

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### Comparaison des options

Le tableau suivant compare les trois options de mise en œuvre selon des critères clés.

| Critères | Option A : fondée sur des règles | Option B : Expérimentation | Option C : Prise De Décisions |
| --- | --- | --- | --- |
| Idéal pour | Mappages segment-contenu connus | Identification du contenu qui fonctionne le mieux | Sélection dynamique de contenu à partir de catalogues volumineux |
| Complexité | Faible | Moyenne | Élevée |
| Latence | Sous-seconde (edge) | Sous-seconde (edge) | Sous-seconde (edge) |
| Précision Personalization | Niveau du segment (règles d’audience) | Niveau du visiteur (affectation aléatoire) | Niveau du visiteur (éligibilité + classement) |
| Optimisation du contenu | Manuelle (pas de mesure) | Tests statistiques (A/B) | Continu (classement par l’IA) ou manuel (priorité) |
| Nécessite des segments d’audience | Oui (évaluation Edge) | Non (fractionnement du trafic) | Facultatif (pour les règles d’éligibilité) |
| Capacité de mesure | Aucun natif (nécessite CJA) | Rapports d’expérience intégrés | Rapports de prise de décision natifs |
| Taille du catalogue de contenu | Petit (1 :1 segment à contenu) | Petite (2-10 variantes) | Volumineux (nombre illimité d’éléments éligibles) |
| Requiert | Audiences Edge, variantes de contenu | Campagne avec expérience activée | Composants de prise de décision (emplacements, offres, politiques) |

### Choisir la bonne option

Utilisez la logique de décision suivante pour sélectionner l’option d’implémentation appropriée :

1. **Savez-vous déjà quel contenu doit être affiché pour chaque segment de visiteurs ?**
   - Oui : Commencez par **Option A (basée sur des règles)**. Vous avez établi des stratégies de contenu par segment et avez besoin d’une diffusion déterministe.
   - Non : Passer à la question 2.

2. **Devez-vous tester un petit nombre de variantes de contenu pour trouver le meilleur résultat ?**
   - Oui : Choisissez **Option B (Expérimentation)**. Vous souhaitez effectuer une validation statistique avant de vous engager dans une stratégie de contenu.
   - Non : Passer à la question 3.

3. **Disposez-vous d’un catalogue volumineux d’éléments de contenu avec des exigences complexes en matière d’éligibilité et de classement ?**
   - Oui : Choisissez **Option C (Prise De Décision)**. Vous avez besoin d’une sélection de contenu dynamique qui va au-delà des simples règles.
   - Non : commencez par l’option **A (basée sur des règles)** pour plus de simplicité, puis passez à l’option B ou C au fur et à mesure que les besoins augmentent.

**Options de combinaison :** ces options ne s’excluent pas mutuellement. Une progression courante consiste à commencer par l’option B (expérimentation) pour découvrir le contenu gagnant, puis à déployer les gagnants à l’aide de l’option A (basée sur des règles) pour une diffusion continue. L’option C (prise de décision) peut être superposée pour les cas d’utilisation qui nécessitent une sélection dynamique basée sur un catalogue, tandis que l’option A gère des règles déterministes plus simples.

## Phases de mise en œuvre

Les phases suivantes décrivent le workflow de mise en œuvre de bout en bout.

### Phase 1 : configuration des surfaces web

**Fonction d’application :** AJO : Configuration de canal

Définissez les surfaces de canal web qui spécifient où le contenu personnalisé sera diffusé sur votre site web. Une surface web identifie une URL de page ou un modèle d’URL spécifique ainsi que l’emplacement sur la page (sélecteur CSS ou surface d’expérience basée sur le code) où AJO peut injecter ou remplacer du contenu.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : type de surface** — Comment le contenu personnalisé doit-il être diffusé sur la page ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Canal web (éditeur visuel) | La personnalisation implique la modification des éléments de page visibles (bannières, titres, images, CTA) à l’aide d’un éditeur visuel par glisser-déposer | Nécessite l’extension de navigateur du concepteur web . Idéal pour les modifications de contenu marketing. Limité aux modifications visuelles des éléments de page existants. |
| Expérience basée sur le code | La personnalisation nécessite l’injection de données structurées (JSON) que le code de l’application du site web utilise et génère | Nécessite une implémentation du développeur pour utiliser la payload JSON. Flexibilité maximale pour une personnalisation complexe. Idéal pour les SPA, les composants dynamiques et le rendu programmatique. |
| Les deux (hybride) | Différentes personnalisations sur le même site nécessitent différents mécanismes de diffusion | Utilisez le canal web pour des modifications visuelles simples et des expériences basées sur du code pour le rendu programmatique. Complexifie la mise en œuvre, mais optimise la couverture. |

>[!NOTE]
>**Décision : portée de la surface** — Quelle portée d’URL la surface web doit-elle couvrir ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Correspondance d’URL exacte | Personalization cible une page spécifique (par exemple, page d’accueil, page de destination) | Le ciblage le plus précis. Nécessite des surfaces distinctes pour chaque page. |
| Modèle d’URL avec caractères génériques | Personalization s’applique à une catégorie de pages (par exemple, toutes les pages de produits, tous les articles de blog) | Réduit les frais généraux de gestion des surfaces. Les variantes de contenu doivent être conçues pour fonctionner sur toutes les pages correspondantes. |
| Surface d’application monopage (SPA) | Le site web est une SPA où les modifications d’URL ne déclenchent pas de rechargements complets de la page | Nécessite une configuration de [!DNL Web SDK] compatible avec les SPA avec des appels `sendEvent` sur les modifications d’affichage. Les définitions de surface utilisent le nom de la vue SPA plutôt que l’URL. |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Administration > Canaux > Configuration web

**Détails de configuration clés :**

- Définir l’URL de page ou le modèle d’URL de la surface
- Spécifier le sélecteur CSS ou l’URI de surface pour l’emplacement du contenu
- Pour les expériences basées sur du code, définissez le nom de surface que le code de l’application référencera
- Associez la surface au sandbox AJO où les campagnes seront créées

**Documentation Experience League :**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canal d’expérience basé sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Configuration de l’expérience basée sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### Phase 2 : définition des audiences comportementales

**Fonction d’application :** RT-CDP : évaluation de l’audience

Définissez des segments d’audience évalués par Edge en fonction des signaux comportementaux en session qui pilotent le ciblage de personnalisation. Ces audiences déterminent quels visiteurs sont qualifiés pour chaque expérience personnalisée. L’évaluation Edge est obligatoire pour ce modèle, car les décisions de personnalisation doivent être prises dans des délais inférieurs à la seconde lorsque le visiteur navigue sur le site.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : sélection des signaux comportementaux** — Quels signaux en session doivent orienter le ciblage de la personnalisation ?

| Signal | Quand l’utiliser | Éligibilité d’Edge |
| --- | --- | --- |
| Paramètres UTM/source de référence | Personnalisation de page de destination spécifique à Campaign | Éligible : vérification simple des attributs de l’événement en cours |
| Situation géographique (pays, région, ville) | Promotions régionales, contenu spécifique à la langue, localisateur de magasin | Éligible — vérification des attributs de profil |
| Type d’appareil (ordinateur de bureau, mobile, tablette) | Mises en page de contenu et CTA optimisées pour les appareils | Éligible — vérification des attributs de profil |
| Pages vues dans la session | Affinité catégorielle, recommandations contenu | Éligible avec contraintes : contrôles simples du nombre d’événements uniquement |
| Nouveau ou visiteur récurrent | Messages de bienvenue, engagement progressif | Éligible — La persistance ECID indique le visiteur récurrent |
| Temps passé sur le site/profondeur de défilement | Offres basées sur l’engagement et l’intention de sortie | Peut nécessiter une implémentation personnalisée, mais pas une implémentation Edge native |

>[!NOTE]
>**Décision : méthode d’évaluation de l’audience** — Toutes les audiences de ce modèle doivent utiliser l’évaluation Edge. Confirmez l’éligibilité avant de définir les segments.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Évaluation Edge | Obligatoire pour ce modèle | Les expressions de règle de segment doivent être éligibles à Edge : comparaisons d’attributs simples, vérifications d’appartenance à un segment, aucune requête de série temporelle ni fonction d’agrégation. Latence de l’évaluation de la sous-seconde. |
| Évaluation par flux (secours) | Lorsque l’expression de la règle de segment n’est pas éligible Edge, mais que le temps quasi réel est acceptable | Latence de secondes à minutes. Prend en charge des expressions de règle de segment plus complexes. Peut introduire un retard notable dans la diffusion de la personnalisation. |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle

**Détails de configuration clés :**

- Utilisez le créateur de segments pour définir des règles d’audience à l’aide d’attributs comportementaux
- Vérifiez l’éligibilité Edge en confirmant que l’expression de règle de segment utilise uniquement les fonctions prises en charge (comparaisons d’attributs simples, appartenance à un segment).
- Définissez la politique de fusion sur la politique de fusion Edge-active configurée dans F4
- Prévisualiser la population de l’audience pour valider le segment renvoie les résultats attendus
- Pour les audiences basées sur les pages vues en session, utilisez des attributs au niveau de l’événement de la session en cours plutôt que des requêtes de série temporelle

**Là où les options divergent :**

**Pour L’Option A (Basée Sur Des Règles) :**
Créez des segments d’audience distincts pour chaque variante de contenu. Chaque segment représente une condition comportementale spécifique (par exemple, « Référence = Google AND Geo = US » mappe à la variante de contenu A). Le nombre d’audiences est égal au nombre de règles de personnalisation.

**Pour L’Option B (Expérimentation) :**
La définition de l’audience est facultative. Si l’expérience cible tous les visiteurs, aucune audience n’est requise ; le fractionnement du trafic gère l’affectation de variantes. Si l’expérience cible un sous-ensemble spécifique (par exemple, uniquement les visiteurs mobiles), définissez une audience de ciblage unique pour l’éligibilité de l’expérience.

**Pour L’Option C (Prise De Décision) :**
Définissez des audiences à utiliser comme règles d’éligibilité sur les éléments de contenu. Ces audiences déterminent quels visiteurs remplissent les critères pour quels éléments de contenu dans la politique de décision. Le moteur de décision gère la sélection de contenu parmi les éléments éligibles.

**Documentation Experience League :**

- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Phase 3 : création de contenu et création de variantes

**Fonction d’application :** AJO : création de messages, AJO : expérimentation de contenu (option B), AJO : prise de décision (option C)

Créez des variantes de contenu personnalisées qui seront diffusées aux visiteurs en fonction de l’appartenance à l’audience (option A), de l’affectation de l’expérience (option B) ou de la logique de prise de décision (option C). Cette phase couvre la création de contenu à l’aide du concepteur web d’AJO ou de l’éditeur d’expérience basé sur du code, ainsi que la configuration d’expérience ou de prise de décision qui régit la manière dont le contenu est sélectionné.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : approche de création de contenu** — Comment les variantes de contenu web doivent-elles être créées ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Éditeur visuel web | L’équipe marketing peut modifier visuellement les éléments de page sans code | Nécessite l’extension du navigateur. Idéal pour les modifications de texte, d’image et de CTA. Limité à la modification des éléments de page existants. |
| Éditeur d’expérience basé sur le code | Le contenu nécessite des données structurées (JSON) rendues par le code de l’application | Flexibilité maximale. Nécessite une implémentation du développeur pour utiliser la payload. Idéal pour les composants dynamiques et les SPA. |
| Éditeur de code HTML/CSS | Les modifications de contenu nécessitent un HTML ou un CSS personnalisé | Contrôle de code direct. Nécessite une expertise HTML/CSS. Idéal pour les modifications de disposition complexes. |

>[!NOTE]
>**Décision : jetons Personalization** — Le contenu doit-il inclure une personnalisation dynamique à l’aide de profils ou d’attributs contextuels ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Variantes de contenu statique | Chaque variante est un élément de contenu fixe sans jetons dynamiques | Approche la plus simple. Le contenu est prévisible et facile à contrôler. Aucun risque de valeurs d’attribut manquantes. |
| Contenu dynamique avec expressions de personnalisation | Le contenu comprend des jetons de style Handlebars qui se résolvent sur les attributs de profil ou d’événement (par exemple, nom de ville, source de référence) | Contenu plus pertinent. Nécessite des valeurs de secours pour les attributs qui peuvent être nuls sur les profils anonymes. Utilisez la syntaxe `{{profile.homeAddress.city}}` avec les assistants . |
| Blocs de contenu conditionnel | Le rendu de différents blocs de contenu est basé sur des conditions d’attribut dans une seule variante | Réduit le nombre de variantes distinctes nécessaires. Augmente la complexité du contenu. Idéal pour les variations mineures dans une mise en page partagée. |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Campagnes > Sélectionner une campagne > Modifier le contenu

**Détails de configuration clés :**

- Créer du contenu à l’aide du concepteur web (modifications visuelles) ou de l’éditeur d’expérience basé sur du code (payload JSON)
- Utilisez l’éditeur d’expression de personnalisation pour insérer des jetons dynamiques à partir des attributs de profil Edge
- Configurer le contenu de secours pour les jetons de personnalisation qui peuvent être vides sur les profils anonymes
- Prévisualiser le contenu avec des profils de test pour vérifier le rendu dans tous les scénarios

**Là où les options divergent :**

**Pour L’Option A (Basée Sur Des Règles) :**
Créez une variante de contenu distincte pour chaque segment d’audience défini à la phase 2. Liez chaque variante à son audience cible à l’aide de règles de contenu conditionnel dans la configuration de la campagne. Assurez-vous qu’une variante de contenu par défaut existe pour les visiteurs qui ne correspondent à aucune règle d’audience.

**Pour L’Option B (Expérimentation) :**
Variantes du traitement de création (A, B, C, etc.) pour l’expérience. Activez l’expérimentation de contenu sur la campagne, définissez des variantes de traitement avec leur contenu, définissez des pourcentages d’affectation de trafic et configurez la mesure de succès.

- Définir 2 à 10 variantes de traitement avec un contenu distinct
- Définissez l’affectation du trafic (par exemple, 50/50 pour A/B ou répartition pondérée pour les tests à faible risque).
- Vous pouvez éventuellement inclure un groupe d’exclusion (par exemple, 10 % reçoit le contenu par défaut) pour mesurer l’effet élévateur incrémentiel
- Sélectionnez la mesure de succès : ouvertures uniques, clics uniques, conversions ou mesure personnalisée.
- Définissez le seuil de confiance : 95 % pour les tests standards, 99 % pour les décisions à enjeux élevés, 90 % pour l’apprentissage directionnel
- **Navigation dans l’interface utilisateur :** Campaign > Expérience de contenu > Ajouter un traitement > Affectation du trafic > Mesure de succès

**Pour L’Option C (Prise De Décision) :**
Configurez la pile de composants Decisioning et intégrez-la à la campagne.

1. **Créer des emplacements** — Définir où apparaîtront les éléments de contenu sur la page (Web HTML, Web JSON, Web Image)
   - **Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Emplacements
2. **Définir des règles d’éligibilité** — Créez des règles basées sur les attributs de profil Edge qui déterminent les visiteurs éligibles pour chaque élément de contenu
   - **Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Règles
3. **Créer des éléments de contenu (offres)** — Créez des éléments de contenu personnalisés avec des représentations pour chaque emplacement, des règles d&#39;éligibilité, une priorité et une limitation facultative
   - **Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Offres > Créer une offre
4. **Créer un contenu de secours** — Définir un élément de secours renvoyé lorsqu&#39;aucun élément personnalisé ne se qualifie
   - **Navigation dans l’interface utilisateur** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Offres > Créer une offre de secours
5. **Organiser en collections** — Regroupez les éléments de contenu à l’aide de qualificateurs de collection (balises) et créez des collections
   - **Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Qualificateurs de collection/Collections
6. **Créer une politique de décision** — Liez les emplacements aux collections et sélectionnez la stratégie de classement (en fonction de la priorité, de la formule ou de l&#39;IA)
   - **Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Composants > Gestion des décisions > Décisions > Créer une décision

**Documentation Experience League :**

- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canal d’expérience basé sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4 : configuration de la campagne et de la diffusion

**Fonction d’application :** AJO : exécution de campagne

Créez et activez la campagne web AJO qui lie la surface web (phase 1), le ciblage d’audience ou la configuration de l’expérience (phases 2-3), ainsi que les variantes de contenu (phase 3) dans une unité livrable. La campagne contrôle quand et comment le contenu personnalisé est diffusé aux visiteurs.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : type de campagne** — Comment la campagne doit-elle être déclenchée ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Campagne planifiée (toujours active) | Personalization doit s’exécuter en continu pour tous les visiteurs éligibles | Définissez une date de début sans date de fin pour la personnalisation permanente. L’évaluation de l’audience se produit à la périphérie en temps réel. Les plus courants pour la personnalisation web. |
| Campagne planifiée (limitée dans le temps) | Personalization est lié à une période de promotion ou à un événement saisonnier spécifique | Définissez des dates de début et de fin explicites. Campaign se désactive automatiquement à la date de fin. Idéal pour les campagnes promotionnelles. |
| Campagne déclenchée par l’API | La diffusion Personalization doit être déclenchée par un événement système externe | Nécessite une intégration d’API. Moins courant pour la personnalisation web anonyme. À utiliser lorsqu’un système principal doit contrôler l’activation de la personnalisation. |

**Navigation dans l’interface utilisateur** [!DNL Journey Optimizer] > Campagnes > Créer une campagne

**Détails de configuration clés :**

- Sélectionnez le canal web et la surface web configurée à la phase 1
- Lier l’audience cible (pour l’option A), configurer les paramètres de l’expérience (pour l’option B) ou incorporer la décision (pour l’option C)
- Définir le planning de la campagne (date de début, date de fin ou valeur toujours activée)
- Configurez le capping de la fréquence au niveau de la campagne, le cas échéant.
- Examiner toutes les configurations et activer la campagne

**Là où les options divergent :**

**Pour L’Option A (Basée Sur Des Règles) :**
Créez une campagne par règle de personnalisation, chacune ciblant une audience Edge différente avec sa variante de contenu correspondante. Vous pouvez également utiliser une seule campagne avec des règles de contenu conditionnel qui mappent l’appartenance de l’audience aux variantes de contenu dans une même campagne.

**Pour L’Option B (Expérimentation) :**
Créez une campagne unique avec l’expérimentation de contenu activée. La configuration de l’expérience (variantes, affectation du trafic, mesure de succès) a été définie au cours de la phase 3. Activez la campagne pour démarrer l’expérience.

**Pour L’Option C (Prise De Décision) :**
Créez une campagne qui incorpore la politique de décision configurée au cours de la phase 3. L’action de contenu de la campagne fait référence à la portée de décision, qui déclenche le moteur de prise de décision à la périphérie. Activez la campagne pour commencer la diffusion de contenu basée sur la prise de décision.

**Documentation Experience League :**

- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Phase 5 : Rapport et analyse des performances

**Fonction d’application :** AJO : Rapports et analyse des performances

Surveillez les performances de personnalisation à l’aide des rapports intégrés d’AJO et étendez éventuellement l’analyse avec CJA pour obtenir des informations cross-canal plus précises. Cette phase couvre l’accès aux rapports de campagne dynamiques et historiques, la révision des résultats des expériences et la création d’espaces de travail d’analyse personnalisés.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : Profondeur des rapports** — Quelle doit être la profondeur de l’analyse des performances ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rapports natifs AJO uniquement | Les mesures de base de diffusion et d’engagement sont suffisantes | Fournit des mesures d’impression, de clic, de taux de clics et de conversion prêtes à l’emploi. Disponible immédiatement dans l’interface utilisateur de Campaign. Personnalisation limitée. |
| Rapports AJO + analyse CJA | Une analyse approfondie de funnel, une comparaison des cohortes ou une mesure de l’impact cross-canal est nécessaire | Nécessite une connexion CJA et une vue de données liées aux jeux de données AJO. Permet l’analyse de structure libre, les mesures calculées personnalisées, la modélisation d’attribution et la publication d’audiences. |

**Navigation dans l’interface utilisateur :** [!DNL Journey Optimizer] > Campagnes > Sélectionner une campagne > Afficher le rapport

**Détails de configuration clés :**

- Accédez au rapport dynamique pendant les campagnes actives pour surveiller la diffusion en temps réel (actualisation toutes les 60 secondes, dernières 24 heures)
- Accédez au rapport historique (à toute heure) une fois la campagne terminée pour une analyse complète (le remplissage complet peut prendre jusqu’à 2 heures).
- Pour l’option B (expérimentation) : consultez le rapport d’expérience pour la comparaison des performances du traitement, les intervalles de confiance et la déclaration du gagnant
- Pour l’analyse CJA : assurez-vous qu’une connexion CJA comprend des jeux de données d’événement d’expérience AJO et qu’une vue de données est configurée avec des mesures de personnalisation web

**Là où les options divergent :**

**Pour L’Option A (Basée Sur Des Règles) :**
Consultez les rapports de campagne pour chaque segment d’audience afin de comparer les mesures de diffusion et d’engagement entre les variantes de contenu personnalisées. Utilisez CJA pour créer un espace de travail de comparaison qui mesure l’impact de la conversion du contenu personnalisé par rapport au contenu par défaut.

**Pour L’Option B (Expérimentation) :**
Consultez le rapport d’expérience pour connaître la confiance statistique, l’effet élévateur de traitement et l’identification du gagnant. Attendez que le seuil de confiance soit atteint avant de déclarer qu’une expérience est probante. Appliquez le contenu gagnant comme variante permanente (en passant à l’option A pour la diffusion en cours).

- **Navigation dans l’interface utilisateur :** Campagne > Expérience de contenu > Afficher le rapport
- **Experience League:** [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

**Pour L’Option C (Prise De Décision) :**
Examinez les mesures de performances de prise de décision, notamment les taux d’impression des offres, la fréquence de sélection et l’attribution de conversion par élément de contenu. Analysez les performances des stratégies de classement et déterminez si le contenu de secours est diffusé trop fréquemment (indiquant que les règles d’éligibilité sont trop restrictives).

**Documentation Experience League :**

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Calculs statistiques dans l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage pour ce modèle de cas d’utilisation.

### Mécanismes de sécurisation et limites

Examinez les mécanismes de sécurisation suivants avant et pendant la mise en œuvre.

- Les segments Edge sont limités à des vérifications d’attributs simples et à l’appartenance à un segment (aucune requête de série temporelle ou agrégation complexe). [Éligibilité de la segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Une seule politique de fusion peut être active sur le serveur Edge par sandbox : [&#x200B; Mécanismes de sécurisation de profil &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum de 500 campagnes actives en direct par sandbox — [Mécanismes de sécurisation Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 10 variantes de traitement par expérience de contenu — [limites de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 10 000 offres personnalisées approuvées par sandbox (option C) — [&#x200B; Mécanismes de sécurisation de la gestion des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum de 30 emplacements par décision (option C) — [Mécanismes de sécurisation Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Les modèles de classement AI nécessitent au moins 1 000 événements de conversion pour la formation (option C)
- [!DNL Edge Network] du temps de réponse SLA : &lt; 200 ms pour les segments évalués par Edge
- Expiration de profil pseudonyme : configurable de 14 à 365 jours pour les profils ECID uniquement
- Les rapports dynamiques sont actualisés toutes les 60 secondes et affichent les dernières 24 heures de données
- Le remplissage complet des rapports historiques peut prendre jusqu’à 2 heures après la fin de la campagne

### Pièges courants

Évitez les erreurs d’implémentation courantes suivantes.

- **[!DNL Web SDK]de ne pas envoyer de signaux comportementaux à AEP :** vérifiez que le service [!DNL Adobe Experience Platform] est activé pour le flux de données et que le jeu de données d’événement est correctement mappé. Sans cela, les profils Edge ne sont pas renseignés et l’évaluation de l’audience échoue silencieusement - le visiteur reçoit le contenu par défaut sans indication d’erreur.
- **Audience Edge ne renvoyant aucune qualification :** la segmentation Edge a des exigences d’éligibilité strictes. Les requêtes de série temporelle, les fonctions d’agrégation et les requêtes d’entités multiples ne sont pas éligibles pour Edge. Réécrivez l’expression de règle de segment à l’aide de comparaisons d’attributs simples ou de contrôles d’appartenance au segment.
- **Politique de fusion non active sur le serveur Edge :** si la politique de fusion utilisée par le segment d’audience ne comporte pas de `isActiveOnEdge: true`, les recherches de profil Edge échoueront et la personnalisation ne sera pas diffusée. Une seule politique de fusion par sandbox peut être active sur le serveur Edge. Vérifiez qu’il n’y a aucun conflit.
- **Personalization scintillement au chargement de la page :** l’appel [!DNL Web SDK] de `sendEvent` qui récupère les propositions de personnalisation doit s’exécuter avant que la page n’effectue le rendu de la zone de contenu cible. Implémentez le masquage préalable des fragments de code ou le rendu asynchrone pour empêcher le contenu par défaut de clignoter avant le chargement du contenu personnalisé.
- **Le contenu n’est pas rendu lors des modifications d’itinéraire SPA :** les applications monopages nécessitent des appels `sendEvent` explicites avec des informations d’affichage mises à jour lors des modifications d’itinéraire. Sans cela, l’[!DNL Edge Network] ne réévalue pas la personnalisation pour la nouvelle vue.
- **Expérience n’atteignant pas la signification statistique :** un volume de trafic insuffisant ou un trop grand nombre de variantes de traitement diluent la taille de l’échantillon par variante. Réduisez le nombre de variantes ou augmentez la durée de l’expérience. N’arrêtez pas les expériences trop tôt, car les résultats peuvent être trompeurs.
- **Prise de décision renvoyant uniquement le contenu de secours :** vérifiez que les éléments de contenu personnalisés sont approuvés, dans leur période de validité, et que les règles d’éligibilité correspondent aux attributs de profil Edge du visiteur anonyme. Vérifiez également que les limites de limitation n’ont pas été atteintes.

### Bonnes pratiques

Suivez ces recommandations pour une implémentation réussie.

- **Démarrer simple, puis itérer :** commencez par l’option A (basée sur des règles) pour la personnalisation initiale, puis utilisez l’option B (expérimentation) pour valider les hypothèses et l’option C (prise de décision) pour les cas d’utilisation avancés. Chaque option s’appuie sur l’infrastructure de base.
- **Utiliser le masquage préalable pour empêcher le scintillement :** implémentez le fragment de code de masquage préalable AEP sur les pages où la personnalisation sera diffusée. Cela masque la zone de contenu cible jusqu’à ce que le contenu personnalisé soit prêt à être rendu, évitant le scintillement visuel.
- **Concevoir délibérément un contenu de secours :** le contenu par défaut (non personnalisé) doit être une expérience de haute qualité en soi. Les visiteurs et visiteuses qui ne remplissent pas les critères de la personnalisation, ou lorsque la réponse [!DNL Edge Network] est retardée, ne doivent pas bénéficier d’une expérience détériorée.
- **Valider l’éligibilité Edge avant de créer des audiences :** avant d’investir dans le développement de règles d’audience, vérifiez que l’expression de règle de segment est éligible Edge en consultant les critères d’éligibilité dans Experience League. Les expressions non éligibles reviendront silencieusement à l’évaluation par lots ou en flux continu avec une latence inacceptable pour ce modèle.
- **Surveiller les performances des diffusions Edge :** configurez la surveillance des alertes pour les temps de réponse [!DNL Edge Network] et les échecs de diffusion de personnalisation. Les problèmes de diffusion Edge sont invisibles pour le visiteur (il voit le contenu par défaut) et peuvent ne pas être détectés sans surveillance proactive.
- **Configurer l’expiration des profils pseudonymes :** définissez des périodes d’expiration appropriées pour les profils Edge anonymes afin d’équilibrer la personnalisation intersessions (en reconnaissant les visiteurs récurrents), la conformité en matière de confidentialité et la gestion du stockage.
- **Test avec des profils représentatifs :** lors de la prévisualisation de contenu personnalisé, utilisez des profils de test qui représentent les scénarios de visiteur anonyme réels (aucune donnée de gestion de la relation client, historique comportemental limité, divers emplacements géographiques et appareils).

### Décisions de compromis

Tenez compte des compromis suivants lors de la planification de votre implémentation.

>[!NOTE]
>**Compromis : largeur de Personalization par rapport à la complexité de l’implémentation**
>
>Une personnalisation plus granulaire (de nombreuses audiences, de nombreuses variantes de contenu) produit des expériences plus pertinentes, mais augmente la complexité de la configuration et les frais généraux de production de contenu.
>
>- **La personnalisation à grande échelle favorise :** simplicité, délai de mise sur le marché plus rapide, coût de production du contenu plus faible. Un petit nombre d’audiences et de variantes couvre la majorité des visiteurs avec une personnalisation significative.
>- **La personnalisation granulaire privilégie :** pertinence maximale, effet élévateur d’engagement plus élevé, meilleurs taux de conversion. De nombreuses audiences et variantes traitent de signaux comportementaux spécifiques avec du contenu personnalisé.
>- **Recommandation :** commencez par 3 à 5 règles de personnalisation à fort impact ciblant les segments de visiteurs les plus courants (par exemple, source de référence, type d’appareil, région géographique). Mesurez l’impact, puis développez pour obtenir des règles plus granulaires en fonction des performances observées et de la valeur commerciale.

>[!NOTE]
>**Compromis : déterminisme basé sur des règles et optimisation basée sur l’IA**
>
>Les approches basées sur des règles (option A) donnent à l’entreprise un contrôle total sur le contenu que chaque visiteur voit. Les approches classées par l’IA (option C) optimisent la sélection de contenu au fil du temps, mais réduisent la visibilité sur les raisons pour lesquelles un contenu spécifique a été sélectionné.
>
>- **Favoris basés sur des règles :** prévisibilité, vérifiabilité, contrôle d’entreprise. Les équipes marketing savent exactement quel contenu chaque segment reçoit et peuvent expliquer la logique aux parties prenantes.
>- Favoris pilotés par l’IA **:** Optimisation des performances, évolutivité et amélioration continue. Le modèle d’IA détecte les affinités contenu-visiteur que l’écriture de règles humaine peut ignorer.
>- **Recommandation :** utilisez des règles pour les décisions de contenu à enjeux élevés où la cohérence de la marque et la transparence des parties prenantes sont primordiales. Utilisez le classement par l’IA pour les catalogues de contenu volumineux où la gestion manuelle des règles devient difficile et où l’optimisation continue offre un effet élévateur mesurable.

>[!NOTE]
>**Compromis : persistance du profil anonyme par rapport à la conformité en matière de confidentialité**
>
>Une expiration de profil pseudonyme plus longue permet une meilleure personnalisation entre sessions (reconnaissance des visiteurs récurrents, création d’un contexte comportemental au fil du temps). Une expiration plus courte améliore la conformité en matière de confidentialité et réduit les coûts de stockage.
>
>- **Une expiration plus longue favorise :** profils anonymes plus riches, une meilleure reconnaissance des visiteurs récurrents, plus de données pour les décisions de personnalisation. Définissez l’expiration sur 90 à 365 jours.
>- **Une durée d’expiration plus courte est préférable :** respect de la confidentialité (RGPD, CCPA), coûts de stockage réduits, risque réduit de données de profil obsolètes. Définissez l’expiration sur 14 à 30 jours.
>- **Recommandation :** aligner l’expiration sur la politique de consentement des cookies et les exigences de confidentialité de votre organisation. Pour la plupart des mises en œuvre, un délai de 30 à 90 jours offre un équilibre raisonnable entre la valeur de personnalisation et la conformité en matière de confidentialité.

## Documentation connexe

Les ressources Experience League ci-après fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

**Expériences de canal web et basées sur du code**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canal d’expérience basé sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Configuration de l’expérience basée sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Audiences et segmentation**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization et contenu**

- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Expérimentation de contenu**

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Gestion des décisions**

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Création de règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campagnes**

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Création d’une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]et collecte de données**

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation des balises](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identité et profil**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**modélisation des données**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Rapports et analyses**

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Gouvernance et confidentialité des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Mécanismes de sécurisation**

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
