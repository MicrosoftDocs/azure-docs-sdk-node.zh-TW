---
title: "適用於 Node.js 的 Azure Service Fabric 模組"
description: "適用於 Node.js 的 Azure Service Fabric 模組參考"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="ba9fc-104">適用於 Node.js 的 Azure Service Fabric 模組</span><span class="sxs-lookup"><span data-stu-id="ba9fc-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ba9fc-105">概觀</span><span class="sxs-lookup"><span data-stu-id="ba9fc-105">Overview</span></span>

<span data-ttu-id="ba9fc-106">Azure Service Fabric 是一個分散式系統平台，可讓您輕鬆封裝、部署及管理可調整和可信賴的微服務與容器。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="ba9fc-107">深入了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="ba9fc-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="ba9fc-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ba9fc-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ba9fc-109">Install the npm module</span></span>

<span data-ttu-id="ba9fc-110">安裝 Azure Service Fabric npm 模組</span><span class="sxs-lookup"><span data-stu-id="ba9fc-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="ba9fc-111">範例</span><span class="sxs-lookup"><span data-stu-id="ba9fc-111">Example</span></span>

<span data-ttu-id="ba9fc-112">此範例會示範如何列出 Azure 訂用帳戶的叢集。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="ba9fc-113">範例</span><span class="sxs-lookup"><span data-stu-id="ba9fc-113">Samples</span></span>

<span data-ttu-id="ba9fc-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ba9fc-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
