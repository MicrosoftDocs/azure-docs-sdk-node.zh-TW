---
title: 適用於 Node.js 的 Azure Operational Insights 模組
description: 適用於 Node.js 的 Azure Operational Insights 模組參考
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261967"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="15c30-103">適用於 Node.js 的 Azure Operational Insights 模組</span><span class="sxs-lookup"><span data-stu-id="15c30-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="15c30-104">使用 npm 來安裝適用於 Node.js 的 Azure Operational Insights 模組參考</span><span class="sxs-lookup"><span data-stu-id="15c30-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="15c30-105">範例</span><span class="sxs-lookup"><span data-stu-id="15c30-105">Example</span></span> 

<span data-ttu-id="15c30-106">此範例會建立用戶端，連線到 Operational Insights 以及擷取所指定資源群組的工作區清單。</span><span class="sxs-lookup"><span data-stu-id="15c30-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="15c30-107">範例</span><span class="sxs-lookup"><span data-stu-id="15c30-107">Samples</span></span>

<span data-ttu-id="15c30-108">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="15c30-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
