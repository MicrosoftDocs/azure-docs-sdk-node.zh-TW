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
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51471582"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="426a5-103">JavaScript Azure 認知服務模組</span><span class="sxs-lookup"><span data-stu-id="426a5-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="426a5-104">願景視覺</span><span class="sxs-lookup"><span data-stu-id="426a5-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="426a5-105">電腦視覺</span><span class="sxs-lookup"><span data-stu-id="426a5-105">Computer Vision</span></span> 

<span data-ttu-id="426a5-106">傳回在影像中找到的視覺化內容資訊：</span><span class="sxs-lookup"><span data-stu-id="426a5-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="426a5-107">使用標籤、描述及網域特定模型，自信從容地識別內容並加上標籤。</span><span class="sxs-lookup"><span data-stu-id="426a5-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="426a5-108">套用成人/猥瑣設定，以啟用自動限制成人內容。</span><span class="sxs-lookup"><span data-stu-id="426a5-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="426a5-109">識別圖片中的影像類型及色彩配置。</span><span class="sxs-lookup"><span data-stu-id="426a5-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="426a5-110">在您的瀏覽器中免費[試用電腦視覺](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="426a5-111">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="426a5-112">[進一步了解](/azure/cognitive-services/computer-vision/home)電腦視覺 API 相關資訊，並參考[電腦視覺 API JavaScript 快速入門](/azure/cognitive-services/computer-vision/quickstarts/javascript)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="426a5-113">內容仲裁</span><span class="sxs-lookup"><span data-stu-id="426a5-113">Content Moderator</span></span>

<span data-ttu-id="426a5-114">由機器協助進行文字、影片及影像審核，並透過人工審核工具加強。</span><span class="sxs-lookup"><span data-stu-id="426a5-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="426a5-115">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="426a5-116">[深入了解 ](/azure/cognitive-services/content-moderator/overview)Content Moderator API。</span><span class="sxs-lookup"><span data-stu-id="426a5-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="426a5-117">人臉識別 API</span><span class="sxs-lookup"><span data-stu-id="426a5-117">Face API</span></span>

<span data-ttu-id="426a5-118">偵測、識別、分析、組織和標記相片中的臉孔。</span><span class="sxs-lookup"><span data-stu-id="426a5-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="426a5-119">在瀏覽器中[試用臉部 API](https://azure.microsoft.com/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="426a5-120">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="426a5-121">[進一步了解](/azure/cognitive-services/face/overview)臉部 API，並參考[臉部 API JavaScript 快速入門](/azure/cognitive-services/Face/quickstarts/javascript)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="426a5-122">搜尋模組</span><span class="sxs-lookup"><span data-stu-id="426a5-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="426a5-123">Web 搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-123">Web search</span></span>

<span data-ttu-id="426a5-124">擷取由 Bing 網路搜尋 API 編製索引的網路文件，並透過結果類型、新鮮度等等，縮小結果範圍。</span><span class="sxs-lookup"><span data-stu-id="426a5-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="426a5-125">在瀏覽器中[試用 Web 搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="426a5-126">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="426a5-127">[進一步了解 ](/azure/cognitive-services/bing-web-search/overview)Bing Web 搜尋 API，並參考 [Web 搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="426a5-128">影像搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-128">Image search</span></span>

<span data-ttu-id="426a5-129">搜尋影像並在結果中取得縮圖、完整的影像 URL、影像中繼資料等資訊。</span><span class="sxs-lookup"><span data-stu-id="426a5-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="426a5-130">在瀏覽器中[試用影像搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="426a5-131">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="426a5-132">[進一步了解 ](/azure/cognitive-services/bing-image-search/overview)Bing 影像搜尋 API，並參考[影像搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="426a5-133">實體搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-133">Entity search</span></span>

<span data-ttu-id="426a5-134">針對給定的搜尋字詞或位置，搜尋最相關的實體 (位置、個人或事物) 動作。</span><span class="sxs-lookup"><span data-stu-id="426a5-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="426a5-135">在瀏覽器中[試用實體搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="426a5-136">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="426a5-137">[進一步了解 ](/azure/cognitive-services/bing-entities-search/search-the-web)Bing 實體搜尋 API，並參考[實體搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="426a5-138">自訂搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-138">Custom search</span></span>

<span data-ttu-id="426a5-139">建置符合特定搜尋範圍的自訂 Web 搜尋。</span><span class="sxs-lookup"><span data-stu-id="426a5-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="426a5-140">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="426a5-141">[進一步了解 ](/azure/cognitive-services/bing-custom-search/)Bing 自訂搜尋服務，並參考[自訂搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)從應用程式查詢您的自訂搜尋。</span><span class="sxs-lookup"><span data-stu-id="426a5-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="426a5-142">影片搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-142">Video search</span></span>

<span data-ttu-id="426a5-143">在網路上尋找影片，並取得建立者、編碼、長度和檢視計數中繼資料等結果。</span><span class="sxs-lookup"><span data-stu-id="426a5-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="426a5-144">在瀏覽器中[試用影片搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="426a5-145">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="426a5-146">[進一步了解 ](/azure/cognitive-services/bing-video-search/search-the-web)Bing 影片搜尋服務，並參考[影片搜尋 API Node.js 快速入門](/azure/cognitive-services/bing-video-search/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="426a5-147">新聞搜尋</span><span class="sxs-lookup"><span data-stu-id="426a5-147">News search</span></span>

<span data-ttu-id="426a5-148">搜尋網站上的新聞文章，並與文章、相關的新聞、影像和提供者資訊中繼資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="426a5-149">在瀏覽器中[試用新聞搜尋 API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="426a5-150">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="426a5-151">[進一步了解 ](/azure/cognitive-services/bing-news-search/search-the-web)Bing 新聞搜尋服務，並參考[新聞搜尋 API JavaScript 快速入門](/azure/cognitive-services/bing-news-search/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="426a5-152">語言模組</span><span class="sxs-lookup"><span data-stu-id="426a5-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="426a5-153">文字分析</span><span class="sxs-lookup"><span data-stu-id="426a5-153">Text Analytics</span></span> 

<span data-ttu-id="426a5-154">文字分析 API 是雲端式服務，對未經處理的文字提供自然語言處理。</span><span class="sxs-lookup"><span data-stu-id="426a5-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="426a5-155">此 API 包含三項主要功能：</span><span class="sxs-lookup"><span data-stu-id="426a5-155">The API includes three main functions:</span></span>

- <span data-ttu-id="426a5-156">情感分析</span><span class="sxs-lookup"><span data-stu-id="426a5-156">Sentiment analysis</span></span>
- <span data-ttu-id="426a5-157">關鍵片語擷取</span><span class="sxs-lookup"><span data-stu-id="426a5-157">Key phrase extraction</span></span>
- <span data-ttu-id="426a5-158">語言偵測</span><span class="sxs-lookup"><span data-stu-id="426a5-158">Language detection</span></span>

<span data-ttu-id="426a5-159">在瀏覽器中[試用文字分析 API](https://azure.microsoft.com/services/cognitive-services/text-analytics/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="426a5-160">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="426a5-161">[進一步了解](/azure/cognitive-services/text-analytics/overview)文字分析 API，並參考[文字分析 API Node.js 快速入門](/azure/cognitive-services/text-analytics/quickstarts/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="426a5-162">拼字檢查</span><span class="sxs-lookup"><span data-stu-id="426a5-162">Spell Check</span></span>

<span data-ttu-id="426a5-163">透過 Bing 拼字檢查 API 執行內容相關的文法與拼字檢查。</span><span class="sxs-lookup"><span data-stu-id="426a5-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="426a5-164">在瀏覽器中[試用拼字檢查 API](https://azure.microsoft.com/services/cognitive-services/spell-check/)。</span><span class="sxs-lookup"><span data-stu-id="426a5-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="426a5-165">使用 [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) 取得 JavaScript 模組：</span><span class="sxs-lookup"><span data-stu-id="426a5-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="426a5-166">[進一步了解](/azure/cognitive-services/bing-spell-check/proof-text)拼字檢查 API，並參考[拼字檢查 API Node.js 快速入門](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)開始使用。</span><span class="sxs-lookup"><span data-stu-id="426a5-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="426a5-167">範例</span><span class="sxs-lookup"><span data-stu-id="426a5-167">Samples</span></span>

<span data-ttu-id="426a5-168">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="426a5-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
