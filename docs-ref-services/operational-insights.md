---
title: "適用於 Node.js 的 Azure Operational Insights 模組"
description: "適用於 Node.js 的 Azure Operational Insights 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 7baa7f2f976cec9d9592231f193eede87a122532
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="fbf61-103">適用於 Node.js 的 Azure Operational Insights 模組</span><span class="sxs-lookup"><span data-stu-id="fbf61-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="fbf61-104">使用 npm 來安裝適用於 Node.js 的 Azure Operational Insights 模組參考</span><span class="sxs-lookup"><span data-stu-id="fbf61-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="fbf61-105">範例</span><span class="sxs-lookup"><span data-stu-id="fbf61-105">Example</span></span> 

<span data-ttu-id="fbf61-106">此範例會建立用戶端，連線到 Operational Insights 以及擷取所指定資源群組的工作區清單。</span><span class="sxs-lookup"><span data-stu-id="fbf61-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fbf61-107">範例</span><span class="sxs-lookup"><span data-stu-id="fbf61-107">Samples</span></span>

<span data-ttu-id="fbf61-108">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="fbf61-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
