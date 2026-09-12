---
title: Vérifier le jeu de mappages final
description: Comparez vos mappages de champs simples et calculés pour le schéma Compte client au jeu de mappages final attendu.
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Vérifier le jeu de mappages final

>[!NOTE]
>
>Si vous venez du laboratoire d’ingestion en flux continu, cliquez sur le lien ci-dessous pour passer à l’étape suivante de cet atelier :
>
>[Atelier D’Ingestion En Flux Continu - Vérification Du Jeu De Mappages Final](../../stream-ingestion/check-final-mapping-set.md)



## Mappages simples

>[!NOTE]
>
>Remplacez \&lt;nom-client> par la valeur de votre sandbox

| Champ Source | Champ cible |
| ------------------------- | --------------------------------- |
| account\_create\_date | \&lt;nom-client>.account.createDate |
| account\_end\_date | \&lt;nom-client>.account.endDate |
| customer\_id | \&lt;nom-client>.customerID |
| plan\_name | \&lt;nom-client>.plan.name |
| plan\_id | \&lt;nom-client>.plan.planID |
| billing\_city | billingAddress.city |
| billing\_zip\_code | billingAddress.postalCode |
| billing\_state | billingAddress.state |
| billing\_street\_address | billingAddress.street1 |
| email\_optIn | consentements.marketing.email.val |
| mobile\_phone | mobilePhone.number |
| firstName | person.name.firstName |
| lastName | person.name.lastName |
| adresse électronique | personalEmail.address |
| createDate | repo.createDate |
| modifyDate | repo.modifyDate |
| shipping\_city | shippingAddress.city |
| shipping\_zip\_code | shippingAddress.postalCode |
| shipping\_state | shippingAddress.state |
| shipping\_street\_address | shippingAddress.street1 |

>[!NOTE]
>
>Assurez-vous que votre mappage final correspond à ce qui est indiqué ci-dessous avant de continuer.



## Mappages calculés

| Champs calculés | Champ XDM |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null ou sms\_optIn == «  », &#39;n&#39;, sms\_optIn) | consentements.marketing.sms.val |
| concat(date\_part(« month », date(born\_Date,« M/d/yyyy »)).toString(), « - », date\_part(« day », date(born\_Date,« M/d/yyyy »)).toString()) | person.bornDayAndMonth |
| date\_part(« aaaa »,date(naissance\_Date,« M/j/aaaa »)) | person.bornYear |

>[!NOTE]
>
>Assurez-vous que votre mappage final correspond à ce qui est indiqué ci-dessous avant de continuer
