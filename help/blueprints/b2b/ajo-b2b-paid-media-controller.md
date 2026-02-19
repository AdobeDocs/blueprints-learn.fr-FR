---
source-git-commit: 9d0eebd5d84671db1c86d73e7e0de50cb926235d
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---
# Présentation

Les équipes marketing qui exécutent des médias achetés B2B à grande échelle sont confrontées à un problème récurrent : **les comptes se retrouvent dans plusieurs campagnes à la fois** (persona, conscience de la catégorie, mené par une solution, poursuite), ce qui dilue les messages, provoque la fatigue de l’audience et force le travail manuel de liste (chargements, exclusions et suppression) sur LinkedIn Account Match (destination du compte). Sans **hiérarchisation en cascade** et **affectation de campagne automatisée**, il n’y a pas d’emplacement unique pour décider quel compte reçoit quel message et les opérations ne sont pas dimensionnées.

Le **Paid Media Controller** est une solution parfaite pour résoudre ce problème. Il utilise **Adobe Journey Optimizer B2B edition (AJO B2B)** et **Adobe Experience Platform (AEP)** ensemble : un **parcours de compte** lit une audience de compte qualifié à partir de Real-Time CDP, applique **logique de chemin partagé (cascade)** pour affecter chaque compte à exactement un niveau de campagne, et **active chaque chemin directement** vers des destinations de médias achetés (**par exemple, audiences correspondantes LinkedIn**), sans remise de liste manuelle. Le résultat est un contrôle de précision, moins de chevauchement et un modèle répétable pour l’orchestration de médias achetés B2B multicanaux.

## Cas d’utilisation : l’histoire d’un spécialiste marketing : l’importance d’un contrôleur

*Maya dirige les médias payants pour une marque B2B mondiale. Son équipe gère des dizaines de campagnes : sensibilisation aux bases, intention de la catégorie (Parcours, données, contenu), programmes pilotés par des solutions, campagnes de persona et poursuites incontournables. Elle a un problème.*

**Le problème :** les mêmes comptes s’affichent dans plusieurs campagnes. Un compte de Parcours à forte intention figure également sur une vaste liste de sensibilisation ; un compte de poursuite reçoit toujours des annonces persona. Les téléchargements et exclusions de liste sont manuels. Chaque fois que le service commercial met à jour une liste « must-win » ou qu’une nouvelle campagne personnalisée est lancée, son équipe réexporte les audiences, réconcilie les chevauchements dans les feuilles de calcul et les recharge sur LinkedIn et d’autres plateformes. Il est lent, sujet aux erreurs et ne se met pas à l’échelle.

**Ce qu’elle souhaite :** un emplacement où chaque compte qualifié est évalué une fois, attribué à la campagne *la plus pertinente* à l’aide de règles de priorité claires (cascade) et envoyé automatiquement à la bonne destination de média payant. Aucune remise manuelle de liste. Lorsque les données ou la stratégie changent, le système réévalue et déplace les comptes entre les campagnes sans que son équipe ne touche aux listes.

**Réponse d’Adobe :** grâce à la collaboration entre **AJO B2B et AEP** Maya peut exécuter un seul parcours **Contrôleur de médias payants** : AEP et Real-Time CDP détiennent les données et une audience principale de « comptes qualifiés » ; AJO B2B exécute un parcours de compte qui utilise **la logique de chemin partagé** (cascade) pour acheminer chaque compte vers le niveau approprié ; par exemple, Poursuites ciblées → campagne → Persona → Sensibilisation à la base → la catégorie et **Activer vers la destination** envoie chaque chemin vers la campagne LinkedIn appropriée (ou autre). Un parcours, une source de vérité, aucune liste manuelle n&#39;exporte. C’est le modèle du contrôleur de médias payants. Et c’est ainsi qu’Adobe assure précision et évolutivité pour les médias payants B2B.

## Importance pour les entreprises B2B :

Les entreprises qui adoptent ce modèle peuvent éliminer complètement la logique de suppression et d’exclusion manuelle (par exemple, 100 % de la résolution de chevauchement gérée dans le parcours), passer à **dizaines de milliers de comptes** par le biais d’un seul contrôleur et conserver une **source unique de vérité** pour quel compte va à quelle campagne. Le système **s’adapte automatiquement** à mesure que le focus de la campagne, les audiences cibles et les objectifs de vente changent, sans devoir réexporter les listes ou procéder à un nouveau chargement sur chaque plateforme. Pour toute entreprise B2B exécutant plusieurs campagnes de médias payants, le modèle de contrôleur de médias payants offre la clarté, le contrôle et l’automatisation que ne permettent pas les workflows de listes manuelles.

Les KPI suivants s’alignent bien sur la mesure du succès :

- **Sensibilisation :** les comptes cibles voient-ils les bonnes annonces et passent-ils aux bonnes campagnes à un taux plus élevé ?
- **Engagement :** l’engagement et la conversion sont-ils meilleurs lorsque le chevauchement est supprimé ?
- **Efficacité :** dans quelle mesure le travail de liste manuelle (chargements, exclusions, suppression) a-t-il diminué ?
- **Coût :** comment le coût par compte ou opportunité acquis change-t-il avec l’orchestration automatisée ?

## Orchestration des Parcours de médias payants

**Un cas d’utilisation courant, et l’objectif de ce plan directeur, est l’orchestration de Parcours de médias achetés B2B** : s’assurer que chaque compte qualifié est affecté à exactement un niveau de campagne et activé à la destination de médias achetés correcte, sans chevauchement ni remise manuelle.

Le parcours de contrôleur **lit** une audience de compte qualifié (créée dans Real-Time CDP à partir de données AEP), **évalue** chaque compte par le biais de conditions de chemin de partage (cascade) (par exemple, la recherche → personnage → → l’intention de catégorie → fondamentales) et **active** chaque chemin vers la destination correspondante (par exemple, les audiences correspondantes LinkedIn pour chaque campagne).

**Solution axée sur les comptes :** le contrôleur de médias payants se concentre sur les **comptes** et leur **affectation de campagne**. La configuration technique prend en charge les données et les audiences qui représentent des comptes qualifiés et leurs attributs (par exemple, intention, segment, persona), ce qui est nécessaire pour une segmentation réussie au niveau du compte et une orchestration basée sur le parcours.

## Conditions requises

La solution axée sur les comptes nécessite les applications et services suivants :

- **Adobe Journey Optimizer B2B edition** — parcours de compte, logique de chemin de partage (cascade), activer vers la destination.
- **B2B edition Adobe Real-time Customer Data Platform (RTCDP)** — Profils de compte, audiences de compte (par exemple, comptes qualifiés pour les médias achetés).

## Architecture

Flux de haut niveau :

1. **Données et audiences** — AEP contient des profils et des événements ; Real-Time CDP B2B crée des audiences de compte (par exemple, « Comptes éligibles de médias payants ») utilisées comme audience d’entrée de parcours.
2. **Orchestration** — parcours de compte B2B d’AJO : **Lecture d’audience** (comptes qualifiés) → **Chemin de partage** (cascade : par exemple, poursuite d’→ projet piloté par une solution → Persona → catégorie → fondamentale) → **Activation vers la destination** (par chemin d’accès à LinkedIn ou à d’autres médias achetés).
3. **Destinations** — Les canaux médias payants (par exemple, LinkedIn Matched Audiences) reçoivent une activation au niveau du compte à partir de chaque chemin de parcours ; aucune liste manuelle de chargement.

## Diagramme d’architecture

<img src="assets/ajo-b2b-paid-media-activation-architecture.svg" alt="Architecture du contrôleur de médias payants B2B AJO" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Modélisation des données dans B2B AEP

Dans toute orchestration pilotée par les données, la conception de schémas est importante. Les profils de compte et de personne dans AEP/RTCDP doivent inclure les attributs utilisés dans les **conditions de chemin partagé** (par exemple, indicateur de poursuite, intérêt de la solution, persona, catégorie d’intention, score d’engagement). Les schémas B2B (compte professionnel XDM, profil individuel XDM, relationnel) doivent représenter votre hiérarchie et vos sources de données. Pour plus d’informations, consultez les [schémas RTCDP B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) et [la documentation AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/home).

**Remarque :** la logique de chemin partagé dans le parcours utilise les données de profil et, lorsqu’elles sont prises en charge, les données relationnelles. Assurez-vous que les champs dont vous avez besoin pour la logique de cascade sont disponibles dans le parcours.

### Garde-fous

- **Journey Optimizer B2B edition** — Consultez la [description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer-b2b.html) pour connaître les limites de parcours, les limites de nœud et la prise en charge des destinations.
- **Real-Time CDP** — Consultez la section [Mécanismes de sécurisation de RTCDP](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/guardrails/overview) pour connaître les limites de segmentation et d’activation.

## Implémentation

Les étapes suivantes fournissent des conseils pour la mise en œuvre du contrôleur de médias payants avec AJO B2B et AEP.

### Étapes prérequises

1. **Définition des audiences de compte et du modèle de données dans Real-Time CDP B2B.**

   Créez l’**audience de compte qualifiée** (par exemple, « Comptes admissibles de médias payants ») qui entrera dans le parcours du contrôleur. Utilisez le créateur de segments et les attributs de compte/personne qui définissent l’éligibilité (par exemple, zone géographique, segment, statut MQA). Cette audience est le point d’entrée unique du parcours.

2. **Définissez la hiérarchie de la campagne et la logique de division.**

   Documentez l’ordre de la cascade (par exemple, Poursuite → solutions → Persona → Catégorie → Fondamentale) et les conditions de chaque chemin (quels attributs ou audiences qualifient un compte). Assurez-vous que les conditions sont **mutuellement exclusives dans l’ordre** (de haut en bas) : un compte doit correspondre au plus à un chemin, le premier qui évalue true.

3. **Configurer les destinations.**

   Configurez les destinations de médias payants (par exemple, les audiences correspondantes LinkedIn) dans AEP/RTCDP et assurez-vous qu’elles sont disponibles pour activation à partir d’AJO B2B. Mappez les identifiants de compte et tous les attributs requis pour chaque destination.

### Configuration du contrôleur de médias payants

1. **Création du parcours de contrôleur dans AJO B2B.**

   - **Lecture d’audience :** sélectionnez l’audience du compte qualifié dans Real-Time CDP.
   - **Chemin de division :** ajoutez des nœuds dans l’ordre de la cascade. Chaque nœud évalue les conditions (par exemple, « dans l’audience de poursuite », « intérêt de la solution = X », « persona = Y », « catégorie d’intention = Z »). Les comptes qui correspondent sortent de l’activation correspondante ; d’autres passent à la division suivante.
   - **Activer vers la destination :** pour chaque chemin d’accès, ajoutez un nœud Activer vers la destination à la campagne/destination LinkedIn (ou autre) appropriée.

2. **Valider l’exclusivité mutuelle.**

   - Vérifiez que chaque compte n’entre qu’un seul chemin (la première condition correspondante).
   - Vérifier l’activation : les comptes s’affichent dans la bonne destination et sont exclus des campagnes de priorité inférieure comme prévu.

## Diagramme de mise en œuvre

<img src="assets/ajo-b2b-paid-media-controller-canvas.svg" alt="Canevas de contrôleur de médias payants B2B AJO" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

### 4.2.3. Activation de l’audience

1. **Activer vers LinkedIn (et d’autres destinations).**

   Utilisez « Activer vers la destination » dans le parcours pour envoyer chaque chemin à l’audience de média payant appropriée. Aucune exportation ou chargement manuel de liste ; le parcours entraîne l’activation lorsque les comptes traversent des chemins d’accès.

2. **Surveiller et régler.**

   Utilisez les rapports de parcours pour surveiller les volumes par chemin.

## Résumé

Le plan directeur **Paid Media Controller** montre comment **AJO B2B et AEP** fonctionnent ensemble pour offrir aux spécialistes du marketing B2B un moyen unique et automatisé d’affecter des comptes aux campagnes et d’effectuer des activations sur des médias achetés : une audience principale, un parcours, une logique de partage en cascade et une activation directe vers les destinations (aucune remise de liste manuelle). Il établit un modèle répétable pour l’orchestration de médias achetés B2B multicanaux et contribue à réduire le chevauchement, à améliorer la pertinence et à mettre à l’échelle les opérations.

## Documentation connexe

- [Plan directeur de marketing et de gestion des Parcours basé sur les groupes d’achat](https://experienceleague.adobe.com/fr/docs/blueprints-learn/architecture/b2b-activation/b2b-buying-group-journeys) — parcours de compte et de groupe d’achat dans AJO B2B.
- [Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b) — Documentation du produit.
- [Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) — Audiences de compte et activation.
