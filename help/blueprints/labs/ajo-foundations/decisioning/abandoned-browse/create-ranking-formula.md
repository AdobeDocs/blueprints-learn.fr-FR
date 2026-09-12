---
title: Créer une formule de classement
description: Créez une formule de classement qui booste de manière dynamique les scores de priorité des offres en fonction des attributs de profil tels que l’âge.
doc-type: article
solution: Experience Platform
exl-id: 67aaca7f-366c-4db4-a5d5-017f52fbd15b
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 0%

---


# Créer une formule de classement

## Objectif

Maintenant que tous les éléments d’offre ont été créés, hiérarchisés, que l’éligibilité a été appliquée et organisés en une collection, nous pouvons nous concentrer sur la détermination de leur classement pour un profil donné. Pour ce faire, créez une formule de classement.

Une formule de classement renforce de manière dynamique les priorités d’offre spécifiques afin qu’elles « atteignent le sommet », en fonction des critères du profil interagissant avec la propriété Web/Mobile ou l’événement d’expérience lui-même.

Dans ce scénario de laboratoire, nous allons prétendre que l&#39;équipe marketing de recherche pour Connection 5G a montré que les moins de 39 ans seraient attirés vers les niveaux Ultra ou Pro et que ceux 40-59 seraient attirés vers les niveaux Base et Pro. Et puisque Connection 5G préférerait vendre des téléphones de niveau supérieur, toutes choses égales par ailleurs, le modèle ultra serait présenté en premier pour les moins de 39 ans, le modèle pro étant présenté en premier pour les 40-59 ans. Cette section vous explique comment créer une formule de classement pour répondre à ces besoins professionnels.

## Créer une formule de classement et une expression par défaut

1. Si nécessaire, développez **Prise de décision** dans le rail de gauche, puis cliquez sur **Configuration de la stratégie**. Vous accédez à la page « Règles de prise de décision » et voyez la règle de décision « Plans de niveau supérieur » que vous avez précédemment créée et utilisée comme conditions d’éligibilité pour les articles d’offre téléphonique de niveau supérieur.
2. Cliquez sur **Formules de classement** dans le menu &#39;Méthodes de classement&#39;. Cette action ouvre une page vide, car vous ne disposez pas encore de formule de classement.

   ![Page Formules de classement vide avant de créer une formule](assets/create-ranking-formula-empty-ranking-formulas-page.png)

3. Cliquez sur le bouton bleu **Créer une formule** pour commencer à créer une formule de classement
4. Nommez la formule de classement **Formule de classement iPhone 17**

   >[!NOTE]
   >
   >Lorsqu’un événement d’expérience est envoyé à la collecte de données Edge avec les paramètres requis pour demander une offre à partir d’un package Decisioning actif, toutes les offres de ce package sont évaluées à l’aide de la formule de classement. Chaque offre conserve sa priorité d’origine ou sa priorité est ajustée dynamiquement en fonction du profil qui a déclenché l’événement d’expérience.

5. Faites défiler la page jusqu’au bas de la section « Critères », cliquez sur l’icône **\&lt;/>** de la zone de texte située le plus bas, puis sélectionnez la variable **Score de priorité de l’offre**.

![Variable de score de priorité des offres sélectionnée dans les critères de la formule de classement](assets/create-ranking-formula-select-offer-priority-score.png)

L’expression par défaut est maintenant définie comme suit :

![Expression par défaut définie sur la variable de score de priorité des offres](assets/create-ranking-formula-default-expression-set.png)

>[!NOTE]
>
>Cette zone de texte inférieure est l&#39;expression par défaut appliquée à tout élément d&#39;offre qui ne répond à aucun critère d&#39;ajustement de priorité. Dans ce cas, il s’agit simplement de la priorité affectée à l’offre lors de sa création. Si aucun score de priorité par défaut n’est attribué à la collection sur laquelle cette formule de classement s’exécutera, vous souhaiterez attribuer un score par défaut

## Créer des règles d’ajustement de priorité

Maintenant qu’il existe une expression par défaut, vous pouvez commencer à ajouter des règles qui ajustent dynamiquement la priorité en fonction de l’âge de l’utilisateur.

Une façon d’envisager les règles d’ajustement de priorité est de les traiter comme des instructions if/then standard qui s’appliquent uniquement à certaines offres. Si le test s’avère vrai, ajustez la priorité des offres qui répondent à un critère donné. L’interface utilisateur organise ces éléments dans un ordre légèrement différent, comme indiqué dans cette capture d’écran.

![Ordre des sections UI de if, then et where dans une règle d’ajustement de priorité](assets/create-ranking-formula-if-then-where-rule-order.png "Ordre des sections UI de if, then et where dans une règle d’ajustement de priorité")

>[!NOTE]
>
>Le « si » est facultatif, car il est possible d’appliquer une règle d’ajustement de priorité lorsqu’une offre répond à un critère spécifique sans instruction conditionnelle au préalable. Pour poursuivre notre exemple dans ce guide, imaginons que nous disposions de plusieurs offres avec un attribut de système d’exploitation de téléphone (Android par rapport à iOS). Il est possible d’augmenter la priorité de toutes les offres iPhone pour lesquelles le système d’exploitation préféré du profil est iOS. Il n’y a pas de « si ». Juste « ajuster le score où attribut d’offre = attribut de profil ». Vous trouverez ci-dessous une image similaire à celle ci-dessus qui illustre cette idée sans instruction conditionnelle.
>
>![Règle d&#39;ajustement de priorité appliquée sans instruction Si conditionnelle](assets/create-ranking-formula-rule-without-conditional.png "Règle d&#39;ajustement de priorité appliquée sans instruction Si conditionnelle")

## Créer le critère 1 : règle d’ajustement pour les personnes de moins de 39 ans

1. Commencez par créer la règle de classement pour l&#39;élément d&#39;offre de niveau Ultra. Cliquez dans la première zone de texte de la section **Critère 1**, puis cliquez sur le bouton **Sélectionner un attribut** lorsqu’il apparaît.

   ![Sélectionner l’option d’attribut affichée pour le critère 1](assets/create-ranking-formula-criterion-one-select-attribute.png)

2. Lorsque la boîte de dialogue &#39;Sélectionner un attribut&#39; s&#39;ouvre, cliquez sur **Nom de l&#39;offre**. Une fois sélectionné, cliquez sur **Enregistrer.**

   >[!NOTE]
   >
   >L’« attribut de décision » fait référence aux éléments de l’élément d’offre. Puisque c’est là que vous indiquez les éléments d’offre auxquels les critères s’appliqueront, les seules options disponibles sont les attributs de l’élément d’offre.
   >

3. Laissez l’opérateur défini sur « Est égal à » et, dans la zone de texte restante, saisissez le nom de l’élément d’offre de niveau supérieur **iphone:17\:ultra**. Après avoir saisi le texte, l’interface utilisateur se met à jour et indique que la condition correspondante a été acceptée.
4. Cliquez sur **+Ajouter une condition** puis cliquez dans la zone de texte **nouveau qui apparaît** (elle contient le texte « *Cliquez pour créer un élément de décision...* »)
5. Cliquez sur l’option désormais disponible **Sélectionner un attribut**&#x200B;**.**
6. Lorsque la boîte de dialogue « Sélectionner un attribut » s’ouvre, cliquez sur **Attributs de profil > Personne** (vous devrez probablement faire défiler la page vers le bas) **> Année de naissance**. Une fois sélectionné, cliquez sur **Enregistrer.**

   >[!NOTE]
   >
   > « Attributs de profil » fait référence à l’utilisateur ou au profil qui a envoyé l’événement d’expérience, tandis que « Données contextuelles » fait référence aux éléments de l’événement d’expérience lui-même, tels que l’URL, le nom de page ou d’autres attributs de la payload de l’événement d’expérience.

7. Remplacez l’opérateur par **Supérieur à** et saisissez l’année de naissance **1986** (l’interface utilisateur place une virgule dans l’année, ce qui est attendu). Après la saisie, l’interface utilisateur se met à jour pour refléter le fait que la condition a été acceptée. Comme le cas d’utilisation commerciale est d’offrir le niveau Ultra à toute personne de moins de 40 ans, la priorité est ajustée pour toute personne née après 1986.

   >[!NOTE]
   >
   >Comme mentionné précédemment, l’interface utilisateur indique que ces conditions supplémentaires sont « facultatives ». Cela est vrai, car il est possible d’ajuster dynamiquement la priorité d’un ensemble d’éléments d’offre sans aucun critère supplémentaire. Il se peut que les mêmes éléments d’offre puissent être utilisés dans une collection différente et classés avec un ensemble différent de règles de classement. Comme cet atelier n’utilise qu’un seul ensemble d’éléments d’offre, des conditions supplémentaires sont utilisées pour ajuster la priorité.

8. La priorité d&#39;origine pour l&#39;élément d&#39;offre de niveau Ultra est 4. Pour augmenter la priorité, multipliez ce chiffre par 100. Pour ce faire, cliquez sur l’icône **\&lt;/>** en regard de la dernière zone de texte et sélectionnez la variable **Score de priorité des offres**. Ajoutez un **\*100** après le texte automatiquement saisi. Cette expression multiplie la priorité d’origine (4) par 100 et lui donne une nouvelle priorité de 400.

   Votre règle doit maintenant ressembler à ceci :

![Règle du critère 1 augmentant de 100 le score de priorité des offres de niveau Ultra](assets/create-ranking-formula-criterion-one-ultra-boost.png)

>[!NOTE]
>
>Pourquoi multiplier par 100 ? L&#39;idée est que si vous voulez vous assurer que vos priorités sont ajustées bien au-dessus des autres priorités, et 100 n&#39;est qu&#39;une façon simple de faire des calculs pour que cela se produise. Les formules de classement peuvent être complexes, comme vous le verrez dans la section suivante. Il est donc utile de garder les mathématiques simples.
>
>De plus, alors que nous avons utilisé la multiplication pour augmenter la note de priorité, d’autres expressions mathématiques auraient pu être utilisées pour diminuer la note de priorité. Cependant, en règle générale, il est plus facile de faire en sorte que les offres recherchées « flottent vers le haut » que d&#39;en faire des offres dont vous ne voulez pas « descendent vers le bas ».



## Créer le critère 2 : règle d’ajustement pour les 40-59 ans

1. Juste en dessous de la règle d’ajustement que vous venez de créer, cliquez sur le bouton **+ Ajouter un critère**.
2. Créez une condition correspondante pour laquelle le **Nom de l’offre** n’est PAS égal à **iphone:17\:ultra**.

   >[!WARNING]
   >
   >Cette règle est destinée à s&#39;appliquer à tous les autres éléments d&#39;offre. Vous trouverez plus de détails sur les raisons de ce choix sur cette page, mais faites très attention à utiliser ce type de logique en pratique, car il s’appliquerait à chaque offre de la collection qui n’a pas cette valeur. Dans notre cas, c&#39;est très bien, mais ce n&#39;est peut-être pas le cas dans d&#39;autres cas d&#39;utilisation.

3. Ajoutez la condition selon laquelle cette règle doit s&#39;appliquer à toute personne dont l&#39;année de naissance est supérieure à **1966** (toute personne de moins de 60 ans).
4. Comme pour la règle précédente, multipliez par 100 le score de priorité par défaut de l’élément de l’offre. Lorsque vous avez terminé, votre règle « Critère 2 » ressemble à ceci :

![Critère 2 : ajustement de la priorité pour les profils nés après 1966](assets/create-ranking-formula-criterion-two-rule.png)

>[!NOTE]
>
>L’utilisation conjointe de formules de classement et de règles d’éligibilité peut sembler complexe, mais voici l’idée de base :
>
>- **Les formules de classement** ajustent dynamiquement les scores de priorité et, par conséquent, l’ordre des offres.
>- **Les règles d’éligibilité** (telles que les règles de décision et les limites de fréquence) suppriment les offres de la liste triée si l’utilisateur n’est pas autorisé à les voir.
>
>Voici comment les offres seraient classées compte tenu de ces exemples et de la formule de classement que vous venez de créer :
>
>**Année de naissance = 1990**
>
>- Ultra Priority devient **400**
>- Pro = **3**, Base = **2**, Générique = **1**
>  Résultat : Ultra affiche d&#39;abord (jusqu&#39;à 3 fois), puis Pro, Base et enfin Generic.
>
>**Année de naissance = 1970**
>
>- La priorité Ultra reste à **4**
>- Pro devient **300**, Base = **200** et Générique = **100**
>  Résultat : Pro s&#39;affiche en premier (3 fois), puis Base, puis Generic. Ultra est classé en dernier car sa priorité (4) est inférieure à Generic (100).
>
>Lorsque l’éligibilité est appliquée via les règles de décision et le capping de la fréquence, alors
>
>- Les utilisateurs nés en 1990 avec un **ID de plan = 1** verront leurs offres Ultra et Pro supprimées, même s&#39;ils occupent la première place. L&#39;utilisateur ne voit que les offres de base et génériques car les niveaux Ultra et Pro sont assortis d&#39;une condition supplémentaire : seuls les utilisateurs possédant les **ID de plan 2 ou 3** peuvent les voir.
>- Comme l&#39;offre générique ne comporte aucune règle de limitation de la fréquence, l&#39;utilisateur de l&#39;année de naissance **1970** ne verra jamais l&#39;offre Ultra, car son score de priorité est inférieur au score boosté de l&#39;offre générique.

&#x200B;5. Une fois toutes les règles et le score de priorité par défaut en place, faites défiler l’écran vers le haut et cliquez sur le bouton bleu **Créer** dans le coin supérieur droit.

>[!TIP]
>
>Vous revenez maintenant à la page « Configuration de la stratégie », et la formule de classement unique que vous venez de créer s’affiche.

>[!NOTE]
>
>Que se passe-t-il si deux offres génèrent la même priorité ? Les offres ayant le même score de priorité sont choisies au hasard pour être renvoyées au système demandeur.

## Récapituler

Sur cette page, vous avez créé une formule de classement qui détermine comment les éléments d’offre sont triés dynamiquement pour chaque profil. Vous avez également défini une expression par défaut (score de priorité d’origine), puis ajouté des règles d’ajustement de priorité qui optimisent les priorités d’offre en fonction de critères de profil (tels que l’âge). Cette logique de classement garantit que les offres pertinentes (comme les niveaux Ultra ou Pro pour des tranches d’âge spécifiques) atteignent le sommet lorsqu’elles sont évaluées.
