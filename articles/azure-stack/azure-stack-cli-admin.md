---
title: Activer Azure CLI pour les utilisateurs d’Azure Stack | Microsoft Docs
description: Découvrez comment utiliser l’interface de ligne de commande (CLI) multiplateforme pour gérer et déployer des ressources sur Azure Stack.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
editor: ''
ms.assetid: f576079c-5384-4c23-b5a4-9ae165d1e3c3
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 09/28/2018
ms.author: mabrigg
ms.openlocfilehash: c2827a4badd61aeb8de556795834dee39769e85e
ms.sourcegitcommit: b767a6a118bca386ac6de93ea38f1cc457bb3e4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53554501"
---
# <a name="enable-azure-cli-for-azure-stack-users"></a>Activer Azure CLI pour les utilisateurs d’Azure Stack

*S’applique à : systèmes intégrés Azure Stack et Kit de développement Azure Stack*

Vous pouvez fournir le certificat racine de l’autorité de certification aux utilisateurs d’Azure Stack afin qu’ils puissent utiliser Azure CLI sur leurs machines de développement. Les utilisateurs ont besoin du certificat pour gérer des ressources à l’aide de l’interface CLI.

* **Le certificat racine de l’autorité de certification Azure Stack** est obligatoire si des utilisateurs utilisent l’interface CLI sur une station de travail qui se trouve en dehors du Kit de développement Azure Stack.  

* **Le point de terminaison des alias de machines virtuelles** fournit un alias, comme « UbuntuLTS » ou « Win2012Datacenter », qui référence un éditeur, une offre, une référence (SKU) et une version d’image sous la forme d’un seul paramètre lors du déploiement de machines virtuelles.  

Les sections suivantes expliquent comment obtenir ces valeurs.

## <a name="export-the-azure-stack-ca-root-certificate"></a>Exporter le certificat racine d’autorité de certification Azure Stack

Vous pouvez trouver le certificat racine de l’autorité de certification Azure Stack dans le kit de développement et sur une machine virtuelle locataire exécutée dans l’environnement du kit de développement. Pour exporter le certificat racine Azure Stack au format PEM, connectez-vous à votre kit de développement ou à la machine virtuelle du locataire, et exécutez le script suivant :

```powershell
$label = "<Your Azure Stack CA root certificate name>"
Write-Host "Getting certificate from the current user trusted store with subject CN=$label"
$root = Get-ChildItem Cert:\CurrentUser\Root | Where-Object Subject -eq "CN=$label" | select -First 1
if (-not $root)
{
    Log-Error "Certificate with subject CN=$label not found"
    return
}

Write-Host "Exporting certificate"
Export-Certificate -Type CERT -FilePath root.cer -Cert $root

Write-Host "Converting certificate to PEM format"
certutil -encode root.cer root.pem
```

## <a name="set-up-the-virtual-machine-aliases-endpoint"></a>Configurer le point de terminaison des alias de machines virtuelles

Nous recommandons aux opérateurs Azure Stack de configurer un point de terminaison accessible publiquement qui héberge un fichier d’alias de machines virtuelles. Le fichier d’alias de machines virtuelles est un fichier JSON qui fournit un nom commun pour une image. Ce nom est spécifié par la suite comme paramètre Azure CLI quand une machine virtuelle est déployée.  

Avant d’ajouter une entrée à un fichier d’alias, pensez à [télécharger les images à partir de la Place de marché Azure](azure-stack-download-azure-marketplace-item.md) ou à [publier votre propre image personnalisée](azure-stack-add-vm-image.md). Si vous publiez une image personnalisée, prenez note des informations concernant l’éditeur, l’offre, la référence (SKU) et la version que vous avez spécifiées lors de la publication. S’il s’agit d’une image provenant de la Place de marché, vous pouvez afficher les informations en utilisant l’applet de commande ```Get-AzureVMImage```.  

Un [exemple de fichier d’alias](https://raw.githubusercontent.com/Azure/azure-rest-api-specs/master/arm-compute/quickstart-templates/aliases.json) contenant de nombreux alias d’images communs est disponible. Vous pouvez l’utiliser comme point de départ. Hébergez ce fichier dans un espace accessible à vos clients utilisant l’interface CLI. Une façon de le faire consiste à héberger le fichier dans un compte Stockage Blob et à partager l’URL avec vos utilisateurs :

1. Téléchargez l’[ exemple de fichier](https://raw.githubusercontent.com/Azure/azure-rest-api-specs/master/arm-compute/quickstart-templates/aliases.json) à partir de GitHub.
2. Créez un compte de stockage dans Azure Stack. Après cela, créez un conteneur d’objets blob. Définissez la stratégie d’accès sur « publique ».  
3. Chargez le fichier JSON dans le nouveau conteneur. À la fin de cette opération, vous pouvez afficher l’URL de l’objet blob en sélectionnant le nom de l’objet blob, puis en sélectionnant l’URL dans ses propriétés.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer des modèles avec l’interface de ligne de commande Azure](azure-stack-deploy-template-command-line.md)
- [Se connecter avec PowerShell](azure-stack-connect-powershell.md)
- [Gérer les autorisations utilisateur](azure-stack-manage-permissions.md)
