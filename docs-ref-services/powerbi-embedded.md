---
title: "適用於 Node.js 的 Azure PowerBI Embedded 模組"
description: "適用於 Node.js 的 Azure PowerBI Embedded 模組參考"
keywords: Azure,SDK,API,PowerBI Embedded, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 74e69421d372ff4ccaebf2b811152dd83b9b4e7b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="c78d7-104">適用於 Node.js 的 Azure PowerBI Embedded 模組</span><span class="sxs-lookup"><span data-stu-id="c78d7-104">Azure PowerBI Embedded modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c78d7-105">概觀</span><span class="sxs-lookup"><span data-stu-id="c78d7-105">Overview</span></span>

<span data-ttu-id="c78d7-106">運用 Power BI Embedded Azure 服務，您可以將 Power BI 報告整合至 Node 應用程式以建立或編輯圖表和報告。</span><span class="sxs-lookup"><span data-stu-id="c78d7-106">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="c78d7-107">深入了解 [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)。</span><span class="sxs-lookup"><span data-stu-id="c78d7-107">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="c78d7-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="c78d7-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c78d7-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="c78d7-109">Install the npm module</span></span>

<span data-ttu-id="c78d7-110">安裝 Azure Power BI npm 模組</span><span class="sxs-lookup"><span data-stu-id="c78d7-110">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="c78d7-111">範例</span><span class="sxs-lookup"><span data-stu-id="c78d7-111">Example</span></span>

<span data-ttu-id="c78d7-112">此範例會在現有的資源群組中建立工作區集合。</span><span class="sxs-lookup"><span data-stu-id="c78d7-112">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="c78d7-113">範例</span><span class="sxs-lookup"><span data-stu-id="c78d7-113">Samples</span></span>

<span data-ttu-id="c78d7-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="c78d7-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
