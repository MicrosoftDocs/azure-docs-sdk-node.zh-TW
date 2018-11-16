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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51487902"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>適用於 JavaScript 的認知服務語音 SDK

## <a name="overview"></a>概觀

為了讓支援語音的應用程式更易於開發，Microsoft 提供了可與[語音服務](https://aka.ms/csspeech)搭配使用的語音 SDK。
語音 SDK 提供具一致性的原生語音轉換文字和語音翻譯 API。

> [!NOTE]
> 認知服務語音 SDK 目前僅適用於瀏覽器。
> 不久後，NPM 套件也可使用此 SDK。

### <a name="install-the-speech-sdk"></a>安裝語音 SDK

下載語音 SDK 的 [.zip 套件](https://aka.ms/csspeech/jsbrowserpackage)並將它解壓縮。
這應該會將大量檔案解壓縮，包括名為 `microsoft.cognitiveservices.speech.sdk.bundle.js` 的檔案。
將此檔案載入為您網頁中的指令碼資源以開始使用語音 SDK：

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>範例 

下列程式碼片段會示範如何從您的瀏覽器中執行簡單的語音辨識：

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

請查看我們的[逐步快速入門](/azure/cognitive-services/speech-service/quickstart-js-browser)。

## <a name="samples"></a>範例

在我們的[語音 SDK 範例存放庫](https://aka.ms/csspeech/samples)中探索更多範例。
