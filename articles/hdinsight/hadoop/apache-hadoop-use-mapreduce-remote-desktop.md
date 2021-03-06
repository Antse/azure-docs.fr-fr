---
title: MapReduce et le Bureau à distance avec Apache Hadoop dans HDInsight - Azure
description: Apprenez à utiliser le Bureau à distance pour vous connecter à Apache Hadoop sur HDInsight et exécuter des tâches MapReduce.
services: hdinsight
author: hrasheed-msft
ms.reviewer: jasonh
ms.service: hdinsight
ms.topic: conceptual
ms.date: 01/12/2017
ms.author: hrasheed
ROBOTS: NOINDEX
ms.openlocfilehash: c0040958cbf748d3eafb3ee60806b064e4e0b1ba
ms.sourcegitcommit: c2e61b62f218830dd9076d9abc1bbcb42180b3a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53435784"
---
# <a name="use-mapreduce-in-apache-hadoop-on-hdinsight-with-remote-desktop"></a>Utilisation de MapReduce dans Apache Hadoop sur HDInsight avec le Bureau à distance
[!INCLUDE [mapreduce-selector](../../../includes/hdinsight-selector-use-mapreduce.md)]

Dans cet article, vous allez apprendre à vous connecter à un Apache Hadoop sur le cluster HDInsight en utilisant le Bureau à distance et exécuter les tâches MapReduce à l’aide de la commande Hadoop.

> [!IMPORTANT]  
> Le Bureau à distance n’est disponible que sur les clusters HDInsight Windows. Linux est le seul système d’exploitation utilisé sur HDInsight version 3.4 ou supérieure. Pour plus d’informations, consultez [Suppression de HDInsight sous Windows](../hdinsight-component-versioning.md#hdinsight-windows-retirement).
>
> Pour HDInsight 3.4 ou versions ultérieures, consultez [Utiliser MapReduce avec SSH](apache-hadoop-use-mapreduce-ssh.md) pour plus d’informations sur la connexion au cluster HDInsight et l’exécution des travaux MapReduce.

## <a id="prereq"></a>Configuration requise
Pour effectuer les étapes présentées dans cet article, vous avez besoin des éléments suivants :

* un cluster HDInsight basé sur Windows (Hadoop sur HDInsight)
* Un ordinateur client avec Windows 10, Windows 8 ou Windows 7

## <a id="connect"></a>Connexion avec le Bureau à distance
Activez le Bureau à distance pour le cluster HDInsight, puis connectez-vous à lui en suivant les instructions fournies dans [Se connecter à des clusters HDInsight avec RDP](../hdinsight-administer-use-management-portal.md#connect-to-clusters-using-rdp).

## <a id="hadoop"></a>Utilisation de la commande Hadoop
Une fois connecté au bureau pour le cluster HDInsight, procédez comme suit pour exécuter une tâche MapReduce à l’aide de la commande Hadoop :

1. À partir du bureau HDInsight, démarrez la **ligne de commande Hadoop**. Cela ouvre une nouvelle invite de commandes dans le répertoire **c:\apps\dist\hadoop-&lt;numéro de version>**.

   > [!NOTE]  
   > Le numéro de version change à mesure que Hadoop est mis à jour. La variable d’environnement **HADOOP_HOME** peut être utilisée pour rechercher le chemin d’accès. Par exemple, `cd %HADOOP_HOME%` permet de basculer vers le répertoire Hadoop sans qu'il soit nécessaire de connaître le numéro de version.
   >
   >
2. Pour utiliser la commande **Hadoop** pour exécuter une tâche MapReduce d’exemple, utilisez la commande suivante :

        hadoop jar hadoop-mapreduce-examples.jar wordcount wasb:///example/data/gutenberg/davinci.txt wasb:///example/data/WordCountOutput

    Cela lance la classe **wordcount**, contenue dans le fichier **hadoop-mapreduce-examples.jar** du répertoire actif. En tant qu’entrée, elle utilise le document **wasb://example/data/gutenberg/davinci.txt** et la sortie est stockée dans **wasb:///example/data/WordCountOutput**.

   > [!NOTE]
   > Pour plus d'informations sur cette tâche MapReduce et sur les exemples de données, consultez <a href="hdinsight-use-mapreduce.md">Utilisation de MapReduce dans HDInsight Hadoop</a>.
   >
   >
3. La tâche émet des informations lors de son traitement, avant de renvoyer des informations semblables aux suivantes lorsqu’elle est terminée.

        File Input Format Counters
        Bytes Read=1395666
        File Output Format Counters
        Bytes Written=337623
4. Une fois la tâche terminée, utilisez la commande suivante pour répertorier les fichiers de sortie stockés sur **wasb://example/data/WordCountOutput** :

        hadoop fs -ls wasb:///example/data/WordCountOutput

    Cela devrait afficher deux fichiers, **_SUCCESS** et **part-r-00000**. Le fichier **part-r-00000** contient la sortie de cette tâche.

   > [!NOTE]
   > Certaines tâches MapReduce peuvent fractionner les résultats sur plusieurs fichiers **part-r-#####** . Dans ce cas, utilisez le suffixe ##### pour indiquer l’ordre des fichiers.
   >
   >
5. Pour afficher la sortie, utilisez la commande suivante :

        hadoop fs -cat wasb:///example/data/WordCountOutput/part-r-00000

    Cela affiche une liste de mots contenus dans le fichier **wasb://example/data/gutenberg/davinci.txt**, ainsi que le nombre d’occurrences de chaque mot. Voici un exemple des données contenues dans le fichier :

        wreathed        3
        wreathing       1
        wreaths         1
        wrecked         3
        wrenching       1
        wretched        6
        wriggling       1

## <a id="summary"></a>Résumé
Comme vous pouvez le voir, la commande Hadoop fournit un moyen facile pour exécuter des tâches MapReduce sur un cluster HDInsight avant d’afficher le résultat de la tâche.

## <a id="nextsteps"></a>Étapes suivantes
Pour obtenir des informations générales sur les tâches MapReduce dans HDInsight :

* [Utilisation de MapReduce dans Hadoop HDInsight](hdinsight-use-mapreduce.md)

Pour plus d’informations sur d’autres méthodes de travail avec Hadoop sur HDInsight :

* [Utiliser Apache Hive avec Apache Hadoop sur HDInsight](hdinsight-use-hive.md)
* [Utiliser Apache Pig avec Apache Hadoop sur HDInsight](hdinsight-use-pig.md)
