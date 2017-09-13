---
title: "適用於 Node.js 的 Azure 媒體服務模組"
description: "適用於 Node.js 的 Azure 媒體服務模組參考"
keywords: "Azure,SDK,API,媒體服務, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="7311a-104">適用於 Node.js 的 Azure 媒體服務模組</span><span class="sxs-lookup"><span data-stu-id="7311a-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7311a-105">概觀</span><span class="sxs-lookup"><span data-stu-id="7311a-105">Overview</span></span>

<span data-ttu-id="7311a-106">Azure 媒體服務是一個可延伸的雲端型平台，供開發人員建置可擴充的媒體管理和傳遞應用程式。</span><span class="sxs-lookup"><span data-stu-id="7311a-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="7311a-107">媒體服務是以 REST API 為基礎，可讓您安全地上傳、儲存、編碼和封裝視訊或音訊內容，以用於隨選和即時資料流傳遞給各種用戶端 (例如電視、電腦和行動裝置)。</span><span class="sxs-lookup"><span data-stu-id="7311a-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="7311a-108">使用 Azure 媒體服務，您可以：</span><span class="sxs-lookup"><span data-stu-id="7311a-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="7311a-109">建置完全採用媒體服務的端對端工作流程。</span><span class="sxs-lookup"><span data-stu-id="7311a-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="7311a-110">在工作流程的某些部分使用第三方元件。</span><span class="sxs-lookup"><span data-stu-id="7311a-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="7311a-111">例如，使用第三方編碼器來進行編碼；</span><span class="sxs-lookup"><span data-stu-id="7311a-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="7311a-112">然後使用媒體服務上傳、保護、封裝、傳遞。</span><span class="sxs-lookup"><span data-stu-id="7311a-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="7311a-113">即時串流您的內容或傳遞隨選內容。</span><span class="sxs-lookup"><span data-stu-id="7311a-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="7311a-114">本主題也會連結到其他相關主題。</span><span class="sxs-lookup"><span data-stu-id="7311a-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="7311a-115">管理套件</span><span class="sxs-lookup"><span data-stu-id="7311a-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7311a-116">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="7311a-116">Install the npm module</span></span>

<span data-ttu-id="7311a-117">安裝 Azure 媒體服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="7311a-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="7311a-118">範例</span><span class="sxs-lookup"><span data-stu-id="7311a-118">Example</span></span>

<span data-ttu-id="7311a-119">此範例會列出資源群組的所有媒體服務。</span><span class="sxs-lookup"><span data-stu-id="7311a-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="7311a-120">範例</span><span class="sxs-lookup"><span data-stu-id="7311a-120">Samples</span></span>

<span data-ttu-id="7311a-121">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="7311a-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
