---
title: 適用於 Node.js 的 Azure 搜尋服務模組
description: 適用於 Node.js 的 Azure 搜尋服務模組參考
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52005902"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="919c6-103">適用於 Node.js 的 Azure 搜尋服務模組</span><span class="sxs-lookup"><span data-stu-id="919c6-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="919c6-104">Azure 搜尋服務是一項雲端搜尋即服務解決方案，可將伺服器和基礎結構管理委託給 Microsoft，讓您利用立即可用的服務來填入搜尋資料，然後用來在您的應用程式中新增搜尋。</span><span class="sxs-lookup"><span data-stu-id="919c6-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="919c6-105">深入了解 [Azure 搜尋服務](https://docs.microsoft.com/azure/search/search-what-is-azure-search)。</span><span class="sxs-lookup"><span data-stu-id="919c6-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="919c6-106">管理封裝</span><span class="sxs-lookup"><span data-stu-id="919c6-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="919c6-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="919c6-107">Install the npm module</span></span>

<span data-ttu-id="919c6-108">安裝 Azure 搜尋服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="919c6-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="919c6-109">範例</span><span class="sxs-lookup"><span data-stu-id="919c6-109">Example</span></span>

<span data-ttu-id="919c6-110">此範例會在 Azure 中建立新的搜尋服務，並列出其資源群組中的資源。</span><span class="sxs-lookup"><span data-stu-id="919c6-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="919c6-111">範例</span><span class="sxs-lookup"><span data-stu-id="919c6-111">Samples</span></span>

<span data-ttu-id="919c6-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="919c6-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
