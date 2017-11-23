---
title: "適用於 Node.js 的 Azure 搜尋服務模組"
description: "適用於 Node.js 的 Azure 搜尋服務模組參考"
keywords: "Azure,SDK,API,搜尋, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="0da97-104">適用於 Node.js 的 Azure 搜尋服務模組</span><span class="sxs-lookup"><span data-stu-id="0da97-104">Azure Search modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0da97-105">概觀</span><span class="sxs-lookup"><span data-stu-id="0da97-105">Overview</span></span>

<span data-ttu-id="0da97-106">Azure 搜尋服務是一項雲端搜尋即服務解決方案，可將伺服器和基礎結構管理委託給 Microsoft，讓您利用立即可用的服務來填入搜尋資料，然後用來在您的應用程式中新增搜尋。</span><span class="sxs-lookup"><span data-stu-id="0da97-106">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="0da97-107">深入了解 [Azure 搜尋服務](https://docs.microsoft.com/azure/search/search-what-is-azure-search)。</span><span class="sxs-lookup"><span data-stu-id="0da97-107">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="0da97-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="0da97-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0da97-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="0da97-109">Install the npm module</span></span>

<span data-ttu-id="0da97-110">安裝 Azure 搜尋服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="0da97-110">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="0da97-111">範例</span><span class="sxs-lookup"><span data-stu-id="0da97-111">Example</span></span>

<span data-ttu-id="0da97-112">此範例會在 Azure 中建立新的搜尋服務，並列出其資源群組中的資源。</span><span class="sxs-lookup"><span data-stu-id="0da97-112">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="0da97-113">範例</span><span class="sxs-lookup"><span data-stu-id="0da97-113">Samples</span></span>

<span data-ttu-id="0da97-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0da97-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
