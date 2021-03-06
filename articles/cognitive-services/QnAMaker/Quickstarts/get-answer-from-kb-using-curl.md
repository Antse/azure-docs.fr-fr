---
title: 'Démarrage rapide : Utiliser cURL pour obtenir une réponse d’une base de connaissances - QnA Maker'
titleSuffix: Azure Cognitive Services
description: Ce démarrage rapide vous aide à obtenir une réponse de votre base de connaissances en utilisant cURL.
services: cognitive-services
author: diberry
manager: cgronlun
ms.service: cognitive-services
ms.component: qna-maker
ms.topic: article
ms.date: 12/04/2018
ms.author: diberry
ms.openlocfilehash: 0cbd25c0ea906c0b0f35b6ac0ae798505863ac8a
ms.sourcegitcommit: 7fd404885ecab8ed0c942d81cb889f69ed69a146
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53273253"
---
# <a name="quickstart-get-answer-from-knowledge-base-using-curl"></a>Démarrage rapide : Obtenir une réponse d’une base de connaissances en utilisant cURL

Ce démarrage rapide basé sur cURL vous montre pas à pas comment obtenir une réponse de votre base de connaissances.

## <a name="prerequisites"></a>Prérequis

* Dernière version de [**cURL**](https://curl.haxx.se/).
* Vous devez disposer d’un [service QnA Maker](../How-To/set-up-qnamaker-service-azure.md) et d’une [base de connaissances avec des questions et des réponses](../Tutorials/create-publish-query-in-portal.md).

## <a name="publish-to-get-endpoint"></a>Publier pour obtenir un point de terminaison

Quand vous êtes prêt à générer une réponse à une question à partir de votre base de connaissances, [publiez](../How-to/publish-knowledge-base.md) votre base de connaissances.

## <a name="use-production-endpoint-with-curl"></a>Utiliser un point de terminaison de production cURL

Une fois votre base de connaissances publiée, la page **Publier** affiche les paramètres de requête HTTP pour générer une réponse. L’onglet **CURL** affiche les paramètres nécessaires à la génération d’une réponse à partir de l’outil de ligne de commande, [CURL](https://www.getpostman.com).

[![Publier les résultats](../media/qnamaker-use-to-generate-answer/curl-command-on-publish-page.png)](../media/qnamaker-use-to-generate-answer/curl-command-on-publish-page.png#lightbox)

Pour générer une réponse avec CURL, effectuez les étapes suivantes :

1. Copiez le texte sous l’onglet CURL. 
1. Ouvrez une ligne de commande ou un terminal et collez le texte.
1. Rectifiez la question pour la rendre pertinente par rapport à base de connaissances. Veillez à ne pas supprimer le JSON contenant la question.
1. Entrez la commande. 
1. La réponse comprend les informations pertinentes. 

    ```bash
    > curl -X POST https://qnamaker-f0.azurewebsites.net/qnamaker/knowledgebases/1111f8c-d01b-4698-a2de-85b0dbf3358c/generateAnswer -H "Authorization: EndpointKey 111841fb-c208-4a72-9412-03b6f3e55ca1" -H "Content-type: application/json" -d "{'question':'How do I programmatically update my Knowledge Base?'}"
    {
      "answers": [
        {
          "questions": [
            "How do I programmatically update my Knowledge Base?"
          ],
          "answer": "You can use our REST APIs to manage your Knowledge Base. See here for details: https://westus.dev.cognitive.microsoft.com/docs/services/5a93fcf85b4ccd136866eb37/operations/5ac266295b4ccd1554da7600",
          "score": 100.0,
          "id": 18,
          "source": "Custom Editorial",
          "metadata": [
            {
              "name": "category",
              "value": "api"
            }
          ]
        }
      ]
    }
    ```

## <a name="use-staging-endpoint-with-curl"></a>Utiliser le point de terminaison de mise en lots avec cURL

Si vous souhaitez obtenir une réponse du point de terminaison de mise en lots, utilisez le paramètre booléen querystring `isTest` avec la valeur `true`.

`isTest=true`

## <a name="next-steps"></a>Étapes suivantes

La page de publication fournit aussi des informations pour [générer une réponse](get-answer-from-kb-using-postman.md) avec Postman. 

> [!div class="nextstepaction"]
> [Utiliser des métadonnées pendant la génération d’une réponse](../How-to/metadata-generateanswer-usage.md)