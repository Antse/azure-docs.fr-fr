---
title: Créer un réseau virtuel - Démarrage rapide - Azure CLI | Microsoft Docs
description: Dans ce démarrage rapide, vous découvrez comment créer un réseau virtuel à l’aide d'Azure CLI. Un réseau virtuel permet à des ressources Azure, comme des machines virtuelles, de communiquer en privé entre elles et avec Internet.
services: virtual-network
documentationcenter: virtual-network
author: jimdial
manager: jeconnoc
editor: ''
tags: azure-resource-manager
Customer intent: I want to create a virtual network so that virtual machines can communicate with privately with each other and with the internet.
ms.assetid: ''
ms.service: virtual-network
ms.devlang: azurecli
ms.topic: quickstart
ms.tgt_pltfrm: virtual-network
ms.workload: infrastructure
ms.date: 12/12/2018
ms.author: jdial
ms.custom: mvc
ms.openlocfilehash: 5219ba0885c15d68bd17f07fb8f1f41e856dad0c
ms.sourcegitcommit: e37fa6e4eb6dbf8d60178c877d135a63ac449076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53321356"
---
# <a name="quickstart-create-a-virtual-network-using-the-azure-cli"></a>Démarrage rapide : Créer un réseau virtuel à l’aide d’Azure CLI

Un réseau virtuel permet à des ressources Azure, comme des machines virtuelles, de communiquer en privé entre elles et avec Internet. Dans ce guide de démarrage rapide, vous allez apprendre à créer un réseau virtuel. Après avoir créé un réseau virtuel, déployez deux machines virtuelles dans le réseau virtuel. Vous vous connectez alors aux machines virtuelles depuis Internet et vous communiquez en privé sur le nouveau réseau virtuel.

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) maintenant.

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

Si vous décidez d’installer et d’utiliser Azure CLI en local, ce guide de démarrage rapide nécessite que vous utilisiez Azure CLI version 2.0.28 ou ultérieure. Exécutez `az --version` pour rechercher la version installée. Pour des informations d'installation ou de mise à niveau, consultez [Installer Azure CLI](/cli/azure/install-azure-cli).

## <a name="create-a-resource-group-and-a-virtual-network"></a>Créer un groupe de ressources et un réseau virtuel

Avant de pouvoir créer un réseau virtuel, vous devez créer un groupe de ressources qui hébergera le réseau virtuel. Créez un groupe de ressources avec la commande [az group create](/cli/azure/group#az_group_create). Cet exemple crée un groupe de ressources nommé *myResourceGroup* dans la région *eastus* :

```azurecli-interactive
az group create --name myResourceGroup --location eastus
```

Créez un réseau virtuel avec la commande [az network vnet create](/cli/azure/network/vnet#az_network_vnet_create). Cet exemple crée un réseau virtuel par défaut nommé *myVirtualNetwork* avec un sous-réseau nommé *default* :

```azurecli-interactive
az network vnet create \
  --name myVirtualNetwork \
  --resource-group myResourceGroup \
  --subnet-name default
```

## <a name="create-virtual-machines"></a>Créer des machines virtuelles

Créez deux machines virtuelles dans le réseau virtuel.

### <a name="create-the-first-vm"></a>Créer la première machine virtuelle

Créez une machine virtuelle avec la commande [az vm create](/cli/azure/vm#az_vm_create). Si des clés SSH n’existent pas déjà dans un emplacement de clé par défaut, la commande les crée. Pour utiliser un ensemble spécifique de clés, utilisez l’option `--ssh-key-value`. L’option `--no-wait` crée la machine virtuelle en arrière-plan. Vous pouvez donc passer à l’étape suivante. Cet exemple crée une machine virtuelle nommée *myVm1* :

```azurecli-interactive
az vm create \
  --resource-group myResourceGroup \
  --name myVm1 \
  --image UbuntuLTS \
  --generate-ssh-keys \
  --no-wait
```

### <a name="create-the-second-vm"></a>Créer la seconde machine virtuelle

Puisque vous avez utilisé l'option `--no-wait` à l’étape précédente, vous pouvez poursuivre et créer la deuxième machine virtuelle nommée *myVm2*.

```azurecli-interactive
az vm create \
  --resource-group myResourceGroup \
  --name myVm2 \
  --image UbuntuLTS \
  --generate-ssh-keys
```

### <a name="azure-cli-output-message"></a>Message de sortie Azure CLI

La création des machines virtuelles peut prendre plusieurs minutes. Une fois les machines virtuelles créées, Azure CLI renvoie une sortie comme la suivante :

```azurecli
{
  "fqdns": "",
  "id": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVm2",
  "location": "eastus",
  "macAddress": "00-0D-3A-23-9A-49",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.5",
  "publicIpAddress": "40.68.254.142",
  "resourceGroup": "myResourceGroup"
}
```

Veuillez noter **publicIpAddress**. Vous utiliserez cette adresse pour vous connecter à la machine virtuelle à partir d’Internet à l’étape suivante.

## <a name="connect-to-a-vm-from-the-internet"></a>Se connecter à une machine virtuelle à partir d’Internet

Dans cette commande, remplacez `<publicIpAddress>` par l’adresse IP publique de votre machine virtuelle *myVm2* :

```bash
ssh <publicIpAddress>
```

## <a name="communicate-between-vms"></a>Établir une communication entre les machines virtuelles

Pour vérifier la communication privée entre les machines virtuelles *myVm2* et *myVm1*, entrez cette commande :

```bash
ping myVm1 -c 4
```

Vous recevrez quatre réponses de *10.0.0.4*.

Fermez la session SSH avec la machine virtuelle *myVm2*.

## <a name="clean-up-resources"></a>Supprimer des ressources

Lorsque vous n'en avez plus besoin, vous pouvez utiliser [az group delete](/cli/azure/group#az_group_delete) pour supprimer le groupe de ressources, ainsi que toutes les ressources qu’il contient :

```azurecli-interactive
az group delete --name myResourceGroup --yes
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez créé un réseau virtuel par défaut et deux machines virtuelles. Vous vous êtes connecté à une machine virtuelle à partir d’Internet et avez établi une communication privée entre les deux machines virtuelles. Pour plus d’informations sur les paramètres des réseaux virtuels, consultez [Gérer un réseau virtuel](manage-virtual-network.md).

Azure autorise une communication privée illimitée entre des machines virtuelles. Par défaut, Azure permet uniquement les connexions Bureau à distance entrantes pour les machines virtuelles Windows depuis Internet. Pour en savoir plus sur la configuration des différents types de communications de réseau de machine virtuelle, accédez au tutoriel [Filtrer le trafic réseau](tutorial-filter-network-traffic.md).