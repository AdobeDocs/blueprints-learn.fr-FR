---
title: Créer une propriété
description: Créez une propriété Transfert d’événement avec un élément de données et une règle qui transfèrent les événements d’expérience entrants vers un point d’entrée webhook.
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# Créer une propriété

En règle générale, nous souhaitons transférer un événement d’expérience à un tiers (ce qui n’est pas obligatoire). Cette option est généralement utilisée lorsqu&#39;une copie d&#39;un événement est nécessaire en temps réel pour informer un tiers dans des circonstances spécifiques (par exemple, en informant Google, Meta ou TikTok d&#39;un achat).

>[!NOTE]
>
>Rappel : une propriété contient toutes les extensions, les éléments de données et les règles nécessaires pour décider quoi transférer et où

1. Dans le rail de gauche, cliquez sur Transfert d’événement .
2. Cliquez ensuite sur Nouvelle propriété

   ![Section Transfert d’événement avec le bouton Nouvelle propriété en surbrillance](assets/create-property-new-property-button.png "Créez une propriété de transfert d’événement")

3. Mettez à jour le nom de la propriété en utilisant la formule suivante : `Event Forward Property SB + [sandbox number]`. Votre nom final ressemblerait à ceci : **Event Forward Property SB01**

4. Cliquez sur **Enregistrer** lorsque vous avez terminé

![Champ Nom de la propriété de transfert d’événement renseigné avec le bouton Enregistrer en surbrillance](assets/create-property-name-property-form.png)

## Installer l’extension

1. Cliquez sur la propriété Transfert d’événement que vous venez de créer

   ![Liste des propriétés de transfert d’événement avec la propriété nouvellement créée mise en surbrillance](assets/create-property-open-new-property.png "Ouvrez votre propriété d’événement")



2. Vous devriez voir un écran comme ci-dessous.  Cliquez sur **Extensions**.

   ![Écran d’aperçu de la propriété Transfert d’événement avec l’onglet Extensions en surbrillance](assets/create-property-click-extensions-tab.png)



3. Installez l’extension Adobe Cloud Connector en procédant comme suit :

4. Cliquez sur **Catalogue** dans le volet de navigation supérieur
5. Cliquez sur la carte **Adobe Cloud Connector**
6. Dans le rail de droite, cliquez sur le bouton **Installer**

![Catalogue d’extensions avec la carte Adobe Cloud Connector et le bouton Installer en surbrillance](assets/create-property-install-cloud-connector-extension.png)



Après avoir cliqué sur installer , vous devriez voir l’affichage des extensions sous les extensions Installées pour votre propriété, comme illustré ci-dessous

![Liste des extensions installées montrant l’extension Adobe Cloud Connector installée avec succès](assets/create-property-extension-installed-confirmation.png "Extension entièrement installée")

## Créer un élément de données

>[!NOTE]
>
>Un élément de données référence l’événement entrant et peut l’analyser en plusieurs composants individuels si nécessaire

1. Dans le rail de gauche, cliquez sur **Éléments de données**



   ![Navigation dans le rail de gauche avec le lien Éléments de données en surbrillance](assets/create-property-navigate-to-data-elements.png "Accédez aux éléments de données")



2. Cliquez sur le bouton **Créer un élément de données**

   ![Page Éléments de données avec le bouton Créer un élément de données en surbrillance](assets/create-property-create-new-data-element-button.png "Créer un élément de données")



3. Configurez le nouvel élément de données avec les informations suivantes :

   | Type d’élément | Valeur à configurer |
   | ----------------- | ------------------ |
   | Nom | Objet de données |
   | Extension | Noyau |
   | Type d’élément de données | Code personnalisé |

   ![Configuration de l’élément de données avec les champs Nom, Extension et Type d’élément de données défini](assets/create-property-data-element-config-step-1.png "Étape 1 de la configuration de l’élément de données")



4. Cliquez sur le bouton **Ouvrir l’éditeur** pour ajouter le code personnalisé suivant :

   ![Paramètres des éléments de données avec le bouton Ouvrir l’éditeur en surbrillance pour le code personnalisé](assets/create-property-open-custom-code-editor.png "Ouvrez l’éditeur")



5. Ajoutez du code personnalisé à l’éditeur comme suit et enregistrez-le

   ```none
   var xdm = arc?.event || '';
   return xdm;
   ```

   ![Éditeur de code personnalisé affichant le script qui renvoie l’objet d’événement XDM entrant](assets/create-property-custom-code-added.png "Code personnalisé")

   >[!NOTE]
   >
   >Il s’agit de saisir l’objet xdm entier sans effectuer de traductions dans la payload.  Si nécessaire, nous pouvions analyser chaque élément individuel dans l’objet XDM (par exemple, le nom de page, le montant de l’achat), en un élément de données par champ.  La raison pour cela pourrait être s’il y a une transformation de la structure vers une autre structure





6. Cliquez sur le bouton **Enregistrer** pour enregistrer l’élément de données.

![Éditeur d’éléments de données avec le bouton Enregistrer en surbrillance](assets/create-property-save-data-element-button.png)



Lorsque vous avez terminé, l’écran suivant qui confirme que votre élément de données a été ajouté devrait s’afficher :

![Liste des éléments de données présentant l’élément de données nouvellement enregistré ajouté à la propriété](assets/create-property-data-element-saved-confirmation.png)


## Créer des règles

>[!NOTE]
>
>Une règle contient :
>
>1. Conditions sur ce qu’il faut transférer
>2. Actions pouvant transformer la payload et définir où l’envoyer



1. Dans le rail de gauche, cliquez sur **Règles**

   ![Navigation dans le rail de gauche avec le lien Règles mis en surbrillance](assets/create-property-navigate-to-rules.png)



2. Cliquez ensuite sur **Créer une règle**

   ![Page Règles avec le bouton Créer une règle en surbrillance](assets/create-property-new-rule-button.png)



3. Mettez à jour le nom de la règle en utilisant la formule suivante : `"EF Rule SB" + [your sandbox number]` (c.-à-d. la règle SB01 de l&#39;EF). Vous trouverez votre numéro de sandbox en haut à droite de la fenêtre de votre navigateur, comme illustré ci-dessous\...

   ![Coin supérieur droit de la fenêtre du navigateur indiquant le numéro du sandbox utilisé dans le nom de la règle](assets/create-property-sandbox-number-location.png)

4. Cliquez sur **Enregistrer** lorsque vous avez terminé

   >[!NOTE]
   >
   >Assurez-vous que le nom de la règle suit le modèle de formule de `"EF Rule SB" + [sandbox number]`

   ![Champ de nom de règle renseigné avec le modèle de dénomination du sandbox des règles EF](assets/create-property-add-rule-name.png "Ajoutez un nom à la règle")



5. Ajoutez une action à votre règle en cliquant sur le signe (+) pour ajouter une nouvelle action

![Éditeur de règles avec l’icône plus mise en surbrillance pour ajouter une nouvelle action](assets/create-property-add-action-button.png "Ajoutez une action")

## Obtenir l’URL du webhook (à utiliser en action)

>[!NOTE]
>
>Cet atelier utilise un webhook ici afin que vous puissiez voir si les données sont arrivées à la destination à laquelle vous les envoyez. Dans un scénario réel, vous vous connecteriez à cette destination et utiliseriez ses outils pour voir ce qui est arrivé.



1. Ouvrez le lien suivant dans un nouvel onglet de votre navigateur -> [](https://webhook.site/)
2. Copiez l’URL unique qui s’affiche et enregistrez-la en lieu sûr.

   ![Page Webhook.site avec l’URL unique mise en surbrillance pour la copie](assets/create-property-webhooksite-copy-url.png)



3. Configurez votre action avec les informations suivantes :

| Paramètre | Valeur |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extension | Adobe Cloud Connector |
| Type d’action | Effectuer l’appel de récupération |
| Méthode | Message |
| URL | Utilisez la même URL de webhook que celle utilisée lors de la configuration de la destination de diffusion en streaming. Pour le trouver, ouvrez un nouvel onglet dans le navigateur et accédez à Destinations -> Parcourir . |
| Corps | Raw |
| Données du corps | \{ « data »: \{ « event »: « \{\{Data Object\}\} » } |

>[!NOTE]
>
>L’élément \{\{Data Object\}\} référencé ici est l’élément de données que vous avez créé précédemment. Ici, le système en aval avait besoin d’encapsuler l’événement dans un objet de données avec un objet d’événement. Vous pouvez mettre n&#39;importe quelle mise en forme ici.
>
>Si nous avions divisé \{\{Objet de données\}\} en plusieurs champs (par exemple, nom de page, achat, etc.), nous pourrions transformer la structure JSON en plaçant chaque champ à l’emplacement souhaité, ce qui nous permettrait de mieux contrôler la correspondance avec la destination.





Lorsque vous avez terminé, vérifiez que votre écran ressemble à ce qui suit, puis cliquez sur **Conserver les modifications**

![Action de règle configurée avec les paramètres d’appel d’extraction Adobe Cloud Connector et l’URL webhook](assets/create-property-configure-action-settings.png "Configurez l’action")



4. Une fois cette opération terminée, l’action doit être ajoutée à la règle. Cliquez sur **Enregistrer** pour continuer.

![Éditeur de règles affichant l’action configurée avec le bouton Enregistrer mis en surbrillance](assets/create-property-save-rule-button.png "Enregistrez votre règle")

>[!WARNING]
>
>Lorsque vous envoyez un événement d’expérience, vous envoyez l’événement, et non le profil, ni aucun de ses attributs, y compris les qualifications d’audience (même s’il s’agit d’une audience Edge).
>
>Cela se produit à des fins de rapidité.



## Publier les modifications

1. Dans le rail de gauche, cliquez sur **Flux de publication**

   ![Navigation dans le rail de gauche avec le lien Flux de publication en surbrillance](assets/create-property-navigate-to-publishing-flow.png "Accédez au flux de publication")



2. Cliquez sur le bouton **Ajouter une bibliothèque**

   ![Publication de la page Flux avec le bouton Ajouter une bibliothèque en surbrillance](assets/create-property-add-library-button.png "Ajouter une bibliothèque")



3. Configurez la bibliothèque avec les informations suivantes :

   - Nom -> **Bibliothèque EF**
   - Environnement -> **Développement**
   - Cliquez sur **Ajouter toutes les ressources modifiées**


   Lorsque vous avez terminé, votre écran doit ressembler à la capture d’écran ci-dessous.  Si tout semble correct, cliquez sur le bouton **Enregistrer et créer dans le développement**

   ![Configuration de la bibliothèque avec le nom, l’environnement de développement et le bouton Enregistrer et créer dans le développement](assets/create-property-configure-library-save-and-build.png)



4. Vous devriez alors voir la version de développement passer au vert indiquant qu’elle est prête à être utilisée

![Flux de publication affichant le statut de version de développement passé au vert et prêt à l’emploi](assets/create-property-development-build-ready.png)
