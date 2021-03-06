---
title: Dans ce didacticiel, vous allez créer une machine virtuelle Azure Stack à l’aide d’un modèle | Microsoft Docs
description: Explique comment utiliser le kit de développement Azure Stack pour créer une machine virtuelle à l’aide d’un modèle prédéfini et d’un modèle GitHub personnalisé.
services: azure-stack
documentationcenter: ''
author: sethmanheim
manager: femila
editor: ''
ms.assetid: ''
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.custom: mvc
ms.date: 11/13/2018
ms.author: sethm
ms.reviewer: ''
ms.openlocfilehash: 7780cfde52cb429503e57216e2543807d3fb1d1d
ms.sourcegitcommit: 0b7fc82f23f0aa105afb1c5fadb74aecf9a7015b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51632456"
---
# <a name="tutorial-create-a-vm-using-a-community-template"></a>Didacticiel : créer une machine virtuelle à l’aide d’un modèle communautaire

En tant qu’opérateur ou utilisateur Azure Stack, vous pouvez créer une machine virtuelle à l’aide de [modèles de démarrage rapide GitHub personnalisés](https://github.com/Azure/AzureStack-QuickStart-Templates), plutôt que d’en déployer une manuellement depuis le marketplace Azure Stack.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Utiliser des modèles de démarrage rapide Azure Stack 
> * Créer une machine virtuelle à l’aide d’un modèle GitHub personnalisé
> * Démarrer minikube et installer une application

## <a name="azure-stack-quickstart-templates"></a>Modèles de démarrage rapide Azure Stack

Les modèles de démarrage rapide Azure Stack sont stockés dans un [dépôt public](https://github.com/Azure/AzureStack-QuickStart-Templates) sur GitHub. Ce référentiel contient des modèles de déploiement Azure Resource Manager qui ont été testés avec le kit de développement Microsoft Azure Stack (ASDK). Vous pouvez les utiliser pour simplifier l’évaluation d’Azure Stack et l’utilisation de l’environnement du kit de développement Azure Stack (ASDK). 

Avec le temps, de nombreux utilisateurs GitHub ont contribué au dépôt, offrant ainsi une collection de plus de 400 modèles de déploiement. Ce référentiel constitue un excellent point de départ pour mieux comprendre comment déployer plusieurs types d’environnement dans Azure Stack. 

>[!IMPORTANT]
> Certains modèles présents sont créés par des membres de la communauté, et non par Microsoft. Chaque modèle est concédé sous licence sous un contrat de licence par son propriétaire, et non par Microsoft. Microsoft ne peut pas être tenu responsable de ces modèles ni ne vérifie leur sécurité, leur compatibilité ou leurs performances. Les modèles de la communauté ne sont pris en charge par aucun programme ou service de support Microsoft. Ils sont proposés « EN L’ÉTAT » sans garantie d’aucune sorte.

Si vous souhaitez mettre à la disposition de GitHub vos modèles Azure Resource Manager, utilisez le dépôt [AzureStack-QuickStart-Templates](https://github.com/Azure/AzureStack-QuickStart-Templates). Pour obtenir plus d’informations sur ce dépôt et savoir comment y contribuer, consultez le [fichier Lisez-moi](https://github.com/Azure/AzureStack-QuickStart-Templates/blob/master/README.md). 

## <a name="create-a-vm-using-a-custom-github-template"></a>Créer une machine virtuelle à l’aide d’un modèle GitHub personnalisé

Dans l’exemple de ce tutoriel, le modèle de démarrage rapide Azure Stack [101-vm-linux-minikube](https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/101-vm-linux-minikube) est utilisé pour déployer une machine virtuelle Ubuntu 16.04 sur Azure Stack qui exécute Minikube pour gérer un cluster Kubernetes.

Minikube est un outil qui simplifie l’exécution de Kubernetes en local. Minikube exécute un cluster Kubernetes à un seul nœud dans une machine virtuelle, qui vous permet d’essayer Kubernetes ou de développer avec au quotidien. Il prend en charge un simple cluster Kubernetes à un seul nœud qui s’exécute sur une machine virtuelle Linux. Minikube est le moyen le plus rapide et le plus direct pour exécuter un cluster Kubernetes entièrement opérationnel. Les développeurs peuvent ainsi développer et tester leurs déploiements d’applications basées sur Kubernetes sur leurs machines locales. Concernant l’architecture, une machine virtuelle Minikube exécute localement les composants du nœud principal et du nœud d’agent :

- Les composants du nœud principal, comme le serveur d’API, le planificateur et le [serveur etcd](https://coreos.com/etcd/) sont exécutés dans un même processus Linux appelé LocalKube.
- Les composants du nœud d’agent sont exécutés dans des conteneurs Docker, exactement comme s’ils étaient exécutés sur un nœud d’agent normal. Du point de vue du déploiement d’application, il n’y a aucune différence entre le déploiement d’une application sur un Minikube ou dans un cluster Kubernetes normal.

Ce modèle installe les composants suivants :

- Une machine virtuelle Ubuntu 16.04 LTS
- [Docker-CE](https://download.docker.com/linux/ubuntu) 
- [Kubectl](https://storage.googleapis.com/kubernetes-release/release/v1.8.0/bin/linux/amd64/kubectl)
- [Minikube](https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64)
- xFCE4
- xRDP

> [!IMPORTANT]
> L’image de machine virtuelle Ubuntu (Ubuntu Server 16.04 LTS dans notre exemple) doit avoir été ajoutée à la place de marché Azure Stack avant le démarrage de cette procédure.

1.  Sélectionnez **+ Créer une ressource**, **Personnalisé**, puis **Déploiement de modèle**.

    ![](media/azure-stack-create-vm-template/1.PNG) 

2. Sélectionnez **Modifier un modèle**.

    ![](media/azure-stack-create-vm-template/2.PNG) 

3.  Sélectionnez **Modèle de démarrage rapide**.

    ![](media/azure-stack-create-vm-template/3.PNG)

4. Sélectionnez **101-vm-linux-minikube** dans les modèles disponibles dans la liste déroulante **Sélectionner un modèle**, puis cliquez sur **OK**.  

    ![](media/azure-stack-create-vm-template/4.PNG)

5. Si vous le souhaitez, vous pouvez modifier le modèle JSON. Si vous n’avez pas de modifications à apporter ou si vous avez terminé, sélectionnez **Enregistrer** pour fermer la boîte de dialogue **Modifier le modèle**.

    ![](media/azure-stack-create-vm-template/5.PNG) 

6.  Sélectionnez **Paramètres**, renseignez ou modifiez les champs disponibles si nécessaire, puis cliquez sur **OK**. Sélectionnez l’abonnement à utiliser, créez ou choisissez un nom de groupe de ressources existant, puis sélectionnez **Créer** pour lancer le déploiement du modèle.

    ![](media/azure-stack-create-vm-template/6.PNG)

7. Sélectionnez l’abonnement à utiliser, créez ou choisissez un nom de groupe de ressources existant, puis sélectionnez **Créer** pour lancer le déploiement du modèle.

    ![](media/azure-stack-create-vm-template/7.PNG)

8. Le déploiement du groupe de ressources met quelques minutes à créer la machine virtuelle basée sur le modèle personnalisé. Vous pouvez surveiller l’état de l’installation via des notifications et depuis les propriétés du groupe de ressources. 

    ![](media/azure-stack-create-vm-template/8.PNG)

    >[!NOTE]
    > La machine virtuelle s’exécute lorsque le déploiement est terminé. 

## <a name="start-minikube-and-install-an-application"></a>Démarrer Minikube et installer une application

Maintenant que la machine virtuelle Linux est créée, vous pouvez vous connecter pour démarrer Minikube et installer une application. 

1. Une fois le déploiement terminé, sélectionnez **Connexion** pour afficher l’adresse IP publique qui sera utilisée pour se connecter à la machine virtuelle Linux. 

    ![](media/azure-stack-create-vm-template/9.PNG)

2. À partir d’une invite de commandes avec élévation de privilèges, exécutez la commande **mstsc.exe** pour ouvrir la connexion Bureau à distance et vous connecter à l’adresse IP publique de la machine virtuelle Linux obtenue à l’étape précédente. Lorsque vous êtes invité à vous connecter à xRDP, utilisez les informations d’identification que vous avez spécifiées lors de la création de la machine virtuelle.

    ![](media/azure-stack-create-vm-template/10.PNG)

3. Ouvrez l’émulateur de terminal et entrez les commandes suivantes pour démarrer Minikube :

    ```shell
    sudo minikube start --vm-driver=none
    sudo minikube addons enable dashboard
    sudo minikube dashboard --url
    ```

    ![](media/azure-stack-create-vm-template/11.PNG)

4. Ouvrez le navigateur web et accédez à l’adresse du tableau de bord Kubernetes. Félicitations ! Vous disposez maintenant d’une installation Kubernetes entièrement opérationnelle utilisant Minikube.

    ![](media/azure-stack-create-vm-template/12.PNG)

5. Pour déployer un exemple d’application, accédez à la page de documentation officielle de Kubernetes et ignorez la section « Create Minikube Cluster » (Créer un cluster Minikube) car vous venez d’en créer un. Passez à la section « Create your Node.js application » (Créer votre application Node.js) sur https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à :

> [!div class="checklist"]
> * En savoir plus sur les modèles de démarrage rapide Azure Stack 
> * Créer une machine virtuelle à l’aide d’un modèle GitHub personnalisé
> * Démarrer minikube et installer une application

