---
title: "適用於 Node.js 的 Azure Commerce 模組"
description: "適用於 Node.js 的 Azure Commerce 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 0597765543cd838049d3946b90ae128875edd4e5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="9c60b-103">適用於 Node.js 的 Azure Commerce 模組</span><span class="sxs-lookup"><span data-stu-id="9c60b-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9c60b-104">概觀</span><span class="sxs-lookup"><span data-stu-id="9c60b-104">Overview</span></span>

<span data-ttu-id="9c60b-105">使用 Azure Commerce API 將使用情況和資源資料提取到您慣用的資料分析工具。</span><span class="sxs-lookup"><span data-stu-id="9c60b-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="9c60b-106">Azure 資源使用情況和 RateCard API 可協助您準確地預測並管理成本。</span><span class="sxs-lookup"><span data-stu-id="9c60b-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="9c60b-107">這些 API 會實作為資源提供者，並成為 Azure Resource Manager 所公開之 API 系列的一部分。</span><span class="sxs-lookup"><span data-stu-id="9c60b-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="9c60b-108">管理封裝</span><span class="sxs-lookup"><span data-stu-id="9c60b-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9c60b-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="9c60b-109">Install the npm module</span></span>

<span data-ttu-id="9c60b-110">安裝 Azure Commerce npm 模組</span><span class="sxs-lookup"><span data-stu-id="9c60b-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="9c60b-111">範例</span><span class="sxs-lookup"><span data-stu-id="9c60b-111">Example</span></span>

<span data-ttu-id="9c60b-112">此範例會擷取您上個月估計的 Azure 取用資料。</span><span class="sxs-lookup"><span data-stu-id="9c60b-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="9c60b-113">範例</span><span class="sxs-lookup"><span data-stu-id="9c60b-113">Samples</span></span>

<span data-ttu-id="9c60b-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9c60b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
