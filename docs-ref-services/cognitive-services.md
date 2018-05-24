---
title: 適用於 Node.js 的 Azure 認知服務模組
description: 適用於 Node.js 的 Azure 認知服務模組參考
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fd0870f4b38928c23145a50d4c71456b4c94c3e9
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="javascript-azure-cognitive-services-modules"></a>JavaScript Azure 認知服務模組

## <a name="vision-modules"></a>願景視覺

### <a name="computer-vision"></a>電腦視覺 

傳回在影像中找到的視覺化內容資訊：

- 使用標籤、描述及網域特定模型，自信從容地識別內容並加上標籤。
- 套用成人/猥瑣設定，以啟用自動限制成人內容。
- 識別圖片中的影像類型及色彩配置。

在您的瀏覽器中免費[試用電腦視覺](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-computervision
```

[進一步了解](/azure/cognitive-services/computer-vision/home)電腦視覺 API 相關資訊，並參考[電腦視覺 API JavaScript 快速入門](/azure/cognitive-services/computer-vision/quickstarts/javascript)開始使用。

### <a name="content-moderator"></a>內容仲裁

由機器協助進行文字、影片及影像審核，並透過人工審核工具加強。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-contentmoderator
```

[深入了解 ](/azure/cognitive-services/content-moderator/overview)Content Moderator API。

### <a name="face-api"></a>人臉識別 API

偵測、識別、分析、組織和標記相片中的臉孔。 

在瀏覽器中[試用臉部 API](https://azure.microsoft.com/en-us/services/cognitive-services/face/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-face
```

[進一步了解](/azure/cognitive-services/face/overview)臉部 API，並參考[臉部 API JavaScript 快速入門](/azure/cognitive-services/Face/quickstarts/javascript)開始使用。

## <a name="search-modules"></a>搜尋模組

### <a name="web-search"></a>Web 搜尋

擷取由 Bing 網路搜尋 API 編製索引的網路文件，並透過結果類型、新鮮度等等，縮小結果範圍。 

在瀏覽器中[試用 Web 搜尋 API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-websearch
```

[進一步了解 ](/azure/cognitive-services/bing-web-search/overview)Bing Web 搜尋 API，並參考 [Web 搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)開始使用。

### <a name="image-search"></a>影像搜尋

搜尋影像並在結果中取得縮圖、完整的影像 URL、影像中繼資料等資訊。

在瀏覽器中[試用影像搜尋 API](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-imagesearch
```

[進一步了解 ](/azure/cognitive-services/bing-image-search/overview)Bing 影像搜尋 API，並參考[影像搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)開始使用。


### <a name="entity-search"></a>實體搜尋

針對給定的搜尋字詞或位置，搜尋最相關的實體 (位置、個人或事物) 動作。

在瀏覽器中[試用實體搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-entitysearch
```

[進一步了解 ](/azure/cognitive-services/bing-entities-search/search-the-web)Bing 實體搜尋 API，並參考[實體搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)開始使用。

### <a name="custom-search"></a>自訂搜尋

建置符合特定搜尋範圍的自訂 Web 搜尋。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-customsearch
```

[進一步了解 ](/azure/cognitive-services/bing-custom-search/)Bing 自訂搜尋服務，並參考[自訂搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)從應用程式查詢您的自訂搜尋。

### <a name="video-search"></a>影片搜尋

在網路上尋找影片，並取得建立者、編碼、長度和檢視計數中繼資料等結果。

在瀏覽器中[試用影片搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-videosearch
```

[進一步了解 ](/azure/cognitive-services/bing-video-search/search-the-web)Bing 影片搜尋服務，並參考[影片搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-video-search/nodejs)開始使用。


### <a name="news-search"></a>新聞搜尋

搜尋網站上的新聞文章，並與文章、相關的新聞、影像和提供者資訊中繼資料搭配使用。

在瀏覽器中[試用新聞搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-newssearch
```

[進一步了解 ](/azure/cognitive-services/bing-news-search/search-the-web)Bing 新聞搜尋服務，並參考[新聞搜尋 API JavaScript 快速入門](/azure/cognitive-services/bing-news-search/nodejs)開始使用。


## <a name="language-modules"></a>語言模組

### <a name="text-analytics"></a>文字分析 

文字分析 API 是雲端式服務，對未經處理的文字提供自然語言處理。 此 API 包含三項主要功能：

- 情感分析
- 關鍵片語擷取
- 語言偵測

在瀏覽器中[試用文字分析 API](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-textanalytics
```

[進一步了解](/azure/cognitive-services/text-analytics/overview)文字分析 API，並參考[文字分析 API Node.js 快速入門](/azure/cognitive-services/text-analytics/quickstarts/nodejs)開始使用。


### <a name="spell-check"></a>拼字檢查

透過 Bing 拼字檢查 API 執行內容相關的文法與拼字檢查。

在瀏覽器中[試用拼字檢查 API](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/)。

使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：

```
npm install azure-cognitiveservices-spellcheck
```

[進一步了解](/azure/cognitive-services/bing-spell-check/proof-text)拼字檢查 API，並參考[拼字檢查 API Node.js 快速入門](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)開始使用。

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
