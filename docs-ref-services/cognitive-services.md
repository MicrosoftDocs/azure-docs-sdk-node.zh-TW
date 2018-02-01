---
title: "適用於 Node.js 的 Azure 認知服務模組"
description: "適用於 Node.js 的 Azure 認知服務模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="31e0a-103">適用於 Node.js 的 Azure 認知服務模組</span><span class="sxs-lookup"><span data-stu-id="31e0a-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="31e0a-104">Microsoft 認知服務是一組可供開發人員使用的 API、SDK 和服務，可讓其應用程式更具智能、吸引力且更容易探索。</span><span class="sxs-lookup"><span data-stu-id="31e0a-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="31e0a-105">Microsoft 認知服務詳述 Microsoft 不斷演變的機器學習 API 發展產品組合，可讓開發人員輕鬆地將智慧型功能 (例如情緒和影片偵測；臉部、語音和視覺辨識；以及語音和語言理解) 新增至其應用程式。</span><span class="sxs-lookup"><span data-stu-id="31e0a-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="31e0a-106">我們的願景是在可逐漸看到、聽到、說出和理解，甚至開始推理之系統的輔助之下，提供更多個人運算體驗並提升生產力。</span><span class="sxs-lookup"><span data-stu-id="31e0a-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="31e0a-107">管理套件</span><span class="sxs-lookup"><span data-stu-id="31e0a-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="31e0a-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="31e0a-108">Install the npm module</span></span>

<span data-ttu-id="31e0a-109">安裝 Azure 認知服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="31e0a-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="31e0a-110">範例</span><span class="sxs-lookup"><span data-stu-id="31e0a-110">Example</span></span>

<span data-ttu-id="31e0a-111">此範例會列出所有的辨識服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="31e0a-111">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="31e0a-112">範例</span><span class="sxs-lookup"><span data-stu-id="31e0a-112">Samples</span></span>

<span data-ttu-id="31e0a-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="31e0a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
