---
title: Vue d’ensemble d’App Service sur Azure Stack | Microsoft Docs
description: Vue d’ensemble d’App Service sur Azure Stack
services: azure-stack
documentationcenter: ''
author: sethmanheim
manager: femila
ms.assetid: ''
ms.service: azure-stack
ms.workload: app-service
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/16/2018
ms.author: sethm
ms.reviewer: anwestg
ms.openlocfilehash: b1b4ea5775a661712838c1495ef0025a83b8c518
ms.sourcegitcommit: 4eeeb520acf8b2419bcc73d8fcc81a075b81663a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53607941"
---
# <a name="app-service-on-azure-stack-overview"></a>Vue d’ensemble d’App Service sur Azure Stack

*S’applique à : systèmes intégrés Azure Stack et Kit de développement Azure Stack*

Azure App Service sur Azure Stack est une offre PaaS (platform-as-a-service) de Microsoft Azure disponible sur Azure Stack. Le service permet à vos clients internes ou externes de créer des applications web, d’API et Azure Functions pour la plateforme ou l’appareil de leur choix. Ils peuvent intégrer des applications locales à vos applications et automatiser leurs processus d’entreprise. Les opérateurs de cloud Azure Stack peuvent exécuter les applications client sur des machines virtuelles entièrement gérées, avec les ressources de machines virtuelles partagées ou les machines virtuelles dédiées de votre choix.

Azure App Service vous permet d’automatiser des processus métier et des API cloud d’hôte. En tant que service intégré unique, Azure App Service vous permet d’assembler différents composants, comme des sites web, des API REST et des processus métier, dans une seule solution.

## <a name="why-offer-azure-app-service-on-azure-stack"></a>Pourquoi proposer Azure App Service sur Azure Stack ?

Voici quelques fonctionnalités et capacités clés d’App Service :

- **Plusieurs langages et frameworks** : App Service offre une excellente prise en charge d’ASP.NET, Node.js, Java, PHP et Python. Vous pouvez également exécuter Windows PowerShell et d’autres scripts ou exécutables sur les machines virtuelles App Service.
- **Optimisation DevOps** : configurez l’intégration et le déploiement continus avec GitHub, local Git, ou BitBucket. Vous pouvez promouvoir des mises à jour dans des environnements de test et de préproduction, et gérer vos applications dans App Service à l’aide d’Azure PowerShell ou de l’interface de ligne de commande (CLI) multiplateforme.
- **Intégration à Visual Studio** : les outils dédiés de Visual Studio simplifient le travail de création et de déploiement d’applications.

## <a name="app-types-in-app-service"></a>Types d’applications dans App Service

App Service offre plusieurs types d’application, chacun d’eux étant destiné à héberger une charge de travail spécifique :

- [Web Apps](../app-service/overview.md) pour l’hébergement de sites et d’applications web.
- [API Apps](../app-service/overview.md) pour l’hébergement d’API REST.
- Azure Functions pour l’hébergement de charges de travail sans serveur, pilotées par les événements.

Le mot *application* fait référence aux ressources d’hébergement dédiées à l’exécution d’une charge de travail. Par exemple, vous avez certainement coutume de penser qu’une *application web* se compose de ressources de calcul et de code d’application qui, ensemble, offrent des fonctionnalités à un navigateur. Dans App Service, une application web est la ressource de calcul fournie par Azure Stack pour héberger votre code d’application.

Votre application peut être composée d’applications App Service de différents types. Par exemple, si votre application se compose d’un front-end web et d’un back-end d’API REST, vous pouvez :

- Déployer les deux (serveur frontal et API) sur une seule application web
- Déployer votre code frontal dans une application web et votre code principal dans une application API.

   [ ![Vue d’ensemble d’App Service avec des données de supervision](media/azure-stack-app-service-overview/image01.png "Vue d’ensemble d’App Service avec des données de supervision") ](media/azure-stack-app-service-overview/image01.png#lightbox)

## <a name="what-is-an-app-service-plan"></a>Qu’est-ce qu’un plan App Service ?

Le fournisseur de ressources App Service utilise le même code que celui utilisé par Azure App Service, et donc partage certains concepts communs. Dans App Service, le conteneur des tarifs des applications est appelé *plan App Service*. Il représente l’ensemble des machines virtuelles dédiées utilisées pour contenir vos applications. Vous pouvez avoir plusieurs plans App Service dans un abonnement donné.

Dans Azure, il existe des Workers partagés et dédiés. Un worker partagé prend en charge l’hébergement d’applications multilocataires à densité élevée et il n’existe qu’un seul ensemble de workers partagés. Les serveurs dédiés sont utilisés par un seul locataire et se présentent dans trois tailles : petit, moyen et grand. Les besoins des clients locaux ne peuvent pas toujours être décrits en ces termes. Dans App Service sur Azure Stack, les administrateurs du fournisseur de ressources peuvent définir les niveaux Worker qu’ils souhaitent rendre disponibles. Vous pouvez définir plusieurs jeux de Workers partagés ou des jeux différents de Workers dédiés selon leurs besoins d’hébergements uniques. À l’aide de ces définitions de niveau Worker, ils peuvent ensuite définir leurs propres références de tarification.

## <a name="portal-features"></a>Fonctionnalités du portail

App Service sur Azure Stack utilise la même interface utilisateur que celle utilisée par Azure App Service. Il en est de même avec le back-end. Cependant, certaines fonctionnalités sont désactivées dans Azure Stack. Les attentes ou les services spécifiques à Azure dont ont besoin ces fonctionnalités ne sont pas encore disponibles dans Azure Stack.

## <a name="next-steps"></a>Étapes suivantes

- [Avant de commencer avec App Service sur Azure Stack](azure-stack-app-service-before-you-get-started.md)
- [Installer le fournisseur de ressources App Service](azure-stack-app-service-deploy.md)

Vous pouvez également tester d’autres [services PaaS](azure-stack-tools-paas-services.md), comme le [fournisseur de ressources SQL Server](azure-stack-sql-resource-provider-deploy.md) et le [fournisseur de ressources MySQL](azure-stack-mysql-resource-provider-deploy.md).
