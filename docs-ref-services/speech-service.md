---
title: 適用於 JavaScript 的認知服務語音 SDK
description: 適用於 JavaScript 的認知服務語音 SDK 參考
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49027432"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="43028-103">適用於 JavaScript 的認知服務語音 SDK</span><span class="sxs-lookup"><span data-stu-id="43028-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="43028-104">概觀</span><span class="sxs-lookup"><span data-stu-id="43028-104">Overview</span></span>

<span data-ttu-id="43028-105">為了讓支援語音的應用程式更易於開發，Microsoft 提供了可與[語音服務](https://aka.ms/csspeech)搭配使用的語音 SDK。</span><span class="sxs-lookup"><span data-stu-id="43028-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="43028-106">語音 SDK 提供具一致性的原生語音轉換文字和語音翻譯 API。</span><span class="sxs-lookup"><span data-stu-id="43028-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="43028-107">認知服務語音 SDK 目前僅適用於瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="43028-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="43028-108">不久後，NPM 套件也可使用此 SDK。</span><span class="sxs-lookup"><span data-stu-id="43028-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="43028-109">安裝語音 SDK</span><span class="sxs-lookup"><span data-stu-id="43028-109">Install the Speech SDK</span></span>

<span data-ttu-id="43028-110">下載語音 SDK 的 [.zip 套件](https://aka.ms/csspeech/jsbrowserpackage)並將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="43028-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="43028-111">這應該會將大量檔案解壓縮，包括名為 `microsoft.cognitiveservices.speech.sdk.bundle.js` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="43028-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="43028-112">將此檔案載入為您網頁中的指令碼資源以開始使用語音 SDK：</span><span class="sxs-lookup"><span data-stu-id="43028-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="43028-113">範例</span><span class="sxs-lookup"><span data-stu-id="43028-113">Example</span></span> 

<span data-ttu-id="43028-114">下列程式碼片段會示範如何從您的瀏覽器中執行簡單的語音辨識：</span><span class="sxs-lookup"><span data-stu-id="43028-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="43028-115">請查看我們的[逐步快速入門](/azure/cognitive-services/speech-service/quickstart-js-browser)。</span><span class="sxs-lookup"><span data-stu-id="43028-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="43028-116">範例</span><span class="sxs-lookup"><span data-stu-id="43028-116">Samples</span></span>

<span data-ttu-id="43028-117">在我們的[語音 SDK 範例存放庫](https://aka.ms/csspeech/samples)中探索更多範例。</span><span class="sxs-lookup"><span data-stu-id="43028-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
