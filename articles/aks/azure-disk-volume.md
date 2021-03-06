---
title: Créer un volume statique pour des pods sur Azure Kubernetes Service (AKS)
description: Découvrez comment créer manuellement un volume avec des disques Azure pour une utilisation avec un pod sur Azure Kubernetes Service (AKS)
services: container-service
author: iainfoulds
ms.service: container-service
ms.topic: article
ms.date: 10/08/2018
ms.author: iainfou
ms.openlocfilehash: 9c5879474568885d9a705e7bfd16e2a4e2304b96
ms.sourcegitcommit: 7b0778a1488e8fd70ee57e55bde783a69521c912
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49068178"
---
# <a name="manually-create-and-use-a-volume-with-azure-disks-in-azure-kubernetes-service-aks"></a>Créer manuellement et utiliser un volume avec des disques Azure sur Azure Kubernetes Service (AKS)

Les applications basées sur des conteneurs doivent souvent consulter et conserver des données dans un volume de données externe. Si un pod unique a besoin d’accéder au stockage, vous pouvez utiliser des disques Azure pour présenter un volume natif pour une utilisation de l’application. Cet article vous montre comment créer manuellement un disque Azure et comment l’attacher à un pod sur AKS.

> [!NOTE]
> Un disque Azure ne peut être monté que sur un pod unique à la fois. Si vous avez besoin de partager un volume persistant entre plusieurs pods, utilisez [Azure Files][azure-files-volume].

Pour plus d’informations sur les volumes Kubernetes, consultez [Volumes Kubernetes][kubernetes-volumes].

## <a name="before-you-begin"></a>Avant de commencer

Cet article suppose que vous avez un cluster AKS existant. Si vous avez besoin d’un cluster AKS, consultez le guide de démarrage rapide d’AKS [avec Azure CLI][aks-quickstart-cli] ou [avec le portail Azure][aks-quickstart-portal].

Vous devez également avoir installé et configuré Azure CLI version 2.0.46 ou ultérieure. Exécutez `az --version` pour trouver la version. Si vous devez installer ou mettre à niveau, consultez [Installer Azure CLI 2.0][install-azure-cli].

## <a name="create-an-azure-disk"></a>Créer un disque Azure

Lorsque vous créez un disque Azure pour une utilisation avec AKS, vous pouvez créer la ressource de disque sur le groupe de ressources de **nœuds**. Cette approche permet au cluster AKS d’accéder et de gérer la ressource de disque. Si, à la place, vous créez le disque dans un groupe de ressources distinct, vous devez donner au service principal Azure Kubernetes Service (AKS) pour votre cluster le rôle `Contributor` dans le groupe de ressource du disque.

Pour cet article, créez le disque dans le groupe de ressources de nœuds. Tout d’abord, obtenez le nom du groupe de ressources avec la commande [az aks show][az-aks-show] et ajoutez le paramètre de requête `--query nodeResourceGroup`. L’exemple suivant obtient les le groupe de ressources du nœud pour le cluster AKS nommé *myAKSCluster* dans le groupe de ressources nommé *myResourceGroup* :

```azurecli
$ az aks show --resource-group myResourceGroup --name myAKSCluster --query nodeResourceGroup -o tsv

MC_myResourceGroup_myAKSCluster_eastus
```

À présent, créez un disque à l’aide de la commande [az disk create][az-disk-create]. Spécifiez en premier le nom de groupe de ressources de nœuds obtenu dans la commande précédente, puis celui pour la ressource de disque, par exemple *myAKSDisk*. L’exemple suivant crée un disque de *20* Gio et génère l’ID du disque après sa création :

```azurecli-interactive
az disk create \
  --resource-group MC_myResourceGroup_myAKSCluster_eastus \
  --name myAKSDisk  \
  --size-gb 20 \
  --query id --output tsv
```

> [!NOTE]
> Les disques Azure sont facturés par référence (SKU) pour une taille donnée. Ces références SKU vont de 32 Gio pour les disques S4 ou P4 à 8 Tio pour les disques S60 ou P60. Le débit et les performances d’E/S d’un disque managé Premium dépendent à la fois de la référence SKU et de la taille d’instance des nœuds dans le cluster AKS. Consultez [Tarification et performances des disques managés][managed-disk-pricing-performance].

L’ID de ressource de disque s’affiche une fois la commande complétée avec succès, comme illustré dans l’exemple de sortie suivant. Cet ID de disque est utilisé pour monter le disque à l’étape suivante.

```console
/subscriptions/<subscriptionID>/resourceGroups/MC_myAKSCluster_myAKSCluster_eastus/providers/Microsoft.Compute/disks/myAKSDisk
```

## <a name="mount-disk-as-volume"></a>Monter le disque en tant que volume

Pour monter le disque Azure dans votre pod, configurez le volume dans les spécifications du conteneur. Créez un fichier nommé `azure-disk-pod.yaml` avec le contenu suivant. Mettez à jour `diskName` avec le nom du disque créé à l’étape précédente, et `diskURI` avec l’ID du disque indiqué en sortie de la commande de création de disque. Si vous le souhaitez, mettez à jour `mountPath`. Il s’agit du chemin du disque Azure qui a été monté dans le pod.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - image: nginx:1.15.5
    name: mypod
    resources:
      requests:
        cpu: 100m
        memory: 128Mi
      limits:
        cpu: 250m
        memory: 256Mi
    volumeMounts:
      - name: azure
        mountPath: /mnt/azure
  volumes:
      - name: azure
        azureDisk:
          kind: Managed
          diskName: myAKSDisk
          diskURI: /subscriptions/<subscriptionID>/resourceGroups/MC_myAKSCluster_myAKSCluster_eastus/providers/Microsoft.Compute/disks/myAKSDisk
```

Utilisez la commande `kubectl` pour créer le pod.

```console
kubectl apply -f azure-disk-pod.yaml
```

Vous disposez maintenant d’un pod en cours d’exécution sur lequel est monté un disque Azure à l’emplacement suivant : `/mnt/azure`. Vous pouvez utiliser `kubectl describe pod mypod` pour vérifier que le disque est monté correctement. La sortie de l’exemple condensé suivant montre le volume monté dans le conteneur :

```
[...]
Volumes:
  azure:
    Type:         AzureDisk (an Azure Data Disk mount on the host and bind mount to the pod)
    DiskName:     myAKSDisk
    DiskURI:      /subscriptions/<subscriptionID/resourceGroups/MC_myResourceGroupAKS_myAKSCluster_eastus/providers/Microsoft.Compute/disks/myAKSDisk
    Kind:         Managed
    FSType:       ext4
    CachingMode:  ReadWrite
    ReadOnly:     false
  default-token-z5sd7:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-z5sd7
    Optional:    false
[...]
Events:
  Type    Reason                 Age   From                               Message
  ----    ------                 ----  ----                               -------
  Normal  Scheduled              1m    default-scheduler                  Successfully assigned mypod to aks-nodepool1-79590246-0
  Normal  SuccessfulMountVolume  1m    kubelet, aks-nodepool1-79590246-0  MountVolume.SetUp succeeded for volume "default-token-z5sd7"
  Normal  SuccessfulMountVolume  41s   kubelet, aks-nodepool1-79590246-0  MountVolume.SetUp succeeded for volume "azure"
[...]
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations à propos de l’interaction entre les clusters AKS et les disques Azure, consultez le [Plug-in Kubernetes pour les disques Azure][kubernetes-disks].

<!-- LINKS - external -->
[kubernetes-disks]: https://github.com/kubernetes/examples/blob/master/staging/volumes/azure_disk/README.md
[kubernetes-volumes]: https://kubernetes.io/docs/concepts/storage/volumes/
[managed-disk-pricing-performance]: https://azure.microsoft.com/pricing/details/managed-disks/

<!-- LINKS - internal -->
[az-disk-list]: /cli/azure/disk#az-disk-list
[az-disk-create]: /cli/azure/disk#az-disk-create
[az-group-list]: /cli/azure/group#az-group-list
[az-resource-show]: /cli/azure/resource#az-resource-show
[aks-quickstart-cli]: kubernetes-walkthrough.md
[aks-quickstart-portal]: kubernetes-walkthrough-portal.md
[az-aks-show]: /cli/azure/aks#az-aks-show
[install-azure-cli]: /cli/azure/install-azure-cli
[azure-files-volume]: azure-files-volume.md