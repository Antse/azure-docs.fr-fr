---
title: Déployer des ressources avec Azure CLI et un modèle | Microsoft Docs
description: Utilisez Azure Resource Manager et Azure CLI pour déployer des ressources sur Azure. Les ressources sont définies dans un modèle Resource Manager.
services: azure-resource-manager
documentationcenter: na
author: tfitzmac
ms.assetid: 493b7932-8d1e-4499-912c-26098282ec95
ms.service: azure-resource-manager
ms.devlang: azurecli
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/14/2018
ms.author: tomfitz
ms.openlocfilehash: 5f27b34bda930d020461bd5f4f7986091ffd5549
ms.sourcegitcommit: b254db346732b64678419db428fd9eb200f3c3c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53413657"
---
# <a name="deploy-resources-with-resource-manager-templates-and-azure-cli"></a>Déployer des ressources à l’aide de modèles Resource Manager et dAzure CLI

Cet article explique comment utiliser Azure CLI avec les modèles Resource Manager pour déployer vos ressources dans Azure. Si vous n’avez pas une bonne connaissance des concepts de déploiement et de gestion des solutions Azure, consultez [Vue d’ensemble d’Azure Resource Manager](resource-group-overview.md).  

Le modèle Resource Manager que vous déployez peut être un fichier local sur votre ordinateur ou un fichier externe qui se trouve dans un dépôt comme GitHub. Le modèle que vous déployez dans le cadre de cet article est disponible en tant que [modèle de compte de stockage dans GitHub](https://github.com/Azure/azure-quickstart-templates/blob/master/101-storage-account-create/azuredeploy.json).

[!INCLUDE [sample-cli-install](../../includes/sample-cli-install.md)]

Si Azure CLI n’est pas installé, vous pouvez utiliser le [Cloud Shell](#deploy-template-from-cloud-shell).

## <a name="deploy-local-template"></a>Déployer un modèle local

Au moment de déployer des ressources dans Azure, vous effectuez les opérations suivantes :

1. Connexion à votre compte Azure
2. Créez un groupe de ressources qui sert de conteneur pour les ressources déployées. Le nom du groupe de ressources ne peut contenir que des caractères alphanumériques, des points, des traits de soulignement, des traits d'union et des parenthèses. Il peut comprendre jusqu’à 90 caractères. Il ne peut pas se terminer par un point.
3. Déploiement dans le groupe de ressources du modèle qui définit les ressources à créer

Un modèle peut inclure des paramètres qui permettent de personnaliser le déploiement. Par exemple, vous pouvez indiquer des valeurs qui sont adaptées à un environnement particulier (par exemple, de développement, de test ou de production). L’exemple de modèle définit un paramètre pour la référence (SKU) de compte de stockage. 

L’exemple suivant crée un groupe de ressources et déploie un modèle à partir de votre ordinateur local :

```azurecli-interactive
az group create --name ExampleGroup --location "Central US"
az group deployment create \
  --name ExampleDeployment \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters storageAccountType=Standard_GRS
```

Le déploiement peut prendre plusieurs minutes. Au terme, vous voyez un message qui inclut le résultat :

```azurecli
"provisioningState": "Succeeded",
```

## <a name="deploy-external-template"></a>Déployer un modèle externe

Au lieu de stocker les modèles Resource Manager sur votre ordinateur local, vous pouvez les stocker dans un emplacement externe. Vous pouvez stocker des modèles dans un dépôt de contrôle de code source (par exemple, GitHub). Vous pouvez aussi les stocker dans un compte de stockage Azure pour mettre en place un accès partagé dans votre organisation.

Pour déployer un modèle externe, utilisez le paramètre **template-uri**. Pour déployer l’exemple de modèle à partir de GitHub, utilisez l’URI figurant dans l’exemple.
   
```azurecli-interactive
az group create --name ExampleGroup --location "Central US"
az group deployment create \
  --name ExampleDeployment \
  --resource-group ExampleGroup \
  --template-uri "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-storage-account-create/azuredeploy.json" \
  --parameters storageAccountType=Standard_GRS
```

L’exemple précédent nécessite un URI accessible publiquement pour le modèle, ce qui convient pour la plupart des scénarios, sachant que votre modèle ne doit pas inclure de données sensibles. Si vous avez besoin de spécifier des données sensibles (par exemple, un mot de passe d’administrateur), passez cette valeur en tant que paramètre sécurisé. Toutefois, si vous ne souhaitez pas que votre modèle soit accessible au public, vous pouvez le protéger en le stockant dans un conteneur de stockage privé. Pour plus d’informations sur le déploiement d’un modèle qui nécessite un jeton de signature d’accès partagé (SAS), consultez [Déployer un modèle privé avec un jeton SAS](resource-manager-cli-sas-token.md).

[!INCLUDE [resource-manager-cloud-shell-deploy.md](../../includes/resource-manager-cloud-shell-deploy.md)]

Dans Azure Cloud Shell, utilisez les commandes suivantes :

```azurecli-interactive
az group create --name examplegroup --location "South Central US"
az group deployment create --resource-group examplegroup \
  --template-uri <copied URL> \
  --parameters storageAccountType=Standard_GRS
```

## <a name="deploy-to-more-than-one-resource-group-or-subscription"></a>Déployer sur plus d’un groupe de ressources ou abonnement

En général, vous déployez toutes les ressources dans votre modèle sur un seul groupe de ressources. Toutefois, il existe des scénarios dans lesquels vous pouvez souhaitez déployer un ensemble de ressources, tout en les plaçant dans différents groupes de ressources ou abonnements. Vous ne pouvez pas déployer sur plus de cinq groupes de ressources dans un déploiement. Pour plus d’informations, voir [Déployer des ressources Azure sur plusieurs groupes de ressources et des abonnements](resource-manager-cross-resource-group-deployment.md).

## <a name="redeploy-when-deployment-fails"></a>Redéploiement en cas d’échec du déploiement

Pour les déploiements qui échouent, vous pouvez spécifier le redéploiement automatique d’un déploiement précédent dans votre historique de déploiement. Pour utiliser cette option, vos déploiements doivent avoir des noms uniques afin de pouvoir être identifiés dans l’historique. Si les noms ne sont pas uniques, le déploiement actuellement en échec peut remplacer le déploiement réussi précédemment dans l’historique. Vous pouvez uniquement utiliser cette option avec les déploiements de niveau racine. Les déploiements à partir d’un modèle imbriqué ne sont pas disponibles pour le redéploiement.

Pour redéployer le dernier déploiement réussi, ajoutez le paramètre `--rollback-on-error` comme indicateur.

```azurecli-interactive
az group deployment create \
  --name ExampleDeployment \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters storageAccountType=Standard_GRS \
  --rollback-on-error
```

Pour redéployer un déploiement spécifique, utilisez le paramètre `--rollback-on-error` et indiquez le nom du déploiement.

```azurecli-interactive
az group deployment create \
  --name ExampleDeployment02 \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters storageAccountType=Standard_GRS \
  --rollback-on-error ExampleDeployment01
```

Le déploiement spécifié doit avoir réussi.

## <a name="parameters"></a>parameters

Pour passer les valeurs de paramètre, vous pouvez utiliser des paramètres inline ou un fichier de paramètres. Les exemples précédents dans cet article décrivent des paramètres inline.

### <a name="inline-parameters"></a>Paramètres inline

Pour passer des paramètres inline, indiquez les valeurs dans `parameters`. Par exemple, pour passer une chaîne et un tableau à un modèle dans un interpréteur de commandes Bash, utilisez :

```azurecli
az group deployment create \
  --resource-group testgroup \
  --template-file demotemplate.json \
  --parameters exampleString='inline string' exampleArray='("value1", "value2")'
```

Vous pouvez également récupérer le contenu d’un fichier et fournir ce contenu en tant que paramètre inline.

```azurecli
az group deployment create \
  --resource-group testgroup \
  --template-file demotemplate.json \
  --parameters exampleString=@stringContent.txt exampleArray=@arrayContent.json
```

Obtenir une valeur de paramètre à partir d’un fichier est utile lorsque vous devez fournir des valeurs de configuration. Par exemple, vous pouvez fournir des [valeurs cloud-init pour une machine virtuelle Linux](../virtual-machines/linux/using-cloud-init.md).

Le format arrayContent.json est :

```json
[
    "value1",
    "value2"
]
```

### <a name="parameter-files"></a>Fichiers de paramètres

Au lieu de passer des paramètres en tant que valeurs inline dans votre script, il peut s’avérer plus facile d’utiliser un fichier JSON qui contient les valeurs des paramètres. Le fichier de paramètres doit être un fichier local. Les fichiers de paramètres externes ne sont pas pris en charge avec Azure CLI.

Le fichier de paramètres doit être au format suivant :

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
     "storageAccountType": {
         "value": "Standard_GRS"
     }
  }
}
```

Notez que la section des paramètres comprend un nom de paramètre qui correspond au paramètre défini dans votre modèle (storageAccountType). Le fichier de paramètres contient une valeur pour le paramètre. Cette valeur est transmise automatiquement au modèle pendant le déploiement. Vous pouvez créer plusieurs fichiers de paramètres, puis transmettre le fichier de paramètres approprié pour le scénario. 

Copiez l’exemple précédent et enregistrez-le dans un fichier nommé `storage.parameters.json`.

Pour transmettre un fichier de paramètres local, utilisez `@` pour spécifier un fichier local nommé storage.parameters.json.

```azurecli-interactive
az group deployment create \
  --name ExampleDeployment \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters @storage.parameters.json
```

### <a name="parameter-precedence"></a>Priorité des paramètres

Vous pouvez utiliser des paramètres inline et un fichier de paramètres local pendant la même opération de déploiement. Par exemple, vous pouvez spécifier certaines valeurs dans le fichier de paramètres local et ajouter d’autres valeurs inline pendant le déploiement. Si vous fournissez des valeurs pour un paramètre à la fois dans le fichier de paramètres local et inline, la valeur inline est prioritaire.

```azurecli
az group deployment create \
  --resource-group testgroup \
  --template-file demotemplate.json \
  --parameters @demotemplate.parameters.json \
  --parameters exampleArray=@arrtest.json
```


## <a name="test-a-template-deployment"></a>Tester le déploiement d’un modèle

Pour tester votre modèle et vos valeurs de paramètres sans réellement déployer toutes les ressources, utilisez [az group deployment validate](/cli/azure/group/deployment#az-group-deployment-validate). 

```azurecli-interactive
az group deployment validate \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters @storage.parameters.json
```

Si aucune erreur n’est détectée, la commande retourne des informations sur le déploiement de test. En particulier, notez que **error** a la valeur Null.

```azurecli
{
  "error": null,
  "properties": {
      ...
```

Si une erreur est détectée, la commande retourne un message d’erreur. Par exemple, la transmission d’une valeur incorrecte pour la référence (SKU) du compte de stockage retourne l’erreur suivante :

```azurecli
{
  "error": {
    "code": "InvalidTemplate",
    "details": null,
    "message": "Deployment template validation failed: 'The provided value 'badSKU' for the template parameter 
      'storageAccountType' at line '13' and column '20' is not valid. The parameter value is not part of the allowed 
      value(s): 'Standard_LRS,Standard_ZRS,Standard_GRS,Standard_RAGRS,Premium_LRS'.'.",
    "target": null
  },
  "properties": null
}
```

Si votre modèle comporte une erreur de syntaxe, la commande retourne une erreur indiquant que le modèle n’a pas pu être analysé. Le message indique le numéro de ligne et la position de l’erreur d’analyse.

```azurecli
{
  "error": {
    "code": "InvalidTemplate",
    "details": null,
    "message": "Deployment template parse failed: 'After parsing a value an unexpected character was encountered:
      \". Path 'variables', line 31, position 3.'.",
    "target": null
  },
  "properties": null
}
```

## <a name="next-steps"></a>Étapes suivantes
* Les exemples de cet article permettent de déployer des ressources dans un groupe de ressources pour votre abonnement par défaut. Pour utiliser un autre abonnement, consultez [Gérer plusieurs abonnements Azure](/cli/azure/manage-azure-subscriptions-azure-cli).
* Pour spécifier comment gérer les ressources présentes dans le groupe de ressources, mais non définies dans le modèle, consultez [Modes de déploiement Azure Resource Manager](deployment-modes.md).
* Pour comprendre comment définir des paramètres dans votre modèle, consultez [Comprendre la structure et la syntaxe des modèles Azure Resource Manager](resource-group-authoring-templates.md).
* Pour obtenir des conseils sur la résolution des erreurs courantes de déploiement, consultez la page [Résolution des erreurs courantes de déploiement Azure avec Azure Resource Manager](resource-manager-common-deployment-errors.md).
* Pour plus d’informations sur le déploiement d’un modèle qui nécessite un jeton SAP, consultez [Déploiement d’un modèle privé avec un jeton SAP](resource-manager-cli-sas-token.md).
* Pour déployer en toute sécurité votre service sur plusieurs régions, consultez [Azure Deployment Manager](deployment-manager-overview.md).
