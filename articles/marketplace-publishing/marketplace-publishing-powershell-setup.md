---
title: Configuration de PowerShell pour créer une machine virtuelle pour Marketplace | Microsoft Docs
description: Instructions pour configurer Azure PowerShell et l’utiliser comme processus facultatif pour créer des images de machines virtuelles à déployer et à vendre sur Azure Marketplace
services: marketplace-publishing
documentationcenter: ''
author: v-miclar
manager: hascipio
editor: ''
ms.assetid: e19d6cda-76df-4e42-be84-c9fe47a636db
ms.service: marketplace
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/04/2016
ms.author: hascipio
ROBOTS: NOINDEX
ms.openlocfilehash: e5175558f18dfc903c280ea6bbe487e0a3ee8189
ms.sourcegitcommit: fbf0124ae39fa526fc7e7768952efe32093e3591
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54076601"
---
# <a name="set-up-azure-powershell-to-create-an-offer-for-the-azure-marketplace"></a>Configurer Azure PowerShell pour créer une offre pour Azure Marketplace

Pour plus d’informations sur la configuration de PowerShell dans Azure, consultez [Installation et configuration d’Azure PowerShell](/powershell/azure/overview). Une approche simple consiste à utiliser la méthode de certificat, qui télécharge et importe le certificat nécessaire à l’authentification. Pour obtenir le certificat requis, utilisez l’applet de commande **Get-AzurePublishSettingsFile** . Enregistrez le fichier lorsque vous y êtes invité. Pour importer le certificat dans une session PowerShell, utilisez l’applet de commande **Import-AzurePublishSettingsFile** .

Pour configurer et stocker les paramètres d’abonnement Microsoft Azure communs pour la session PowerShell, utilisez les applets de commande **Set-AzureSubscription** et **Select-AzureSubscription** :

        Set-AzureSubscription -SubscriptionName “mySubName” -CurrentStorageAccountName “mystorageaccount”
        Select-AzureSubscription -SubscriptionName "mySubName" –Current

La première commande associe un compte de stockage par défaut à l’abonnement (nécessaire pour certaines opérations d’approvisionnement de la machine virtuelle).  La seconde définit l’abonnement comme abonnement actif (reconnu par les autres applets de commande).

Pour plus d’informations, consultez les articles suivants :
* [Prise en main : Comment publier une offre dans la Place de marché Microsoft Azure](marketplace-publishing-getting-started.md)
* [Création d’une image de machine virtuelle pour la Place de Marché](marketplace-publishing-vm-image-creation.md)

