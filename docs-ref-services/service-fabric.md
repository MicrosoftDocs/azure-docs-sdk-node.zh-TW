---
title: "適用於 Node.js 的 Azure Service Fabric 模組"
description: "供 Node.js 參照使用的 Azure Service Fabric 模組"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: c855e0003a4b6f4a4d75f37b4c8480721fe0a942
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="17048-103">適用於 Node.js 的 Azure Service Fabric 模組</span><span class="sxs-lookup"><span data-stu-id="17048-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="17048-104">概觀</span><span class="sxs-lookup"><span data-stu-id="17048-104">Overview</span></span>

<span data-ttu-id="17048-105">Azure Service Fabric 是一個分散式系統平台，可讓您輕鬆封裝、部署及管理可調整和可信賴的微服務與容器。</span><span class="sxs-lookup"><span data-stu-id="17048-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="17048-106">深入了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。</span><span class="sxs-lookup"><span data-stu-id="17048-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="17048-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="17048-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="17048-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="17048-108">Install the npm module</span></span>

<span data-ttu-id="17048-109">安裝 Azure Service Fabric npm 模組</span><span class="sxs-lookup"><span data-stu-id="17048-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="17048-110">範例</span><span class="sxs-lookup"><span data-stu-id="17048-110">Example</span></span>

<span data-ttu-id="17048-111">此範例會示範如何列出 Azure 訂用帳戶的叢集。</span><span class="sxs-lookup"><span data-stu-id="17048-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="17048-112">範例</span><span class="sxs-lookup"><span data-stu-id="17048-112">Samples</span></span>

<span data-ttu-id="17048-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="17048-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
