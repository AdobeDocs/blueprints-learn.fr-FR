---
title: Correspondance de segment
description: En savoir plus sur [!UICONTROL Correspondance de segment] pour Adobe Experience Platform (AEP). [!UICONTROL Correspondance de segment] est un service de collaboration de données qui vous permet d’échanger des données de segment d’après des identifiants de secteur communs d’une manière sécurisée, régie et respectueuse de la vie privée.
solution: Experience Platform
source-git-commit: a5bf86b8606d40a0686c667f83516e3b495350b8
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 0%

---

# Correspondance de segment

La correspondance de segment permet aux marques partenaires de partager des audiences dans leurs environnements Experience Platform respectifs. La clé pour les marques est de se connecter avec les clients en fonction des données collectées à partir de leurs relations directes avec les consommateurs. Grâce à de meilleurs systèmes de gouvernance, d’autorisations et de gestion des préférences, les marketeurs peuvent améliorer davantage leurs audiences authentifiées propriétaires avec des partenaires clés.

[!UICONTROL Correspondance de segment] est un service de collaboration des données qui permet aux clients Experience Platform (AEP) (appelés _partenaires_) pour échanger des données de segment en fonction d’identifiants de secteur communs d’une manière sécurisée, régie et respectueuse de la confidentialité.

Le service permet aux clients d’identifier en toute sécurité et de manière neutre les identifiants correspondants sans avoir à dévoiler l’intégralité de leur base de données. Les partenaires reçoivent uniquement des attributs désignés (nom du segment) pour les ID qui se chevauchent, ce qui permet un partage plus rapide et plus facile d’une manière contrôlable et régie par le consentement.

[!UICONTROL Correspondance de segment] utilise la gouvernance des données AEP et le cadre de consentement comme colonne vertébrale. Il est disponible pour tous les clients B2C et B2P Real-time Customer Data Platform. Fonctionnalités clés de [!UICONTROL [!UICONTROL Correspondance de segment]] inclure :

* Partage de segments pour les clients consentants qui se chevauchent
* Rapports de chevauchement de pré-partage pour obtenir des informations sur le volume de correspondance estimé
* Stratégie DULE entièrement intégrée et application des autorisations
* Noeud de structure de consentement du partage de données
* Flux de données pour l’organisation des segments et des partenaires

## Applications

Marque vers l’éditeur :

Le &quot;cas d’utilisation d’éditeur&quot; est le plus affecté par l’obsolescence des cookies tiers et des données d’ID de publicité mobile. Ce cas pratique a un impact majeur sur l’industrie des médias et du divertissement qui se concentre sur la vente de la publicité comme modèle commercial. [!UICONTROL Correspondance de segment] est un chemin d’accès pour les éditeurs disposant d’un grand public propriétaire qui souhaitent collaborer directement avec leurs annonceurs. Les annonceurs peuvent collaborer directement avec les éditeurs pour faire de la publicité par rapport aux audiences correspondantes sur les propriétés de l’éditeur pour des campagnes de ciblage ou de prospection granulaires.

### Marque à la marque

Les parcours des consommateurs ne sont jamais linéaires. Par exemple, un client peut être fidèle à une compagnie aérienne et à sa société de carte de crédit. En utilisant [!UICONTROL Correspondance de segment], la compagnie aérienne et la société de carte de crédit peuvent créer un partenariat de données pour comprendre les audiences qui se chevauchent, puis personnaliser les offres pour les clients fidèles de chacune des entreprises.

### BU en BU

Les multinationales sont confrontées à des défis liés à la collaboration des données entre des entités commerciales indépendantes. La combinaison de données dans un seul environnement de test peut ne pas être possible en raison de la variabilité des politiques de confidentialité, des acquisitions ou de la gestion des autorisations entre les différentes unités de gestion.

[!UICONTROL Correspondance de segment] aide les équipes marketing disparates des grandes entreprises à collaborer plus efficacement tout en continuant à fonctionner de manière indépendante ;

## Architecture

![Architecture de correspondance de segment](assets/architecture-segment-match.png)

[!UICONTROL Correspondance de segment] n’est pas un marché de données où les données peuvent être achetées. Il s’agit plutôt d’une fonction AEP qui fonctionne avec des données propriétaires avec des partenaires sélectionnés, en utilisant des contrôles de confidentialité et de consentement pour faciliter la collaboration. [!UICONTROL Correspondance de segment] aide à concentrer les efforts sur l’amélioration des relations client et l’augmentation de la marque. Elle est bénéfique lorsque des marques ou des relations de partenaires préexistantes existent. [!UICONTROL Correspondance de segment] Cette expérience est facile à gérer, évolutive et permet aux administrateurs de partager des segments d’une manière d’opt-in et contrôlable.

[!UICONTROL Correspondance de segment] active :

* Segmenter les données d’appartenance à des organisations à l’aide d’identifiants de niveau personnel standard, tels que le courrier électronique haché ou le numéro de téléphone.
* Interface utilisateur de partage d’audience et workflows avec notifications
* Estimations de chevauchement pré-partagées
* Configuration des partenaires en libre-service
* Chevauchement sur certains espaces de noms normalisés (courrier électronique haché, téléphone haché, ECID, IDFA, GAID)
* Application du consentement au partage des données
* Gestion du cycle de vie des audiences partagées
* Application DULE dans le workflow de partage
* Mises à jour par lots quotidiennes

[!UICONTROL Correspondance de segment] permet de créer une expérience client interconnectée. Les identifiants durables pris en charge sont les emails hachés, les numéros de téléphone hachés et les identifiants comme ECID, IDFA et GAID. Les clients peuvent créer des flux qui correspondent aux données d’audience et les déplacent entre les environnements de test de marque, avec une gouvernance solide, une transparence et des fonctionnalités de révocation à utiliser dans les activités publicitaires et marketing.

## Conditions préalables

Conditions préalables pour [!UICONTROL Correspondance de segment] sont :

* RT-CDP principal sous licence
* Les identifiants hachés standard pris en charge sont les e-mails hachés SHA256, le téléphone haché, l’ECID, l’Apple IDFA et GAID.
* Structure de confidentialité et stratégie de consentement
* Contrats de partage de données en place entre les clients

## Sécurité

### RBAC

Le [!UICONTROL Correspondance de segment] Le flux de gestion des partenaires est sécurisé par RBAC. Seules les personnes disposant des autorisations appropriées peuvent initier, accepter ou gérer des partenaires. Vous pouvez le faire dans la section Data Ingestion du profil de produit. Les autorisations suivantes sont requises :

![Connexion au partage d’audience](assets/data-ingestion.png)

| Autorisation | Description |
|---|---|
| **Gestion des connexions du partage d’audience** | Cette autorisation vous permet d’effectuer le processus de négociation des liens avec les partenaires, qui connecte deux organisations IMS pour activer [!UICONTROL Correspondance de segment] flux. |
| **Gestion des partages d’audience** | Cette autorisation vous permet de créer, modifier et publier des flux (le module de données utilisé pour [!UICONTROL Correspondance de segment]) avec des partenaires principaux (partenaires qui ont été connectés par l’utilisateur administrateur avec **Connexions avec le partage d’audience** Accès). |

Consultez la [documentation officielle](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#understanding-segment-match-permissions) pour en savoir plus sur les autorisations.

### Connect ID

Le processus de connexion des partenaires est géré par le **[!UICONTROL Connect ID],** qui est un identifiant généré de manière aléatoire qui correspond à un environnement de test AEP spécifique. Cet identifiant de connexion est nécessaire pour lancer et gérer des environnements de test de partenaire. Il est également possible de régénérer l’identifiant de connexion pour reconfigurer une connexion de partenaire, si nécessaire.

### Gouvernance

Tout jeu de données ou attribut de données avec *C11* le libellé du contrat est limité pour la variable [!UICONTROL Correspondance de segment] service. Les segments utilisant ces attributs ne peuvent pas être utilisés pour [!UICONTROL Correspondance de segment]. Cela permet de contrôler quels segments peuvent ou ne peuvent pas être utilisés pour [!UICONTROL Correspondance de segment]. En outre, les stratégies personnalisées et les actions marketing créées sont également appliquées. Par défaut, les stratégies sont désactivées et doivent être activées pour l’application. Les restrictions telles que le marketing par e-mail et la publicité sur site qui sont sélectionnées lors du partage de segments sont également propagées et partagées avec les partenaires.

### Consentement

Les paramètres de consentement pour [!UICONTROL Correspondance de segment] peut être géré de la manière suivante :

* Au niveau de l’organisation, lors de l’intégration, à l’aide du paramètre d’exclusion ou d’inclusion pour les vérifications de consentement.

   Ce paramètre détermine si les données utilisateur peuvent être partagées ou non. La valeur par défaut est définie sur exclusion, indiquant que les données utilisateur peuvent être partagées en supposant que le client AEP a déjà le consentement requis pour l’utilisation du partage de données. Ce paramètre peut être modifié pour s’inscrire en contactant le gestionnaire de compte Adobe, en mettant en place un contrôle supplémentaire pour forcer les clients AEP à suivre explicitement le consentement.

* La définition de l’attribut share spécifique aux identités (idSpecific) à l’aide de la propriété [Groupe de champs Consentements et Préférences](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=en).

   Ce groupe de champs fournit un champ de type objet unique, les consentements, pour capturer les informations de consentement et de préférence. [!UICONTROL Correspondance de segment], par défaut, inclut toutes les identités qui n’ont pas été explicitement désactivées, par exemple :

   ```
   "share": {
   `                `"val": "n"
   `     `}
   ```

   Ce paramètre peut être modifié en contactant le gestionnaire de compte Adobe afin d’inclure uniquement les identités avec inclusion explicite, par exemple :

   ```
   "share": {
   `                `"val": "y"
   `     `}
   ```

### Alertes

Des alertes sont générées lorsqu’une connexion de partenaire est lancée ou lorsque des flux de segment sont partagés avec des partenaires.

## Workflow de configuration

Le workflow de configuration de la connexion des partenaires est géré à l’aide du reporting (RBAC), comme mentionné ci-dessus. Une fois les autorisations appropriées en place, la connexion à un environnement de test partenaire nécessite que l’identifiant de connexion de cet environnement de test/instance au sein de l’organisation du partenaire soit partagé.

Une fois qu’une connexion est demandée au partenaire d’envoi, elle doit être approuvée du côté récepteur pour garantir une configuration du partenaire sécurisée. L’établissement d’une liaison avec le partenaire garantit que l’accord existe entre les deux organisations et permet à l’Adobe de faciliter la [!UICONTROL Correspondance de segment] processus au nom de l’organisation. Une fois la connexion approuvée et en principal état, le processus de partage de segment peut être lancé de part et d’autre.

### Partage de segments

Le partage de segments avec le partenaire se produit uniquement lorsqu’il existe une correspondance sur l’identifiant sélectionné. Il peut y avoir une relation de partenaire de type &quot;un à plusieurs&quot;, ce qui signifie que les segments peuvent être partagés avec plusieurs partenaires.

Pour lancer le partage de segments une fois la connexion du partenaire configurée, le partenaire d’envoi doit créer un flux. Sélectionnez ensuite les cas d’utilisation marketing ou les actions dont les données de segment doivent être exclues, ainsi que les identifiants durables. Les segments pertinents peuvent ensuite être ajoutés au flux pour le partage.

Dans le cadre de ce workflow de partage de segments, le partenaire d’envoi peut découvrir des segments à forte valeur potentielle par le biais de recouvrements estimés avant tout déplacement de données.

Le flux de processus global est le suivant :

![Partage de segments](assets/segment-sharing.png)

Ces estimations de chevauchement offrent des informations clés, la découverte de partenaires et des données pour alimenter les accords de collaboration sur les données. Aucune donnée de client ou de segment n’est déplacée dans les environnements de test pour obtenir ces mesures d’estimation de chevauchement. Les identités applicables sélectionnées par le client et préhachées dans un environnement de test donné sont ajoutées à une structure de données probabiliste qui permet à l’Adobe d’effectuer des opérations d’union et d’intersection entre elles. Ces opérations aident [!UICONTROL Correspondance de segment] obtenir l’intersection estimée de deux structures de données composées d’identités à partir de deux environnements de test différents sans avoir à comparer les valeurs réelles ;

Le processus de chevauchement d’identités dépend de **export de profil complet quotidien** jeu de données des environnements de test de l’expéditeur et du destinataire afin d’identifier les profils communs qui appartiennent aux segments partagés. Le flux de processus détaillé du processus de chevauchement est illustré ci-dessous :

![Processus de chevauchement des identités](assets/overlap-process.png)

Une fois le partage de segment terminé à partir du partenaire d’envoi, le destinataire reçoit une notification sur le flux de segment partagé. Ce flux de segments doit être activé pour le profil au niveau du récepteur pour lancer le flux de données d’adhésion au segment. Seules les adhésions au segment sont ingérées dans les fragments de profil se chevauchant de l’organisation IMS du récepteur et aucune identité supplémentaire n’est transférée de l’expéditeur au destinataire.

Le segment partagé est disponible sous le `AEPSegmentMatch` de la section **[!UICONTROL Audiences]** dans le **[!UICONTROL Créateur de segments]** et peut être utilisé pour l’inclusion ou la suppression d’audiences lors de la création de segments dans l’environnement de test du récepteur.

Le processus de chevauchement quotidien maintient l’appartenance au segment synchronisé entre l’expéditeur et le destinataire. Le destinataire peut désactiver le profil du flux de segment reçu pour suspendre le processus de partage de segment.

#### Sortie/entrée de segment

Dans le cadre de l’exportation de profil complète, l’état des segments-ID partagés sous l’appartenance au segment pour les profils comporte l’une des valeurs correspondantes : _réalisé_, _exited_ ou _existant_ pour refléter l’état actuel.

Au cours du processus de chevauchement d’identités quotidien, si l’identité correspondante existe dans l’environnement de test du récepteur, ces états d’adhésion aux segments pour les segments partagés sont envoyés au récepteur pour ingestion.

#### Révocation de segment

La révocation/suppression de segments de l’expéditeur est un processus à la demande où la liste de tous les profils avec les ID de segment révoqués est obtenue du destinataire. Les ID de segment sont supprimés de l’appartenance au segment de ces identités et ingérés au destinataire. Cette action remplace le fragment d’adhésion au segment existant, qui supprime l’adhésion pour ce segment.

## Informations complémentaires

* [Correspondance de segment](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#)
* [Autorisations](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=en)
* [Résolution des problèmes](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=en)
* [XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=en)
