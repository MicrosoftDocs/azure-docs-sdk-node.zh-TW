---
title: "適用於 Node.js 的 Azure 媒體服務模組"
description: "適用於 Node.js 的 Azure 媒體服務模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 77a6716d4ef0d566690325a86e85d66c5ac234d6
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="9291f-103">適用於 Node.js 的 Azure 媒體服務模組</span><span class="sxs-lookup"><span data-stu-id="9291f-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="9291f-104">Azure 媒體服務是一個可延伸的雲端型平台，供開發人員建置可擴充的媒體管理和傳遞應用程式。</span><span class="sxs-lookup"><span data-stu-id="9291f-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="9291f-105">媒體服務是以 REST API 為基礎，可讓您安全地上傳、儲存、編碼和封裝視訊或音訊內容，以用於隨選和即時資料流傳遞給各種用戶端 (例如電視、電腦和行動裝置)。</span><span class="sxs-lookup"><span data-stu-id="9291f-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="9291f-106">使用 Azure 媒體服務，您可以：</span><span class="sxs-lookup"><span data-stu-id="9291f-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="9291f-107">建置完全採用媒體服務的端對端工作流程。</span><span class="sxs-lookup"><span data-stu-id="9291f-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="9291f-108">在工作流程的某些部分使用第三方元件。</span><span class="sxs-lookup"><span data-stu-id="9291f-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="9291f-109">例如，使用第三方編碼器來進行編碼；</span><span class="sxs-lookup"><span data-stu-id="9291f-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="9291f-110">然後使用媒體服務上傳、保護、封裝、傳遞。</span><span class="sxs-lookup"><span data-stu-id="9291f-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="9291f-111">即時串流您的內容或傳遞隨選內容。</span><span class="sxs-lookup"><span data-stu-id="9291f-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="9291f-112">本主題也會連結到其他相關主題。</span><span class="sxs-lookup"><span data-stu-id="9291f-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="9291f-113">管理套件</span><span class="sxs-lookup"><span data-stu-id="9291f-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9291f-114">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="9291f-114">Install the npm module</span></span>

<span data-ttu-id="9291f-115">安裝 Azure 媒體服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="9291f-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="9291f-116">範例</span><span class="sxs-lookup"><span data-stu-id="9291f-116">Example</span></span>

<span data-ttu-id="9291f-117">此範例會列出資源群組的所有媒體服務。</span><span class="sxs-lookup"><span data-stu-id="9291f-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9291f-118">範例</span><span class="sxs-lookup"><span data-stu-id="9291f-118">Samples</span></span>

<span data-ttu-id="9291f-119">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9291f-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
