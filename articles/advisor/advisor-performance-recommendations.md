---
title: Recommandations Azure Advisor en matière de performances | Microsoft Docs
description: Utilisez Advisor pour optimiser les performances de vos déploiements Azure.
services: advisor
documentationcenter: NA
author: kasparks
manager: carmonm
editor: ''
ms.assetid: ''
ms.service: advisor
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 11/16/2016
ms.author: kasparks
ms.openlocfilehash: 349632c751c3116244bc8ef7708708f3aa45754c
ms.sourcegitcommit: 698ba3e88adc357b8bd6178a7b2b1121cb8da797
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53013234"
---
# <a name="advisor-performance-recommendations"></a>Recommandations Azure Advisor en matière de performances

Les recommandations d’Azure Advisor en matière de performances vous aident à optimiser la vitesse et la réactivité de vos applications stratégiques. Vous pouvez obtenir des recommandations en matière de performances à l’aide d’Advisor dans l’onglet **Performances** du tableau de bord d’Advisor.

## <a name="reduce-dns-time-to-live-on-your-traffic-manager-profile-to-fail-over-to-healthy-endpoints-faster"></a>Diminuer la durée de vie DNS dans votre profil Traffic Manager pour passer plus rapidement à des points de terminaison intègres

Les [paramètres TTL (durée de vie)](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-performance-considerations) de votre profil Traffic Manager permettent de spécifier l’intervalle de temps nécessaire avant de changer de point de terminaison lorsque celui-ci ne répond plus. Lorsque l’on réduit les valeurs TTL, les clients sont redirigés plus rapidement vers des points de terminaison opérationnels.

Azure Advisor identifie les profils Traffic Manager ayant une valeur TTL élevée et recommande de la régler à 20 secondes ou 60 secondes selon que le profil est configuré pour une [Bascule rapide](https://azure.microsoft.com/roadmap/fast-failover-and-tcp-probing-in-azure-traffic-manager/).

## <a name="improve-database-performance-with-sql-db-advisor"></a>Améliorer les performances de base de données avec SQL DB Advisor

Le conseiller vous offre une vue cohérente et consolidée des recommandations pour toutes vos ressources Azure. Il s’intègre à SQL Database Advisor pour vous proposer des recommandations en vue d’améliorer les performances de votre base de données SQL Azure. SQL Database Advisor évalue les performances de vos bases de données SQL Azure en analysant votre historique d’utilisation. Il propose alors les recommandations les plus adaptées pour exécuter la charge de travail standard de la base de données. 

> [!NOTE]
> Pour obtenir des recommandations, une base de données doit avoir été utilisée pendant environ une semaine et avoir fait l’objet d’une activité cohérente au cours de cette semaine. SQL Database Advisor peut plus facilement optimiser les modèles de requête cohérents que les pics d’activité aléatoires.

Pour plus d’informations sur SQL Database Advisor, consultez la page [SQL Database Advisor](https://azure.microsoft.com/documentation/articles/sql-database-advisor/).

## <a name="improve-azure-cache-for-redis-performance-and-reliability"></a>Améliorer la fiabilité et les performances du Cache Azure pour Redis

Advisor identifie les instances de Cache Azure pour Redis où les performances peuvent être défavorablement affectées par une utilisation intensive de la mémoire, la charge du serveur, la bande passante réseau ou un grand nombre de connexions clientes. Il fournit également des recommandations quant aux meilleures pratiques pour vous éviter les problèmes potentiels. Pour plus d’informations sur les recommandations liées au Cache Azure pour Redis, consultez [Azure Cache for Redis Advisor](https://azure.microsoft.com/documentation/articles/cache-configure/#redis-cache-advisor).


## <a name="improve-app-service-performance-and-reliability"></a>Améliorer la fiabilité et les performances d’App Service

Le conseiller Azure intègre des recommandations quant aux meilleures pratiques pour améliorer votre expérience App Services et vous faire découvrir des fonctionnalités appropriées de la plateforme. Exemples de recommandations App Services :
* Détection des instances où les ressources de mémoire ou de processeur sont épuisées par des exécutions d’application avec options d’atténuation.
* Détection des instances où la colocalisation de ressources telles que les applications web et les bases de données peut améliorer les performances et réduire les coûts. 

Pour plus d’informations sur les recommandations App Services, consultez [Meilleures pratiques pour Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-best-practices/).

## <a name="remove-data-skew-on-your-sql-data-warehouse-table-to-increase-query-performance"></a>Supprimez l’asymétrie des données sur votre table d’entrepôt de données SQL pour augmenter les performances de requête

L’asymétrie des données peut provoquer des déplacement des données ou des goulots d’étranglement de ressource inutiles lors de l’exécution de votre charge de travail. Advisor va détecter l’asymétrie des données au-delà de 15 % et vous recommander de redistribuer vos données et de revisiter vos sélections de clé de distribution de table. Pour en savoir plus sur l’identification et la suppression d’une asymétrie, consultez [résolution des problèmes d’asymétrie](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-distribute#how-to-tell-if-your-distribution-column-is-a-good-choice).

## <a name="create-or-update-outdated-table-statistics-on-your-sql-data-warehouse-table-to-increase-query-performance"></a>Créer ou mettre à jour les statistiques de table obsolètes sur votre table d’entrepôt de données SQL pour augmenter les performances de requête

Advisor identifie les tables qui n’ont pas de [statistiques de table](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-statistics) à jour et recommande la création ou mise à jour des statistiques de table. L’optimiseur de requête d’entrepôt de données SQL utilise des statiques à jour pour estimer la cardinalité ou le nombre de lignes dans le résultat de requête qui permet à l’optimiseur de requête de créer un plan de requête de haute qualité pour de meilleures performances.

## <a name="migrate-your-storage-account-to-azure-resource-manager-to-get-all-of-the-latest-azure-features"></a>Migrer votre compte de stockage vers Azure Resource Manager pour obtenir toutes les dernières fonctionnalités Azure

Migrez le modèle de déploiement de votre compte de stockage vers Azure Resource Manager (ARM) pour tirer parti des déploiements de modèles, d’options de sécurité supplémentaires, et de la possibilité de mettre à niveau votre compte vers GPv2 pour bénéficier des dernières fonctionnalités de Stockage Azure. Advisor identifie les comptes de stockage autonomes utilisant le modèle de déploiement classique et recommande une migration vers le modèle de déploiement ARM. 

## <a name="how-to-access-performance-recommendations-in-advisor"></a>Comment accéder aux recommandations en matière de performances dans le conseiller

1. Connectez-vous au [portail Azure](https://portal.azure.com), puis ouvrez [Advisor](https://aka.ms/azureadvisordashboard).

2.  Dans le tableau de bord Advisor, cliquez sur l’onglet **Performances**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les recommandations d’Advisor, consultez les ressources suivantes :

* [Présentation du conseiller](advisor-overview.md)
* [Prise en main d’Advisor](advisor-get-started.md)
* [Recommandations du conseiller en matière de coûts](advisor-performance-recommendations.md)
* [Recommandations du conseiller en matière de haute disponibilité](advisor-high-availability-recommendations.md)
* [Recommandations du conseiller en matière de sécurité](advisor-security-recommendations.md)

