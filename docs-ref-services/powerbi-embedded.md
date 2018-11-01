---
title: 適用於 Node.js 的 Azure PowerBI Embedded 模組
description: 適用於 Node.js 的 Azure PowerBI Embedded 模組參考
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50405754"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="615ae-103">適用於 Node.js 的 Azure PowerBI Embedded 模組</span><span class="sxs-lookup"><span data-stu-id="615ae-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="615ae-104">運用 Power BI Embedded Azure 服務，您可以將 Power BI 報告整合至 Node 應用程式以建立或編輯圖表和報告。</span><span class="sxs-lookup"><span data-stu-id="615ae-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="615ae-105">深入了解 [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)。</span><span class="sxs-lookup"><span data-stu-id="615ae-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="615ae-106">管理套件</span><span class="sxs-lookup"><span data-stu-id="615ae-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="615ae-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="615ae-107">Install the npm module</span></span>

<span data-ttu-id="615ae-108">安裝 Azure Power BI npm 模組</span><span class="sxs-lookup"><span data-stu-id="615ae-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="615ae-109">範例</span><span class="sxs-lookup"><span data-stu-id="615ae-109">Example</span></span>

<span data-ttu-id="615ae-110">此範例會在現有的資源群組中建立工作區集合。</span><span class="sxs-lookup"><span data-stu-id="615ae-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="615ae-111">範例</span><span class="sxs-lookup"><span data-stu-id="615ae-111">Samples</span></span>

<span data-ttu-id="615ae-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="615ae-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
