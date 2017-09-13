---
title: "適用於 Node.js 的 Azure Analysis Services 模組"
description: "適用於 Node.js 的 Azure Analysis Services 模組參考"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="d7ae5-104">適用於 Node.js 的 Azure Analysis Services 模組</span><span class="sxs-lookup"><span data-stu-id="d7ae5-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d7ae5-105">概觀</span><span class="sxs-lookup"><span data-stu-id="d7ae5-105">Overview</span></span>
<span data-ttu-id="d7ae5-106">此套件提供可讓您輕鬆管理 Microsoft Azure Analysis Services 的 Node.js 模組。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="d7ae5-107">管理套件</span><span class="sxs-lookup"><span data-stu-id="d7ae5-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d7ae5-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="d7ae5-108">Install the npm module</span></span>

<span data-ttu-id="d7ae5-109">安裝 Azure Analysis Services npm 模組</span><span class="sxs-lookup"><span data-stu-id="d7ae5-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="d7ae5-110">範例</span><span class="sxs-lookup"><span data-stu-id="d7ae5-110">Example</span></span>

<span data-ttu-id="d7ae5-111">此範例會列出所有可用的 Analysis Service 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-111">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d7ae5-112">範例</span><span class="sxs-lookup"><span data-stu-id="d7ae5-112">Samples</span></span>

<span data-ttu-id="d7ae5-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d7ae5-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
