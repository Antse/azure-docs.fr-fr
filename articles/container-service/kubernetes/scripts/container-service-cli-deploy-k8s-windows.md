---
title: Exemple de script Azure CLI - Créer un cluster ACS Windows Kubernetes | Microsoft Docs
description: Exemple de script Azure CLI - Créer un cluster ACS Windows Kubernetes
services: container-service
documentationcenter: ''
author: iainfoulds
manager: jeconnoc
editor: ''
tags: acs, azure-container-service
keywords: Docker, conteneurs, microservices, Kubernetes, DC/OS, Azure
ms.assetid: ''
ms.service: container-service
ms.devlang: azurecli
ms.topic: sample
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/30/2017
ms.author: iainfou
ms.openlocfilehash: 1f24f036858f9c77ed6b07af27617d3e3706bba2
ms.sourcegitcommit: 2469b30e00cbb25efd98e696b7dbf51253767a05
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "53001571"
---
# <a name="deprecated-create-an-azure-container-service-kubernetes-windows-cluster"></a>(DÉPRÉCIÉ) Créer un cluster Windows Kubernetes Azure Container Service

[!INCLUDE [ACS deprecation](../../../../includes/container-service-kubernetes-deprecation.md)]

Cet exemple crée un cluster Azure Container Service exécutant Kubernetes pour des conteneurs basés sur Windows.

[!INCLUDE [sample-cli-install](../../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>Exemple de script

```azurecli
az group create --name myResourceGroup --location eastus

az acs create \
  --orchestrator-type kubernetes \
  --resource-group myResourceGroup \
  --name myK8SCluster \
  --generate-ssh-keys \
  --admin-username azureuser \
  --admin-password Password12 \
  --windows
```

## <a name="clean-up-deployment"></a>Nettoyer le déploiement 

Exécutez la commande suivante pour supprimer le groupe de ressources, la machine virtuelle et toutes les ressources associées.

```azurecli
az group delete --name myResourceGroup
```

## <a name="script-explanation"></a>Explication du script

Ce script a recours aux commandes suivantes pour créer le déploiement. Chaque élément du tableau renvoie à une documentation spécifique.

| Commande | Notes |
|---|---|
| [az group create](https://docs.microsoft.com/cli/azure/group#az-group-create) | Crée un groupe de ressources dans lequel toutes les ressources sont stockées. |
| [az acs create](https://docs.microsoft.com/cli/azure/acs#az-acs-create) | Crée un cluster ACS. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’interface Azure CLI, consultez la [documentation relative à l’interface Azure CLI](https://docs.microsoft.com/cli/azure).

Vous trouverez des exemples supplémentaires de scripts CLI Azure Container Service dans la [documentation sur Azure Container Service](../cli-samples.md).
