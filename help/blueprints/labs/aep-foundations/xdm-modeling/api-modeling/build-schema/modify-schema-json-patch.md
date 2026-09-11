---
hold: true
title: Modifier le schéma - Correctif JSON
description: Utilisez un appel API JSON PATCH pour ajouter un nouveau champ à un groupe de champs client existant et voir la modification répercutée dans le schéma.
doc-type: article
solution: Experience Platform
exl-id: c0313594-d998-4525-a0a4-d9d844bed5ef
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---


# Modifier le schéma - Correctif JSON

## Présentation

Supposons un instant qu’après avoir créé le schéma, vous deviez revenir et ajouter un champ supplémentaire à l’objet `plan` appelé `planDescription`, car vous avez oublié de l’ajouter lors de la création ou il s’agissait d’une demande qui vous est parvenue des mois plus tard.  Pour effectuer cette tâche, vous pouvez simplement effectuer une opération `PATCH` qui met à jour le schéma avec le nouveau champ.

Vous pouvez en savoir plus sur JSON PATCH en cliquant sur les liens ci-dessous, mais pour les besoins de ce Lab, supposons que vous ayez un certain concept de son fonctionnement 😄

- [https://jsonpatch.com/](https://jsonpatch.com/)
- [Principes fondamentaux des API d’Experience League](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-fundamentals.html?lang=fr#json-patch)

![Diagramme d&#39;application d&#39;un correctif à un champ planDescription manquant dans un schéma existant](assets/modify-schema-json-patch-patching-missing-plan-description-field.png "Application d&#39;un correctif à une description de plan de champ manquante")

>[!NOTE]
>
>Gardez à l’esprit les points suivants :
>
>- Un schéma est composé d’une (1) classe et d’un (1) ou de plusieurs groupes de champs
>- Vous ne pouvez pas ajouter directement de nouveaux champs à un schéma sans d’abord les ajouter à un groupe de champs. Cela permet de garantir la réutilisation d’un champ dans tout schéma qui utilise ce groupe de champs.



Pour ajouter un nouveau champ à un schéma, vous devez effectuer les opérations suivantes dans l’ordre.  C’est ce que vous ferez dans les étapes de ce Lab.

- Identifiez le groupe de champs dans lequel vous souhaitez ajouter la nouvelle propriété
- Construire un appel PATCH JSON pour mettre à jour le groupe de champs
- Exécutez l’appel JSON PATCH pour mettre à jour le groupe de champs (dont le schéma héritera).



## Localiser et identifier le groupe de champs à mettre à jour

1. Sélectionnez l’appel API `Step 1 - Get Tenant Field groups` situé dans le dossier `XDM Schema Lab -> Customize Schema`
1. Exécutez la requête en cliquant sur le bouton `Send` .

![Étape 1 - Demande d’API Get Tenant Field Groups](assets/modify-schema-json-patch-step-1-get-tenant-field-groups.png "Étape 1 - Get Tenant Field Groups")

>[!NOTE]
>
>N’oubliez pas que vous avez créé l’objet `plan` dans un groupe de champs personnalisés. Les objets créés personnalisés dans le registre des schémas XDM sont appelés « client », d’où l’appel API utilisant le chemin d’accès `/schemaregistry/tenant/mixins/`.



1. Dans la réponse, recherchez l’ID de schéma pour le groupe de champs personnalisés que vous avez créé précédemment intitulé `Customer Account Details - Sandbox <your number here> `

1. Copiez le `$meta:altId` et enregistrez-le dans un endroit sûr, car vous en aurez besoin pour l’étape suivante

![Recherche du groupe de champs personnalisé Détails du compte client dans la réponse de l’API](assets/modify-schema-json-patch-search-field-group-response.jpeg "recherchez la réponse du groupe de champs Détails du compte client")

>[!CAUTION]
>
>Veillez à sélectionner le groupe de champs approprié à copier.  Il en existe un appelé de la même manière `dep: Customer Account Details` que vous ne devriez **pas** utiliser

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré le `$meta:altId `quelque part.  Cela sera nécessaire lors des prochaines étapes du laboratoire



## Recherche du groupe de champs par $meta\:altId

1. Sélectionnez l’appel API `Step 2 - Fetch path for the object to be modified` dans le dossier `XDM Schema Lab -> Customize Schema` .
1. Dans l’URL de la requête, remplacez la `<replace me>` par la `$meta:altId` que vous avez enregistrée à partir de l’étape de section précédente jusqu’à la fin de l’appel, comme illustré ci-dessous
1. Enregistrez les modifications apportées à la requête
1. Exécutez la requête en cliquant sur le bouton `Send` .

![Étape 2 - Chemin de récupération de l’appel API à modifier pour l’objet](assets/modify-schema-json-patch-step-2-fetch-object-path.jpeg "Étape 2 - Chemin de récupération des étapes de l’objet à modifier")



Passez en revue la réponse et notez que le chemin d’accès du pointeur JSON pour l’objet **plan** est construit à l’aide de chacune des propriétés mises en surbrillance ci-dessous.

![Propriétés mises en surbrillance composant le chemin du pointeur JSON vers l’objet de plan](assets/modify-schema-json-patch-customer-account-details-path-to-the-plan-object.png "Chemin d’accès des détails du compte client vers l’objet de plan")



Le chemin entièrement composé ressemble à ce que vous voyez ci-dessous.  Copiez ce chemin et enregistrez-le quelque part pour référence

```none
/definitions/customFields/properties/_devbc/properties/plan/properties
```

>[!NOTE]
>
>Pensez à mettre à jour le nom du client ci-dessus (\_devbc) avec le vôtre



## PATCH du groupe de champs

### Exemple de corps d’API JSON PATCH

```none
[
    {
        "op": "",
        "path": "",
        "value": {
            "title": "",
            "type": "",
            "description": ""
        }
    }
]
```

- **op (Opération)** -> fournit des instructions sur l’action que le PATCH doit effectuer
- **Chemin** -> il s’agit du chemin que vous souhaitez créer, mettre à jour ou supprimer (c’est-à-dire le pointeur JSON vers l’emplacement du nouveau champ)
- **Valeur** -> ce champ est facultatif et est utilisé uniquement lors de la création ou du remplacement d’un champ existant



### Exécution de la requête API

1. Cliquez sur l’appel API `Step 3 - Modify Tenant Field group` dans le dossier `XDM Schema Lab -> Customize Schema` .

![Étape 3 - Modifier l’appel API du groupe de champs du client](assets/modify-schema-json-patch-step-3-modify-tenant-field-group.png "Étape 3 - Modifier le groupe de champs du client")



&#x200B;2. Mettez à jour le corps de la requête avec les informations suivantes

- **op** ->` add`
- **path** -> `path from previous step +`&#x200B;` the new field name`
- **value** ->
  - **title** -> `Plan Description`
  - **type** -> `string`
  - **description** -> `High-level details about the plan`

Lorsque vous avez terminé, votre requête API doit ressembler à ceci

![Corps de requête JSON PATCH terminé ajoutant le champ planDescription](assets/modify-schema-json-patch-step-3-final-call-example.png "Étape 3 - Exemple d’appel final")

>[!WARNING]
>
>Veillez à inclure le nouveau nom du champ, **planDescription,** dans votre chemin d’accès



&#x200B;3. Si tout vous semble correct `Save` votre appel

&#x200B;4. `Execute` l’appel pour exécuter le PATCH

Vous devriez voir une `200 OK `réponse et devriez maintenant voir le champ `planDescription` dans votre groupe de champs comme suit :

Réponse ![200 OK après avoir corrigé le groupe de champs avec planDescription](assets/modify-schema-json-patch-step-3-200-ok-successful-patch.png "Étape 3 - 200 OK PATCH réussie")

>[!TIP]
>
>Félicitations ! Vous avez correctement mis à jour un groupe de champs/schéma à l’aide de JSON PATCH



## Afficher la modification dans l’interface utilisateur

Parcourez votre schéma à travers l’interface utilisateur et jetez un coup d’œil au champ que vous venez d’ajouter.  Plutôt cool, hein ?

![Champ Description du plan visible dans le schéma après le correctif JSON dans l’interface utilisateur d’Experience Platform](assets/modify-schema-json-patch-plan-description-added-to-field-group.png "Description du plan ajouté au groupe de champs Détails du compte client - Sandbox \&lt;votre numéro> . Modifier le schéma JSON ")
