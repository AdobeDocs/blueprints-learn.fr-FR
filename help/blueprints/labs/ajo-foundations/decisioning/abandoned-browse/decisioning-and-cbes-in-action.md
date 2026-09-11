---
title: Prise de décision et CBE en action
description: Utilisez Postman pour envoyer des événements d’expérience pour les profils de test et valider que l’éligibilité, le classement et le capping de la fréquence renvoient les offres correctes.
doc-type: article
solution: Experience Platform
exl-id: 540e50c9-bf39-49a4-ae63-c1d7b94f6b8c
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '2147'
ht-degree: 0%

---


# Prise de décision et CBE en action

## Objectif

Maintenant que le Parcours est actif, vous pouvez commencer à envoyer des événements d’expérience et voir les offres renvoyées. Comme les identifiants d’année de naissance et de plan téléphonique des profils individuels affectent l’offre renvoyée, nous devons envoyer des événements d’expérience pour les profils préconfigurés avec des années de naissance et des identifiants de plan spécifiques.

## Configuration des profils et de Postman

Les trois profils que vous utiliserez se trouvent déjà dans votre sandbox et sont décrits dans ce tableau :

| Prénom | Nom | Année de naissance | ID de plan | customerID | ECID | E-mail |
| ---------- | ------------ | ---------- | ------- | ---------- | -------------------------------------- | --------------- |
| Bob | De base | 1974 | 1 | 287415903 | 34566216966446312560595171785271630085 | bob\@dep.com |
| Peter | Professionnel | 1981 | 2 | 105946728 | 22344522145769262754334953788432801285 | peter\@dep.com |
| Ursule | Ultimate | 2002 | 3 | 730682145 | 35615467908312308343036144243711275069 | ursula\@dep.com |

Localiser ces profils dans AEP

1. Si nécessaire, développez l’élément **Client** dans le rail de gauche, puis cliquez sur **Profils**
1. Cliquez sur l’onglet **Parcourir** et parmi tous les profils qui ont déjà été créés pour vous ou que vous avez créés dans le cadre d’ateliers précédents, vous voyez ces trois profils.

   Recherchez les événements d’expérience correspondants pour chaque profil dans la collection Postman

1. Si nécessaire, ouvrez Postman
1. Assurez-vous que les variables d’environnement **EDGE\_REGION** et **DATASTREAM\_CONFIG** sont toujours définies. S’ils doivent être définis à nouveau, consultez les étapes du Lab « Importer l’environnement et la collecte ».
1. Développez le dossier **Decisioning Lab**. Deux événements d’expérience s’affichent pour chaque profil :

![Dossier Postman Decisioning Lab présentant deux événements d’expérience par profil](assets/decisioning-and-cbes-in-action-postman-collection-folder.png)

## Envoi dans les événements d’expérience

>[!IMPORTANT]
>
>Ne passez pas à côté de l’explication du texte d’ouverture de cette section.

Avec un temps et des ressources illimités, nous vous demanderions de créer et de déployer une bibliothèque de balises avec AEP Web SDK sur un site web réel. Cela montre comment récupérer les offres et générer des rapports sur celles-ci. Cependant, compte tenu de l’ampleur et de la profondeur du contenu couvert dans ces ateliers, nous avons choisi de précréer les événements d’expérience nécessaires pour accéder au Parcours, récupérer les offres et créer des rapports sur ces offres dans une collection Postman, plutôt que d’avoir à baliser un site web. Lorsqu’elle est utilisée correctement, cette collection reproduit la manière dont un site correctement balisé (ou tout canal numérique) utiliserait le canal de diffusion CBE dans un Parcours.

L’approche recommandée pour les déploiements d’AEP Web SDK consiste à utiliser une approche deux appels par page. Dans ce modèle, le SDK Web envoie un appel de récupération en haut de la page à Edge, qui demande toutes les personnalisations nécessaires pour l’utilisateur. Ces personnalisations sont renvoyées par l’Edge, puis rendues par le SDK Web. Un deuxième appel au bas de la page, généralement appelé appel de collecte de données, est ensuite envoyé à Edge et rend compte de ce qui a été présenté à l’utilisateur final, avec d’autres données pour Analytics, CJA et d’autres solutions. Lorsqu’il s’agit de récupérer des propositions à partir d’Edge, souvenez-vous d’un simple mnémonique : FAR, qui signifie Fetch, Apply et Report. Toutes les propositions doivent être récupérées, appliquées ou rendues (présentées à l’utilisateur final), puis faire l’objet de rapports. Il est essentiel que ces offres soient signalées comme étant vues afin que les règles de limitation de la fréquence fonctionnent.

Les activités Adobe Target et le canal web AJO peuvent voir leurs réponses récupérées et appliquées automatiquement par AEP Web SDK. Leurs rapports peuvent également être envoyés avec l’appel de collecte de données au bas de la page. Cependant, les CBE sont différents. Le SDK Web d’AEP peut récupérer les propositions, mais il appartient au client ou à la cliente d’appliquer (rendre) tout ce qui est renvoyé, puis d’utiliser le SDK Web d’AEP pour créer un rapport sur ce qui a été affiché. Un CBE n’utilise généralement pas les appels de collecte de données pour générer des rapports sur ce qui a été affiché. Ils doivent donc être transmis manuellement.

Dans la collection Postman, vous verrez que chaque profil comporte deux appels d’événement d’expérience

Un Événement D’Expérience D’Extraction De Haut De Page

Événement D’Expérience De Collecte De Données Page Bottom (Bas De Page)

L’Événement d’expérience en haut de la page inclut le paramètre « jsonOfferContainer » dans la requête, à savoir l’« Emplacement sur la page » que vous avez configuré pour le CBE. En outre, cet appel utilise la fonctionnalité de script de Postman pour obtenir la réponse d’Edge, puis envoyer immédiatement un deuxième appel au reporting d’Edge pour signaler que l’offre a été présentée à l’utilisateur final. Il n’y a pas d’application ou de rendu réel de l’offre, car il n’y a pas de site web pour ce Lab. Mais du point de vue d’AJO, l’offre a été renvoyée, puis signalée comme vue.

L’appel de collecte de données de la page inférieure a pour seul but de générer une page vue pour la page Aperçu d’iPhone 17 . Rappelez-vous que le segment pour accéder au Parcours lui-même nécessite 3 vues de cette page. Une fois que cet événement d’expérience a été envoyé 3 fois, cet utilisateur entre dans le Parcours, puis seul l’événement d’expérience Récupération en haut de la page est nécessaire pour obtenir l’offre et signaler qu’elle a été vue.

Commencez par le profil de Bob.

1. Cliquez sur la requête **Bob - Collecte de données en bas de page**.
2. Cliquez sur l’onglet **Body** et notez les paramètres transmis, tels que l’espace de noms customerID dans IdentityMap, qui indique qu’il est authentifié, ainsi que le paramètre « web.webPageDetails.name » qui transmet dans le nom de page de « phones\:apple\:iphone 17\:overview ».

   ![Bob - Corps de requête de collecte de données du bas de la page dans Postman](assets/decisioning-and-cbes-in-action-bob-page-bottom-request.png)

3. Cliquez sur **Envoyer** dans le coin supérieur droit pour envoyer une page vue. Vous obtenez une réponse similaire à celle-ci

   ![Réponse reçue après l’envoi de l’événement de collecte de données Page Bottom de Bob](assets/decisioning-and-cbes-in-action-bob-data-collection-response.png)

4. Une fois que vous avez reçu une réponse appropriée, cliquez de nouveau sur **Envoyer** pour renvoyer le même événement Bas de page une deuxième fois. Patientez quelques secondes, puis envoyez un troisième appel de collecte de données pour le profil Bob. Vous avez envoyé un total de 3 appels de bas de page.

   À ce stade, le système traite ces accès et ajoute Bob au segment de diffusion en continu « dep : Intéressé par iPhone 17 ». Une fois que c&#39;est fait, Bob est mis dans le Parcours. Une fois dans le Parcours, il suffit de quelques minutes pour que l’entrée de Robert dans le Parcours et le segment soit projeté vers la boutique de profils Edge pour qu’il y figure.

5. Revenez à l’interface utilisateur d’AJO et cliquez sur **Profils** dans le rail de gauche, suivi de l’onglet **Parcourir**.
6. Recherchez le profil de Bob à l’aide de l’espace de noms **customerID** avec la valeur **287415903**.

   ![Recherche du profil de Bob à l’aide de l’espace de noms customerID](assets/decisioning-and-cbes-in-action-search-bob-profile.png)

7. Cliquez sur **Afficher** pour ouvrir le profil de Bob (la couleur du profil de Bob peut être différente de celle affichée dans la capture d’écran).

   ![Ouverture de la page de profil de Bob dans AJO](assets/decisioning-and-cbes-in-action-bob-profile-opened.png)

8. Une fois le profil de Bob ouvert, cliquez sur l’onglet **Appartenance à une audience** et vous constatez que Bob est désormais membre du segment « dep : Intéressé par iPhone 17 », au moins du point de vue d’AEP Hub.
9. Cliquez sur **Attributs** puis sélectionnez le bouton radio **Edge** pour passer à la vue Edge.

   ![Onglet Attributs avec le bouton radio Edge pour changer de vue de profil](assets/decisioning-and-cbes-in-action-edge-view-toggle.png)

   >[!WARNING]
   >
   >Il existe un bug malheureux de l’interface utilisateur qui nécessite que vous cliquiez sur l’onglet Attributs pour passer le bouton radio à Edge.



10. Cliquez à nouveau sur **Appartenance à une audience** et si vous avez suivi ces étapes assez rapidement, vous verrez que l’Edge est sélectionnée et que Bob n’est pas membre de l’audience

![Vue Edge du profil de Bob ne montrant aucune appartenance à l&#39;audience pour le moment](assets/decisioning-and-cbes-in-action-edge-audience-membership-empty.png)

11. Dans un nouvel onglet du navigateur, accédez au Parcours que vous avez créé et cliquez dessus. Vous constatez qu’un profil est entré dans le Parcours et se trouve désormais sur le nœud CBE.

![Zone de travail de Parcours affichant le profil de Bob saisi au niveau du nœud CBE](assets/decisioning-and-cbes-in-action-bob-enters-journey.png)

À ce stade, Bob est entré sur le Parcours et la projection Edge est en train d’assembler une projection qui met à jour le profil de Bob sur Edge.

12. Revenez à Postman et cliquez sur le second des appels d’événement d’expérience de Bob, **Bob - Page Top Fetch.**
13. Cliquez sur **Envoyer**. Que se passe-t-il ?
    - Si le profil Edge de Bob n’a pas encore été mis à jour, vous obtenez une réponse très similaire à celle de l’appel de collecte de données. Si c’est le cas, patientez encore une minute ou deux, puis essayez d’envoyer à nouveau l’appel de récupération du haut de la page de Bob.
    - Si le profil Edge de Bob a été mis à jour, vous obtenez une réponse avec le fichier JSON qui a été configuré précédemment, ainsi que des informations supplémentaires utilisées pour le compte rendu des performances. Mais avant de passer à autre chose, quelle offre iPhone 17 doit proposer à Robert ?

      Bob est né en 1974, c&#39;est-à-dire plus de 1966. Il se serait donc qualifié pour le critère de la formule de classement 2, et ses scores de priorité d&#39;offre Générique, Base et Pro auraient été multipliés par 100, donnant à ces scores d&#39;offre des scores de 100, 200 et 300, respectivement. Cependant, Bob Basic a un ID de plan 1, il n&#39;est donc pas éligible aux offres de niveau Ultra ou Pro grâce à la règle de décision. Par conséquent, l’offre de niveau de base, qui a un score de 200, s’affiche. Vous pouvez voir que dans la réponse (vous devrez probablement faire défiler l’écran vers le bas) :

![Réponse Postman affichant l’offre de niveau de base renvoyée pour Bob](assets/decisioning-and-cbes-in-action-bob-base-offer-response.png)

14. N’oubliez pas que cette requête Postman envoie automatiquement une notification d’affichage pour cette offre. AJO a donc déjà enregistré au moins une impression pour cette offre. Cliquez à nouveau sur **Envoyer** pour envoyer une deuxième impression. Vérifiez que l&#39;offre de base a été renvoyée.
15. Rappelez-vous qu&#39;une limitation de fréquence de 3 impressions s&#39;applique aux modèles de niveau Base, Pro et Ultra. Cliquez sur **Envoyer** une troisième fois pour obtenir une troisième réponse avec le niveau de base et pour enregistrer une autre impression.
16. Cliquez sur **Envoyer** une quatrième fois. Que se passe-t-il ? La limite de fréquence de l’offre de niveau de base est atteinte et vous recevez l’offre générique dans la réponse :

![Réponse Postman affichant l’offre générique renvoyée une fois la limitation de fréquence atteinte](assets/decisioning-and-cbes-in-action-bob-generic-offer-after-cap.png)

17. Cliquez de nouveau sur **Envoyer** pour afficher l’offre de niveau générique. Vous pouvez cliquer sur Envoyer 100 fois de plus et obtenir la même offre en retour jusqu’au lendemain, lorsque le capping de la fréquence est réinitialisé.

>[!WARNING]
>
>N’oubliez pas que dans AJO, la journée se réinitialise à minuit GMT. Si vous deviez envoyer un autre appel de récupération après minuit GMT, vous verriez l’offre de niveau de base renvoyer à la place.

18. Revenez à l’interface utilisateur de Journey Orchestration et cliquez sur le Parcours **Parcourir les abandons d’iPhone 17** que vous avez créé. Comme le Parcours est actif et publié, vous commencez à voir des statistiques. Vous voyez qu’1 profil est entré dans le Parcours et se trouve actuellement au nœud CBE.

![Rapports de Parcours affichant un profil actuellement sur le nœud CBE](assets/decisioning-and-cbes-in-action-bob-enters-journey.png)

>[!NOTE]
>
>À ce stade, vous vous demandez peut-être pourquoi le profil ne se trouve pas au nœud d’attente. Une fois qu’il a atteint le nœud CBE et projeté les mises à jour sur le profil Edge de Bob, doit-il se trouver au nœud d’attente ? La réponse courte est que ça pourrait l&#39;être, mais... on pourrait aussi faire valoir que puisque le CBE est activement retourné, c&#39;est là que Bob est sur ce Parcours. Mais au bout de 3 jours, le Parcours indique que le profil a terminé le Parcours sans jamais se trouver réellement dans le nœud d’attente.

## Envoi d’événements d’expérience pour d’autres profils

Maintenant que vous avez vu le Parcours fonctionner pour le profil de Bob, il y a deux autres profils à tester.

1. Revenez à Postman et recherchez les événements d’expérience pour Peter et Ursula.
2. Exécutez l’événement « Collecte de données en bas de page » 3 fois pour chaque profil, en n’oubliant pas de donner 1 à 3 secondes entre chaque demande d’envoi/de collecte de données.
3. Patientez quelques minutes pour que les trois profils soient qualifiés pour le segment de streaming, saisissez le Parcours, puis faites projeter le CBE sur leurs profils Edge.
4. Envoyez l’appel de récupération du haut de la page autant de fois que nécessaire pour vérifier que les règles de prise de décision et les formules de classement fonctionnent comme prévu.

   **Profils de prise de décision : comportement attendu**

   | Prénom | Nom | 1ère offre | 2e offre | 3ème offre | 4e offre |
   | ---------- | ------------ | --------- | --------- | --------- | --------- |
   | Bob | De base | Base | Générique | Générique | Générique |
   | Peter | Professionnel | Pro | Base | Générique | Générique |
   | Ursule | Ultimate | Ultra | Pro | Base | Générique |

5. Une fois que vous avez terminé, revenez au Parcours. Vous constatez que les 3 profils sont entrés dans le Parcours et se trouvent au niveau du nœud CBE.

>[!NOTE]
>
>Si vous deviez attendre 3 jours et envoyer à nouveau la récupération du haut de la page, vous constateriez qu’aucune offre n’a été renvoyée et que les trois profils ont terminé le Parcours

## Récapituler

Sur cette dernière page du Lab, vous êtes passé à la phase d’exécution, au cours de laquelle vous avez testé la configuration de votre décision à l’aide d’événements d’expérience et d’un canal d’expérience basée sur le code (CBE). Vous avez utilisé Postman pour envoyer des événements d’expérience simulés à Adobe Journey Optimizer afin que :

- Les profils ont rejoint le parcours que vous avez créé, car ils répondaient aux critères du segment de diffusion en continu.
- Le canal CBE a été appelé avec des événements de récupération pour obtenir des décisions d’offre basées sur les données de profil (année de naissance, forfait téléphonique, etc.).
- Les offres ont été renvoyées et comptabilisées par rapport aux limites de fréquence telles que configurées, ce qui montre comment différentes règles et logiques de classement ont affecté l’offre diffusée.
- Vous avez vérifié que le capping de la fréquence et l’éligibilité fonctionnaient comme prévu en envoyant à plusieurs reprises des appels de récupération des offres.

Vous avez exécuté de vrais appels de prise de décision et validé que vos règles d’éligibilité, votre formule de classement et votre configuration d’offre se comportent correctement lorsque les profils interagissent avec le moteur de prise de décision.
