---
title: Effectuer une reconnaissance vocale à l’aide du kit de développement logiciel (SDK) Speech pour Java
titleSuffix: Azure Cognitive Services
description: Découvrez comment effectuer une reconnaissance vocale (à partir d’un fichier, à partir d’un micro, avec un modèle personnalisé, en continu ou en une seule fois) à l’aide du kit SDK Speech pour Java.
services: cognitive-services
author: wolfma61
manager: cgronlun
ms.service: cognitive-services
ms.component: speech-service
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: wolfma
ms.openlocfilehash: 0accd353f0079e5e9da80e3aab8eb542aaa21edd
ms.sourcegitcommit: 62759a225d8fe1872b60ab0441d1c7ac809f9102
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49468317"
---
# <a name="recognize-speech-by-using-the-speech-sdk-for-java"></a>Effectuer une reconnaissance vocale à l’aide du kit de développement logiciel (SDK) Speech pour Java

[!INCLUDE [Selector](../../../includes/cognitive-services-speech-service-how-to-recognize-speech-selector.md)]

[!INCLUDE [Introduction](../../../includes/cognitive-services-speech-service-how-to-recognize-speech-intro.md)]

[!INCLUDE [Introduction for top-level declarations](../../../includes/cognitive-services-speech-service-how-to-toplevel-declarations.md)]

[!code-java[Top-level declarations](~/samples-cognitive-services-speech-sdk/samples/java/jre/console/src/com/microsoft/cognitiveservices/speech/samples/console/SpeechRecognitionSamples.java#toplevel)]

[!INCLUDE [Introduction to using a microphone](../../../includes/cognitive-services-speech-service-how-to-recognize-speech-microphone.md)]

[!code-java[Speech recognition by using a microphone](~/samples-cognitive-services-speech-sdk/samples/java/jre/console/src/com/microsoft/cognitiveservices/speech/samples/console/SpeechRecognitionSamples.java#recognitionWithMicrophone)]

[!INCLUDE [Introduction to using customized recognition](../../../includes/cognitive-services-speech-service-how-to-recognize-speech-customized.md)]

[!code-java[Speech recognition by using a customized model](~/samples-cognitive-services-speech-sdk/samples/java/jre/console/src/com/microsoft/cognitiveservices/speech/samples/console/SpeechRecognitionSamples.java#recognitionCustomized)]

[!INCLUDE [Introduction to using a continuous file](../../../includes/cognitive-services-speech-service-how-to-recognize-speech-continuous.md)]

[!code-java[Continuous speech recognition](~/samples-cognitive-services-speech-sdk/samples/java/jre/console/src/com/microsoft/cognitiveservices/speech/samples/console/SpeechRecognitionSamples.java#recognitionContinuousWithFile)]

[!INCLUDE [Download the sample](../../../includes/cognitive-services-speech-service-speech-sdk-sample-download-h2.md)]
Recherchez le code utilisé dans cet article au sein du dossier samples/java/jre/console.

## <a name="next-steps"></a>Étapes suivantes

- [Comment reconnaître les intentions vocales](how-to-recognize-intents-from-speech-java.md)
- [Comment traduire une entrée vocale](how-to-translate-speech-java.md)

