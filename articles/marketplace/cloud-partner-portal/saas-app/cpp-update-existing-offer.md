---
title: Mettre à jour une offre d’application Azure SaaS existante | Microsoft Docs
description: Comment mettre à jour une offre d’application SaaS existante sur la place de marché Azure.
services: Azure, Marketplace, Cloud Partner Portal,
documentationcenter: ''
author: dan-wesley
manager: Patrick.Butler
editor: ''
ms.assetid: ''
ms.service: marketplace
ms.workload: ''
ms.tgt_pltfrm: ''
ms.devlang: ''
ms.topic: conceptual
ms.date: 12/04/2018
ms.author: pbutlerm
ms.openlocfilehash: 9d490a0ec09e351e4cee00e7c30c9161bdfac3e6
ms.sourcegitcommit: 5b869779fb99d51c1c288bc7122429a3d22a0363
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53196175"
---
# <a name="update-an-existing-saas-application-offer"></a>Mettre à jour une offre d’application SaaS existante

Différents types de mises à jour peuvent s’appliquer à votre offre à l’issue de la publication et de la mise en ligne de celle-ci. Toute modification apportée à la nouvelle version de votre offre doit être enregistrée et republiée pour apparaître sur la Place de marché. Cet article explique en détail comment mettre à jour une offre SaaS sur le [Portail Cloud Partner](https://cloudpartner.azure.com/).

Vous pouvez mettre à jour votre offre pour plusieurs raisons, par exemple :

- Ajouter une nouvelle version à une application existante.
- Mise à jour d’une application.
- Ajout de nouvelles fonctionnalités à une application.
- Mise à jour des métadonnées de la Place de marché pour l’offre.

Le portail propose les fonctions **Comparer** et **Historique** pour faciliter ces modifications.

## <a name="unpermitted-changes-to-a-saas-offer"></a>Modifications non autorisées apportées à l’offre SaaS

Certains attributs d’une offre SaaS ne sont plus modifiables une fois l’offre publiée sur la Place de marché Azure. Vous ne pouvez pas modifier les paramètres suivants :

- ID d’offre et ID de l’éditeur de l’offre
- Balises de version, par exemple : `1.0.1`
- Modifications du modèle de facturation/licence apportées à des offres existantes.

## <a name="common-update-operations"></a>Opérations de mise à jour courantes
 
Les opérations de mise à jour suivantes sont courantes.

### <a name="update-offer-contacts"></a>Mettre à jour les contacts de l’offre

Suivez les étapes ci-dessous pour mettre à jour les contacts de support de votre offre.

1. Connectez-vous au [Portail Cloud Partner](https://cloudpartner.azure.com/).
2. Sous **Toutes les offres**, recherchez l’offre que vous souhaitez mettre à jour.
3. Accédez à l’onglet **Contacts**. Mettez à jour vos contacts.
4. Cliquez sur **Publier** pour démarrer le flux de travail et publier vos modifications.


### <a name="update-offer-marketplace-metadata"></a>Mettre à jour les métadonnées de Place de marché d’une offre

Pour mettre à jour les métadonnées de Place de marché associées à votre offre, procédez comme suit. (par exemple : nom de l’entreprise, logos, etc.)

1. Connectez-vous au [Portail Cloud Partner](https://cloudpartner.azure.com/).
2. Sous **Toutes les offres**, recherchez l’offre que vous souhaitez mettre à jour.
3. Accédez à l’onglet des **informations sur les vitrines**. Suivez les instructions de l’article [Publier une offre SaaS](./cpp-publish-offer.md) pour apporter des modifications aux métadonnées.
4. Cliquez sur **Publier** pour démarrer le flux de travail et publier vos modifications.

## <a name="compare-feature"></a>Fonctionnalité Comparer

Lorsque vous apportez des modifications à une offre publiée, vous pouvez utiliser la fonctionnalité Comparer pour les vérifier. La capture d’écran suivante montre l’option Comparer d’une offre publiée.

![Utiliser l’option Comparer pour afficher les modifications apportées à l’offre dans le Portail Cloud Partner](./media/saas-offer-compare.png)

### <a name="to-use-the-compare-feature"></a>Pour utiliser la fonctionnalité Comparer :

1. Au cours du processus de modification, sélectionnez Comparer pour votre offre.
2. Affichez côte à côte les versions des ressources marketing et des métadonnées.

## <a name="publishing-history"></a>Historique de publication

Pour afficher tout l’historique des activités de publication, cliquez sur l’onglet **Historique** dans la barre du menu de navigation sur le côté gauche du Portail Cloud Partner. Vous pouvez consulter ici les actions horodatées effectuées pendant la durée de vie de vos offres sur la Place de marché Microsoft Azure.

![Voir l’historique des offres dans le Portail Cloud Partner](./media/saas-offer-history.png)

Vous pouvez utiliser la page d’historique des audits pour rechercher une offre spécifique et appliquer des filtres tels que Serveur de publication, Offre et Type d’événement (par exemple, OfferGoLiveRequested.) Vous pouvez également télécharger l’historique des audits dans un fichier csv.


## <a name="next-steps"></a>Étapes suivantes

[Offre d’application SaaS](./cpp-saas-offer.md)