---
title: Extension CLI Machine Learning
titleSuffix: Azure Machine Learning service
description: Découvrez l’extension CLI Azure Machine Learning pour l'interface de ligne de commande Azure. L’interface de ligne de commande Azure est un utilitaire de ligne de commande multiplateforme qui vous permet d'utiliser des ressources du cloud Azure. Grâce à l'extension de Machine Learning, vous pouvez utiliser le service Azure Machine Learning.
services: machine-learning
ms.service: machine-learning
ms.component: core
ms.topic: conceptual
ms.reviewer: jmartens
ms.author: jordane
author: jpe316
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: e16506773e38f1732a55161cdd58ffb7523602d4
ms.sourcegitcommit: 7fd404885ecab8ed0c942d81cb889f69ed69a146
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53277282"
---
# <a name="use-the-cli-extension-for-azure-machine-learning-service"></a>Utiliser l’extension CLI pour le service Azure Machine Learning

L'interface CLI Azure Machine Learning est une extension pour l'[interface Azure](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest), une interface de ligne de commande multiplateforme pour la plateforme Azure. Cette extension fournit les commandes à utiliser avec le service Azure Machine Learning à partir de la ligne de commande. Elle vous permet de créer des scripts capables d'automatiser votre flux de travail Machine Learning. Par exemple, vous pouvez créer des scripts pour ce qui suit :

+ Exécuter des expérimentations pour créer des modèles Machine Learning

+ Inscrire des modèles Machine Learning pour l’usage des clients

+ Empaqueter, déployer et suivre le cycle de vie de vos modèles Machine Learning

L’interface CLI ne remplace en rien le kit de développement logiciel (SDK) Azure. Il s'agit d'un outil complémentaire optimisé pour gérer les tâches hautement paramétrables, notamment :

* Création de ressources de calcul

* Soumission d’expérimentations paramétrables

* Inscription de modèles

* Création d'images

* Déploiement de services

## <a name="prerequisites"></a>Prérequis


* Pour utiliser l'interface de ligne de commande, vous devez disposer d'un abonnement Azure. Si vous n’avez pas d’abonnement Azure, créez un compte gratuit avant de commencer. Essayez la [version gratuite ou payante de Azure Machine Learning service](http://aka.ms/AMLFree) dès aujourd’hui.

* [Interface de ligne de commande Azure](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest).

## <a name="install-the-extension"></a>Installer l’extension

Pour installer l'extension d'interface de ligne de commande Machine Learning, utilisez la commande suivante :

```azurecli-interactive
az extension add -s https://azuremlsdktestpypi.blob.core.windows.net/wheels/sdk-release/Preview/E7501C02541B433786111FE8E140CAA1/azure_cli_ml-1.0.2-py2.py3-none-any.whl --pip-extra-index-urls  https://azuremlsdktestpypi.azureedge.net/sdk-release/Preview/E7501C02541B433786111FE8E140CAA1
```

Lorsque vous y êtes invité, sélectionnez `y` pour installer l’extension.

Pour vérifier que l’extension a été installée, utilisez la commande suivante afin d'afficher la liste des sous-commandes spécifiques à ML :

```azurecli-interactive
az ml -h
```

> [!TIP]
> Pour mettre à jour l’extension, vous devez la __supprimer__, puis l'__installer__. Cela installe la dernière version.

## <a name="remove-the-extension"></a>Supprimer l’extension

Pour supprimer l'extension CLI, utilisez la commande suivante :

```azurecli-interactive
az extension remove -n azure-cli-ml
```

## <a name="resource-management"></a>Gestion des ressources

Les commandes suivantes montrent comment utiliser l'interface de ligne de commande pour gérer les ressources utilisées par Azure Machine Learning.


+ Créer un espace de travail pour le service Azure Machine Learning :

    ```azurecli-interactive
    az ml workspace create -n myworkspace -g myresourcegroup
    ```

+ Définir un espace de travail par défaut :

    ```azurecli-interactive
    az configure --defaults aml_workspace=myworkspace group=myresourcegroup
    ```

+ Créer une cible de calcul managée pour la formation distribuée :

    ```azurecli-interactive
    az ml computetarget create amlcompute -n mycompute --max_nodes 4 --size Standard_NC6
    ```

* Mettre à jour une cible de calcul managée :

    ```azurecli-interactive
    az ml computetarget update --name mycompute --workspace –-group --max_nodes 4 --min_nodes 2 --idle_time 300
    ```

* Joindre une cible de calcul non managée pour l’apprentissage ou le déploiement :

    ```azurecli-interactive
    az ml computetarget attach aks -n myaks -i myaksresourceid -g myrg -w myworkspace
    ```

## <a name="experiments"></a>Expériences

Les commandes suivantes montrent comment utiliser l’interface de ligne de commande à des fins d'expérimentation :

* Rattachez-vous à un projet (configuration d’exécution) avant de soumettre une expérimentation :

    ```azurecli-interactive
    az ml project attach --experiment-name myhistory
    ```

* Exécutez votre expérimentation. Lorsque vous utilisez cette commande, spécifiez une cible de calcul. Dans cet exemple, `local` utilise l’ordinateur local pour permettre au modèle d'utiliser le script `train.py` :

    ```azurecli-interactive
    az ml run submit -c local train.py
    ```

* Affichez la liste des expérimentations soumises :

    ```azurecli-interactive
    az ml history list
    ```

## <a name="model-registration-image-creation--deployment"></a>Inscription de modèles, création d’images et déploiement

Les commandes suivantes montrent comment inscrire un modèle entraîné, puis le déployer en tant que service de production :

+ Inscrivez un modèle dans Azure Machine Learning :

  ```azurecli-interactive
  az ml model register -n mymodel -m sklearn_regression_model.pkl
  ```

+ Créez une image contenant votre modèle Machine Learning et vos dépendances : 

  ```azurecli-interactive
  az ml image create container -n myimage -r python -m mymodel:1 -f score.py -c myenv.yml
  ```

+ Déployer une image sur une cible de calcul :

  ```azurecli-interactive
  az ml service create aci -n myaciservice --image-id myimage:1
  ```
