---
title: "適用於 Node.js 的 Azure Operational Insights 模組"
description: "適用於 Node.js 的 Azure Operational Insights 模組參考"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="2e0c2-104">適用於 Node.js 的 Azure Operational Insights 模組</span><span class="sxs-lookup"><span data-stu-id="2e0c2-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2e0c2-105">概觀</span><span class="sxs-lookup"><span data-stu-id="2e0c2-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="2e0c2-106">管理套件</span><span class="sxs-lookup"><span data-stu-id="2e0c2-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2e0c2-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="2e0c2-107">Install the npm module</span></span>

<span data-ttu-id="2e0c2-108">使用 npm 來安裝適用於 Node.js 的 Azure Operational Insights 模組參考</span><span class="sxs-lookup"><span data-stu-id="2e0c2-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="2e0c2-109">範例</span><span class="sxs-lookup"><span data-stu-id="2e0c2-109">Example</span></span> 

<span data-ttu-id="2e0c2-110">此範例會建立用戶端，連線到 Operational Insights 以及擷取所指定資源群組的工作區清單。</span><span class="sxs-lookup"><span data-stu-id="2e0c2-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="2e0c2-111">範例</span><span class="sxs-lookup"><span data-stu-id="2e0c2-111">Samples</span></span>

<span data-ttu-id="2e0c2-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="2e0c2-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
