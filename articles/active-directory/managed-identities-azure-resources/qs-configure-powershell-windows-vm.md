---
title: Guide de configuration d’identités managées pour ressources Azure sur une machine virtuelle Azure en utilisant PowerShell
description: Instructions détaillées pour configurer des identités managées pour ressources Azure sur une machine virtuelle Azure en utilisant PowerShell.
services: active-directory
documentationcenter: ''
author: daveba
manager: mtillman
editor: ''
ms.service: active-directory
ms.component: msi
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 11/27/2017
ms.author: daveba
ms.openlocfilehash: a29980da64775ca39f103b7430239f38c98a43fc
ms.sourcegitcommit: 0fc99ab4fbc6922064fc27d64161be6072896b21
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51578450"
---
# <a name="configure-managed-identities-for-azure-resources-on-an-azure-vm-using-powershell"></a>Configurer des identités managées pour ressources Azure sur une machine virtuelle Azure en utilisant PowerShell

[!INCLUDE [preview-notice](../../../includes/active-directory-msi-preview-notice.md)]

Les identités managées pour ressources Azure fournissent des services Azure avec une identité managée automatiquement dans Azure Active Directory. Vous pouvez utiliser cette identité pour vous authentifier sur n’importe quel service prenant en charge l’authentification Azure AD, sans avoir d’informations d’identification dans votre code. 

Cet article explique comment effectuer les opérations suivantes d’identités managées pour ressources Azure sur une machine virtuelle Azure en utilisant PowerShell :

## <a name="prerequisites"></a>Prérequis

- Si vous n’êtes pas familiarisé avec les identités managées pour ressources Azure, consultez la [section Vue d’ensemble](overview.md). **Veillez à consulter la [différence entre les identités managées affectées par le système et celles affectées par l’utilisateur](overview.md#how-does-it-work)**.
- Si vous n’avez pas encore de compte Azure, [inscrivez-vous à un essai gratuit](https://azure.microsoft.com/free/) avant de continuer.
- Installez [la dernière version d’Azure PowerShell](https://www.powershellgallery.com/packages/AzureRM) si ce n’est déjà fait.

## <a name="system-assigned-managed-identity"></a>Identité managée affectée par le système

Dans cette section, vous allez découvrir comment activer et désactiver l’identité managée affectée par le système en utilisant Azure PowerShell.

### <a name="enable-system-assigned-managed-identity-during-creation-of-an-azure-vm"></a>Activer une identité managée affectée par le système lors de la création d’une machine virtuelle Azure

Pour créer une machine virtuelle Azure avec l’identité managée affectée par le système sur une machine virtuelle, votre compte a besoin de l’affectation de rôle [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor).  Aucune attribution de rôle d’annuaire Azure AD supplémentaire n’est requise.

1. Consultez l’un des démarrages rapides de machine virtuelle Azure suivants, en ne complétant que les sections nécessaires (« Se connecter à Azure », « Créer un groupe de ressources », « Créer un groupe de mise en réseau », « Créer la machine virtuelle »).
    
    Lorsque vous accédez à la section « Créer la machine virtuelle », apportez une légère modification à la syntaxe de l’applet de commande [New-AzureRmVMConfig](/powershell/module/azurerm.compute/new-azurermvm). Veillez à ajouter un paramètre `-AssignIdentity:$SystemAssigned` afin d’approvisionner la machine virtuelle avec l’identité affectée par le système activée, par exemple :
      
    ```powershell
    $vmConfig = New-AzureRmVMConfig -VMName myVM -AssignIdentity:$SystemAssigned ...
    ```

   - [Créer une machine virtuelle Windows avec PowerShell](../../virtual-machines/windows/quick-create-powershell.md)
   - [Créer une machine virtuelle Linux avec PowerShell](../../virtual-machines/linux/quick-create-powershell.md)

2. (Facultatif) Ajoutez l’extension de machine virtuelle d’identités managées pour ressources Azure (dont l’abandon est prévu en janvier 2019) en utilisant le paramètre `-Type` sur l’applet de commande [Set-AzureRmVMExtension](/powershell/module/azurerm.compute/set-azurermvmextension). Vous pouvez transmettre « ManagedIdentityExtensionForWindows » ou « ManagedIdentityExtensionForLinux », selon le type de machine virtuelle, et nommez-le à l’aide paramètre `-Name`. Le paramètre `-Settings` spécifie le port utilisé par le point de terminaison de jeton OAuth pour l’acquisition de jeton :

   ```powershell
   $settings = @{ "port" = 50342 }
   Set-AzureRmVMExtension -ResourceGroupName myResourceGroup -Location WestUS -VMName myVM -Name "ManagedIdentityExtensionForWindows" -Type "ManagedIdentityExtensionForWindows" -Publisher "Microsoft.ManagedIdentity" -TypeHandlerVersion "1.0" -Settings $settings 
   ```
    > [!NOTE]
    > Cette étape est facultative, car vous pouvez également utiliser le point de terminaison d’identité IMDS (Instance Metadata Service) Azure pour récupérer des jetons. L’extension de machine virtuelle d’identités managées pour ressources Azure doit être abandonnée en janvier 2019. 

### <a name="enable-system-assigned-managed-identity-on-an-existing-azure-vm"></a>Activer une identité managée affectée par le système sur une machine virtuelle Azure existante

Pour activer l’identité managée affectée par le système sur une machine virtuelle qui en était dépourvue initialement, votre compte a besoin de l’affectation de rôle [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor).  Aucune attribution de rôle d’annuaire Azure AD supplémentaire n’est requise.

1. Connectez-vous au portail Azure à l’aide de `Login-AzureRmAccount`. Utilisez un compte associé à l’abonnement Azure qui contient la machine virtuelle.

   ```powershell
   Login-AzureRmAccount
   ```

2. Commencez par récupérer les propriétés de la machine virtuelle à l’aide de la cmdlet `Get-AzureRmVM`. Ensuite, pour activer une identité managée affectée par le système, utilisez le commutateur `-AssignIdentity` avec l’applet de commande [Update-AzureRmVM](/powershell/module/azurerm.compute/update-azurermvm) :

   ```powershell
   $vm = Get-AzureRmVM -ResourceGroupName myResourceGroup -Name myVM
   Update-AzureRmVM -ResourceGroupName myResourceGroup -VM $vm -AssignIdentity:$SystemAssigned
   ```

3. (Facultatif) Ajoutez l’extension de machine virtuelle d’identités managées pour ressources Azure (dont l’abandon est prévu en janvier 2019) en utilisant le paramètre `-Type` sur l’applet de commande [Set-AzureRmVMExtension](/powershell/module/azurerm.compute/set-azurermvmextension). Vous pouvez transmettre « ManagedIdentityExtensionForWindows » ou « ManagedIdentityExtensionForLinux », selon le type de machine virtuelle, et nommez-le à l’aide paramètre `-Name`. Le paramètre `-Settings` spécifie le port utilisé par le point de terminaison de jeton OAuth pour l’acquisition de jeton. Veillez à indiquer le paramètre `-Location` approprié, correspondant à l’emplacement de la machine virtuelle existante :

   ```powershell
   $settings = @{ "port" = 50342 }
   Set-AzureRmVMExtension -ResourceGroupName myResourceGroup -Location WestUS -VMName myVM -Name "ManagedIdentityExtensionForWindows" -Type "ManagedIdentityExtensionForWindows" -Publisher "Microsoft.ManagedIdentity" -TypeHandlerVersion "1.0" -Settings $settings 
   ```
    > [!NOTE]
    > Cette étape est facultative, car vous pouvez également utiliser le point de terminaison d’identité IMDS (Instance Metadata Service) Azure pour récupérer des jetons.

## <a name="disable-system-assigned-managed-identity-from-an-azure-vm"></a>Désactiver une identité managée affectée par le système d’une machine virtuelle Azure

Pour désactiver l’identité managée affectée par le système sur une machine virtuelle, votre compte a besoin de l’affectation de rôle [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor).  Aucune attribution de rôle d’annuaire Azure AD supplémentaire n’est requise.

Si vous disposez d’une machine virtuelle qui n’a plus besoin de l’identité managée affectée par le système, mais qui a toujours besoin d’identités managées affectées par l’utilisateur, utilisez l’applet de commande suivante :

1. Connectez-vous au portail Azure à l’aide de `Login-AzureRmAccount`. Utilisez un compte associé à l’abonnement Azure qui contient la machine virtuelle.

   ```powershell
   Login-AzureRmAccount
   ```

2. Récupérez les propriétés de la machine virtuelle à l’aide de l’applet de commande `Get-AzureRmVM` et définissez le paramètre `-IdentityType` sur `UserAssigned` :

   ```powershell   
   $vm = Get-AzureRmVM -ResourceGroupName myResourceGroup -Name myVM    
   Update-AzureRmVm -ResourceGroupName myResourceGroup -VM $vm -IdentityType "UserAssigned"
   ```

Si vous disposez d’une machine virtuelle qui n’a plus besoin de l’identité managée affectée par le système et qui n’a pas d’identité managée affectée par l’utilisateur, utilisez les commandes suivantes :

```powershell
$vm = Get-AzureRmVM -ResourceGroupName myResourceGroup -Name myVM
Update-AzureRmVm -ResourceGroupName myResourceGroup -VM $vm -IdentityType None
```

Pour supprimer l’extension de machine virtuelle d’identités managées pour ressources Azure, utilisez le commutateur -Name avec l’applet de commande [Remove-AzureRmVMExtension](/powershell/module/azurerm.compute/remove-azurermvmextension), en spécifiant le même nom que celui que vous avez utilisé lors de l’ajout de l’extension :

   ```powershell
   Remove-AzureRmVMExtension -ResourceGroupName myResourceGroup -Name "ManagedIdentityExtensionForWindows" -VMName myVM
   ```

## <a name="user-assigned-managed-identity"></a>Identité managée affectée par l’utilisateur

Dans cette section, vous allez découvrir comment ajouter et supprimer une identité managée affectée par l’utilisateur sur une machine virtuelle en utilisant Azure PowerShell.

### <a name="assign-a-user-assigned-managed-identity-to-a-vm-during-creation"></a>Attribuer une identité managée affectée par l’utilisateur à une machine virtuelle lors de sa création

Pour affecter une identité managée affectée par l’utilisateur à une machine virtuelle, votre compte a besoin de l’affectation de rôle [Opérateur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) et [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#managed-identity-operator). Aucune attribution de rôle d’annuaire Azure AD supplémentaire n’est requise.

1. Consultez l’un des démarrages rapides de machine virtuelle Azure suivants, en ne complétant que les sections nécessaires (« Se connecter à Azure », « Créer un groupe de ressources », « Créer un groupe de mise en réseau », « Créer la machine virtuelle »). 
  
    Quand vous parvenez à la section « Créer la machine virtuelle », apportez une légère modification à la syntaxe de l’applet de commande [`New-AzureRmVMConfig`](/powershell/module/azurerm.compute/new-azurermvm). Ajoutez les paramètres `-IdentityType UserAssigned` et `-IdentityID ` pour approvisionner la machine virtuelle avec une identité affectée par l’utilisateur.  Remplacez `<VM NAME>`, `<SUBSCRIPTION ID>`, `<RESROURCE GROUP>` et `<USER ASSIGNED IDENTITY NAME>` par vos propres valeurs.  Par exemple : 
    
    ```powershell 
    $vmConfig = New-AzureRmVMConfig -VMName <VM NAME> -IdentityType UserAssigned -IdentityID "/subscriptions/<SUBSCRIPTION ID>/resourcegroups/<RESROURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>..."
    ```
    
    - [Créer une machine virtuelle Windows avec PowerShell](../../virtual-machines/windows/quick-create-powershell.md)
    - [Créer une machine virtuelle Linux avec PowerShell](../../virtual-machines/linux/quick-create-powershell.md)

2. (Facultatif) Ajoutez l’extension de machine virtuelle d’identité managée pour ressources Azure en utilisant le paramètre `-Type` avec l’applet de commande [Set-AzureRmVMExtension](/powershell/module/azurerm.compute/set-azurermvmextension). Vous pouvez transmettre « ManagedIdentityExtensionForWindows » ou « ManagedIdentityExtensionForLinux », selon le type de machine virtuelle, et nommez-le à l’aide paramètre `-Name`. Le paramètre `-Settings` spécifie le port utilisé par le point de terminaison de jeton OAuth pour l’acquisition de jeton. Veillez à indiquer le paramètre `-Location` approprié, correspondant à l’emplacement de la machine virtuelle existante :
      > [!NOTE]
    > Cette étape est facultative, car vous pouvez également utiliser le point de terminaison d’identité IMDS (Instance Metadata Service) Azure pour récupérer des jetons. L’extension de machine virtuelle d’identités managées pour ressources Azure doit être abandonnée en janvier 2019.

   ```powershell
   $settings = @{ "port" = 50342 }
   Set-AzureRmVMExtension -ResourceGroupName myResourceGroup -Location WestUS -VMName myVM -Name "ManagedIdentityExtensionForWindows" -Type "ManagedIdentityExtensionForWindows" -Publisher "Microsoft.ManagedIdentity" -TypeHandlerVersion "1.0" -Settings $settings 
   ```

### <a name="assign-a-user-assigned-managed-identity-to-an-existing-azure-vm"></a>Attribuer une identité managée affectée par l’utilisateur à une machine virtuelle Azure existante

Pour affecter une identité managée affectée par l’utilisateur à une machine virtuelle, votre compte a besoin de l’affectation de rôle [Opérateur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) et [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#managed-identity-operator). Aucune attribution de rôle d’annuaire Azure AD supplémentaire n’est requise.

1. Connectez-vous au portail Azure à l’aide de `Connect-AzureRmAccount`. Utilisez un compte associé à l’abonnement Azure qui contient la machine virtuelle.

   ```powershell
   Connect-AzureRmAccount
   ```

2. Créez une identité managée affectée par l’utilisateur en utilisant l’applet de commande [New-AzureRmUserAssignedIdentity](/powershell/module/azurerm.managedserviceidentity/new-azurermuserassignedidentity).  Notez la valeur `Id` dans la sortie, car vous en aurez besoin à l’étape suivante.

   > [!IMPORTANT]
   > La création d’identités managées affectées par l’utilisateur prend uniquement en charge les caractères alphanumériques et les traits d’union (0-9, a-z, A-Z ou -). De plus, le nom doit être limité à 24 caractères pour que l’attribution à la machine virtuelle/au groupe de machines virtuelles identiques fonctionne correctement. Revenez ultérieurement pour des mises à jour. Pour plus d’informations, consultez [FAQ et problèmes connus](known-issues.md)

   ```powershell
   New-AzureRmUserAssignedIdentity -ResourceGroupName <RESOURCEGROUP> -Name <USER ASSIGNED IDENTITY NAME>
   ```
3. Récupérez les propriétés de la machine virtuelle à l’aide de l’applet de commande `Get-AzureRmVM`. Ensuite, pour attribuer une identité managée affectée par l’utilisateur à la machine virtuelle Azure, utilisez les commutateurs `-IdentityType` et `-IdentityID` avec l’applet de commande [Update-AzureRmVM](/powershell/module/azurerm.compute/update-azurermvm).  La valeur du paramètre `-IdentityId` est la valeur `Id` que vous avez notée à l’étape précédente.  Remplacez `<VM NAME>`, `<SUBSCRIPTION ID>`, `<RESROURCE GROUP>` et `<USER ASSIGNED IDENTITY NAME>` par vos propres valeurs.

   > [!WARNING]
   > Pour conserver les identités managées précédemment affectées par l’utilisateur à la machine virtuelle, effectuez une requête sur la propriété `Identity` de l’objet machine virtuelle (par exemple, `$vm.Identity`).  Si de telles identités managées sont retournées, ajoutez-les à la commande suivante, avec la nouvelle identité managée affectée par l’utilisateur que vous souhaitez affecter à la machine virtuelle.

   ```powershell
   $vm = Get-AzureRmVM -ResourceGroupName <RESOURCE GROUP> -Name <VM NAME>
   Update-AzureRmVM -ResourceGroupName <RESOURCE GROUP> -VM $vm -IdentityType UserAssigned -IdentityID "/subscriptions/<SUBSCRIPTION ID>/resourcegroups/<RESROURCE GROUP>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<USER ASSIGNED IDENTITY NAME>"
   ```

4. Ajoutez l’extension de machine virtuelle d’identités managées pour ressources Azure (dont l’abandon est prévu en janvier 2019) en utilisant le paramètre `-Type` sur l’applet de commande [Set-AzureRmVMExtension](/powershell/module/azurerm.compute/set-azurermvmextension). Vous pouvez transmettre « ManagedIdentityExtensionForWindows » ou « ManagedIdentityExtensionForLinux », selon le type de machine virtuelle, et nommez-le à l’aide paramètre `-Name`. Le paramètre `-Settings` spécifie le port utilisé par le point de terminaison de jeton OAuth pour l’acquisition de jeton. Spécifiez le paramètre `-Location` approprié, correspondant à l’emplacement de la machine virtuelle existante.

   ```powershell
   $settings = @{ "port" = 50342 }
   Set-AzureRmVMExtension -ResourceGroupName myResourceGroup -Location WestUS -VMName myVM -Name "ManagedIdentityExtensionForWindows" -Type "ManagedIdentityExtensionForWindows" -Publisher "Microsoft.ManagedIdentity" -TypeHandlerVersion "1.0" -Settings $settings 
   ```

### <a name="remove-a-user-assigned-managed-identity-from-an-azure-vm"></a>Supprimer une identité managée affectée par l’utilisateur d’une machine virtuelle Azure

Pour supprimer une identité affectée par l’utilisateur à une machine virtuelle, votre compte a besoin de l’affectation de rôle [Contributeur d’identité managée](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor).

Si votre machine virtuelle a plusieurs identités managées affectées par l’utilisateur, vous pouvez les supprimer toutes sauf la dernière à l’aide des commandes suivantes. N’oubliez pas de remplacer les valeurs des paramètres `<RESOURCE GROUP>` et `<VM NAME>` par vos propres valeurs. `<USER ASSIGNED IDENTITY NAME>` est la propriété de nom de l’identité managée affectée par l’utilisateur, qui doit rester sur la machine virtuelle. Pour obtenir cette information, effectuez une requête sur la propriété `Identity` de l’objet machine virtuelle.  Par exemple, `$vm.Identity`:

```powershell
$vm = Get-AzureRmVm -ResourceGroupName myResourceGroup -Name myVm
Update-AzureRmVm -ResourceGroupName myResourceGroup -VirtualMachine $vm -IdentityType UserAssigned -IdentityID <USER ASSIGNED IDENTITY NAME>
```
Si votre machine virtuelle ne dispose pas d’une identité managée affectée par le système, et si vous souhaitez supprimer toutes les identités managées affectées par l’utilisateur, utilisez la commande suivante :

```powershell
$vm = Get-AzureRmVm -ResourceGroupName myResourceGroup -Name myVm
Update-AzureRmVm -ResourceGroupName myResourceGroup -VM $vm -IdentityType None
```
Si votre machine virtuelle dispose d’identités managées affectées tant par le système que par l’utilisateur, vous pouvez supprimer toutes les identités managées affectées par l’utilisateur en choisissant de n’utiliser que l’identité managée affectée par le système.

```powershell 
$vm = Get-AzureRmVm -ResourceGroupName myResourceGroup -Name myVm
Update-AzureRmVm -ResourceGroupName myResourceGroup -VirtualMachine $vm -IdentityType "SystemAssigned"
```

## <a name="next-steps"></a>Étapes suivantes

- [Vue d’ensemble des identités managées pour les ressources Azure](overview.md)
- Pour obtenir les guides de démarrages rapides complets sur la création de machines virtuelles Azure, consultez :
  
  - [Créer une machine virtuelle Windows avec PowerShell](../../virtual-machines/windows/quick-create-powershell.md) 
  - [Créer une machine virtuelle Linux avec PowerShell](../../virtual-machines/linux/quick-create-powershell.md) 
