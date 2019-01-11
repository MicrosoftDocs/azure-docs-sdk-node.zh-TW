---
title: 適用於 JavaScript 的認知服務語音 SDK
description: 適用於 JavaScript 的認知服務語音 SDK 參考
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185985"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="cdfb8-103">適用於 JavaScript 的認知服務語音 SDK</span><span class="sxs-lookup"><span data-stu-id="cdfb8-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="cdfb8-104">概觀</span><span class="sxs-lookup"><span data-stu-id="cdfb8-104">Overview</span></span>

<span data-ttu-id="cdfb8-105">為了讓支援語音的應用程式更易於開發，Microsoft 提供了可與[語音服務](https://aka.ms/csspeech)搭配使用的語音 SDK。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="cdfb8-106">語音 SDK 提供具一致性的原生語音轉換文字和語音翻譯 API。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cdfb8-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="cdfb8-107">Install the npm module</span></span>

<span data-ttu-id="cdfb8-108">安裝認知服務語音 SDK 的 npm 模組</span><span class="sxs-lookup"><span data-stu-id="cdfb8-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="cdfb8-109">範例</span><span class="sxs-lookup"><span data-stu-id="cdfb8-109">Example</span></span> 

<span data-ttu-id="cdfb8-110">下列程式碼片段會示範如何從檔案中執行簡單的語音辨識：</span><span class="sxs-lookup"><span data-stu-id="cdfb8-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="cdfb8-111">請查看我們的[逐步快速入門](/azure/cognitive-services/speech-service/quickstart-js-node)。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="cdfb8-112">範例</span><span class="sxs-lookup"><span data-stu-id="cdfb8-112">Samples</span></span>

* <span data-ttu-id="cdfb8-113">[Node.js 逐步快速入門](/azure/cognitive-services/speech-service/quickstart-js-node)。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="cdfb8-114">[瀏覽器逐步快速入門](/azure/cognitive-services/speech-service/quickstart-js-browser)。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="cdfb8-115">您可以在我們的[語音 SDK 範例存放庫](https://aka.ms/csspeech/samples)中找到更多範例。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
