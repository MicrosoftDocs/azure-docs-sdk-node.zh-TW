---
title: 適用於 Node.js 的 Azure 監視器模組
description: 適用於 Node.js 的 Azure 監視器模組參考
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51424742"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="d3f54-103">適用於 Node.js 的 Azure 監視器模組</span><span class="sxs-lookup"><span data-stu-id="d3f54-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="d3f54-104">雲端應用程式相當複雜，且具有許多移動組件。</span><span class="sxs-lookup"><span data-stu-id="d3f54-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="d3f54-105">監視會提供資料，以確保應用程式持續運作並以健全的狀態執行。</span><span class="sxs-lookup"><span data-stu-id="d3f54-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="d3f54-106">它也可協助您預防潛在問題，或是針對過去所發生的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="d3f54-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="d3f54-107">除此之外，您還可以使用監視資料來取得應用程式的深入解析。</span><span class="sxs-lookup"><span data-stu-id="d3f54-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="d3f54-108">這些知識可協助您提升應用程式效能或維護性，或是將原本需要手動介入的動作自動化。</span><span class="sxs-lookup"><span data-stu-id="d3f54-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="d3f54-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="d3f54-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="d3f54-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="d3f54-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="d3f54-111">範例</span><span class="sxs-lookup"><span data-stu-id="d3f54-111">Example</span></span>

<span data-ttu-id="d3f54-112">此程式碼範例會列印與資源群組相關聯的所有警示規則。</span><span class="sxs-lookup"><span data-stu-id="d3f54-112">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });
```

### <a name="samples"></a><span data-ttu-id="d3f54-113">範例</span><span class="sxs-lookup"><span data-stu-id="d3f54-113">Samples</span></span>

<span data-ttu-id="d3f54-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d3f54-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
