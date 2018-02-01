---
title: "適用於 Node.js 的 Azure Analysis Services 模組"
description: "適用於 Node.js 的 Azure Analysis Services 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 7dd9ac4a2a4939b66f5a91d048e49fb59cd547c0
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="6991d-103">適用於 Node.js 的 Azure Analysis Services 模組</span><span class="sxs-lookup"><span data-stu-id="6991d-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6991d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="6991d-104">Overview</span></span>
<span data-ttu-id="6991d-105">此套件提供可讓您輕鬆管理 Microsoft Azure Analysis Services 的 Node.js 模組。</span><span class="sxs-lookup"><span data-stu-id="6991d-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="6991d-106">管理封裝</span><span class="sxs-lookup"><span data-stu-id="6991d-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6991d-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="6991d-107">Install the npm module</span></span>

<span data-ttu-id="6991d-108">安裝 Azure Analysis Services npm 模組</span><span class="sxs-lookup"><span data-stu-id="6991d-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="6991d-109">範例</span><span class="sxs-lookup"><span data-stu-id="6991d-109">Example</span></span>

<span data-ttu-id="6991d-110">此範例會列出所有可用的 Analysis Service 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6991d-110">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="6991d-111">範例</span><span class="sxs-lookup"><span data-stu-id="6991d-111">Samples</span></span>

<span data-ttu-id="6991d-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="6991d-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
