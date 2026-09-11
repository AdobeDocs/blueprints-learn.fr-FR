---
hold: true
title: Réessayer un flux de données ayant échoué
description: Réessayez une exécution de flux de données ayant échoué afin que les données sources soient retraitées selon des règles de mappage mises à jour dans un nouveau flux de données.
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# Réessayer un flux de données ayant échoué

Pour réessayer un workflow, procédez comme suit :

1. Accédez à **Sources -> Flux de données -> \[Nom du flux de données] -> \[Échec de l’exécution]**
1. Mettez en surbrillance l’exécution du flux de données qui n’a pas réussi à afficher le rail de droite.
1. Cliquez sur **Réessayer**. La nouvelle tentative prend la copie des données associées à l’exécution ayant échoué et lui applique désormais les nouvelles règles de mappage

![Nouvelle tentative d’exécution d’un flux de données ayant échoué dans le rail de droite](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>Notez que lorsque vous réessayez un flux de données en échec, un nouveau flux de données est créé et exécuté. Il s’affiche en haut de la liste des flux de données
