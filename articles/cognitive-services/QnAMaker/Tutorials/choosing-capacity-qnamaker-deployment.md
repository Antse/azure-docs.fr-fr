---
title: Capacité de ressources pour un déploiement - QnA Maker
titleSuffix: Azure Cognitive Services
description: Avant de créer votre service QnA Maker, vous devez décider quel niveau des services ci-dessus vous convient.
services: cognitive-services
author: tulasim88
manager: cgronlun
ms.service: cognitive-services
ms.component: qna-maker
ms.topic: article
ms.date: 09/12/2018
ms.author: tulasim
ms.custom: seodec18
ms.openlocfilehash: 9e197929ce08f4e0c665f96d1c4ddbd382fdfb22
ms.sourcegitcommit: 9fb6f44dbdaf9002ac4f411781bf1bd25c191e26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53084451"
---
# <a name="choosing-capacity-for-your-qna-maker-deployment"></a>Choisir la capacité de votre déploiement QnA Maker

Le service QnA Maker prend une dépendance sur trois ressources Azure :
1.  App Service (pour l’exécution)
2.  Recherche Azure (pour le stockage des QnA)
3.  App Insights (facultatif, pour le stockage des journaux de conversation et les données de télémétrie)

Avant de créer votre service QnA Maker, vous devez décider quel niveau des services ci-dessus vous convient. 

En général, il existe trois paramètres dont vous devez tenir compte :
1. **Débit dont vous avez besoin à partir du service** : sélectionnez le [plan App Service](https://azure.microsoft.com/pricing/details/app-service/plans/) approprié en fonction de vos besoins. Vous pouvez faire [monter en puissance](https://docs.microsoft.com/azure/app-service/web-sites-scale) ou faire descendre en puissance l’application. Ceci doit également influencer votre sélection de la référence SKU de la Recherche Azure. Consultez plus d’informations [ici](https://docs.microsoft.com/azure/search/search-sku-tier).

2. **Taille et nombre de bases de connaissances** : Choisissez la [référence SKU Recherche Azure](https://azure.microsoft.com/pricing/details/search/) adaptée à votre scénario. Vous pouvez publier N-1 bases de connaissances dans un niveau spécifique, où N correspond au nombre maximal d’index autorisé dans le niveau. Vérifiez également la taille maximale et le nombre de documents autorisés par niveau.

3. **Nombre de documents comme sources** : la référence SKU gratuite du service de gestion QnA Maker limite à 3 le nombre de documents (d’une taille de 1 Mo chacun) que vous pouvez gérer via le portail et les API. La référence SKU Standard n’a aucune limite en termes de nombre de documents que vous pouvez gérer. Vous trouverez plus de détails [ici](https://aka.ms/qnamaker-pricing).

Le tableau suivant vous donne des indications d’ordre général.

|                        | Administration de QnA Maker | App Service | Recherche Azure | Limites                      |
| ---------------------- | -------------------- | ----------- | ------------ | -------------------------------- |
| Expérimentation        | Référence SKU Gratuite             | Niveau Gratuit   | Niveau Gratuit    | Publier jusqu’à 2 Ko, taille de 50 Mo  |
| Environnement de test/développement   | Référence SKU standard         | Partagé      | De base        | Publier jusqu’à 14 Ko, taille de 2 Go    |
| Environnement de production | Référence SKU standard         | De base       | standard     | Publier jusqu’à 49 Ko, taille de 25 Go |

Pour mettre à niveau votre pile QnA Maker, consultez [Mettre à niveau votre service QnA Maker](../How-To/upgrade-qnamaker-service.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Mettre à niveau votre service QnA Maker](../How-To/upgrade-qnamaker-service.md)
