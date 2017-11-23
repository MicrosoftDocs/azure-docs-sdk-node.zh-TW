---
title: "適用於 Node.js 的 Azure CDN 模組"
description: "適用於 Node.js 的 Azure CDN 模組參考"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="b55a3-104">適用於 Node.js 的 Azure CDN 模組</span><span class="sxs-lookup"><span data-stu-id="b55a3-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b55a3-105">概觀</span><span class="sxs-lookup"><span data-stu-id="b55a3-105">Overview</span></span>

<span data-ttu-id="b55a3-106">Azure 內容傳遞網路 (CDN) 為開發人員提供一套傳遞高頻寬內容 (裝載在 Azure 或任何其他位置中) 的通用解決方案。</span><span class="sxs-lookup"><span data-stu-id="b55a3-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="b55a3-107">使用 CDN，可讓您快取從 Azure Blob 儲存體、Web 應用程式、虛擬機器、應用程式資料夾或其他 HTTP/HTTPS 位置載入的公用物件。</span><span class="sxs-lookup"><span data-stu-id="b55a3-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="b55a3-108">CDN 快取可以保留在策略性位置上，以提供最大頻寬將內容傳遞給使用者。</span><span class="sxs-lookup"><span data-stu-id="b55a3-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="b55a3-109">CDN 通常用來傳遞靜態內容，例如影像、樣式表、文件、檔案、用戶端指令碼和 HTML 頁面。</span><span class="sxs-lookup"><span data-stu-id="b55a3-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="b55a3-110">管理套件</span><span class="sxs-lookup"><span data-stu-id="b55a3-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b55a3-111">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b55a3-111">Install the npm module</span></span>

<span data-ttu-id="b55a3-112">安裝 Azure CDN npm 模組</span><span class="sxs-lookup"><span data-stu-id="b55a3-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="b55a3-113">範例</span><span class="sxs-lookup"><span data-stu-id="b55a3-113">Example</span></span>

<span data-ttu-id="b55a3-114">此範例會列出所有的 CDN 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b55a3-114">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="b55a3-115">範例</span><span class="sxs-lookup"><span data-stu-id="b55a3-115">Samples</span></span>

<span data-ttu-id="b55a3-116">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b55a3-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
