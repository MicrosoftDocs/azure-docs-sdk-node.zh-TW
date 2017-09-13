---
title: "適用於 Node.js 的 Azure 事件中樞模組"
description: "適用於 Node.js 的 Azure 事件中樞模組參考"
keywords: Azure,SDK,API,Event Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="a5f5c-104">適用於 Node.js 的 Azure 事件中樞模組</span><span class="sxs-lookup"><span data-stu-id="a5f5c-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a5f5c-105">概觀</span><span class="sxs-lookup"><span data-stu-id="a5f5c-105">Overview</span></span>
<span data-ttu-id="a5f5c-106">Azure 事件中樞是可高度調整的資料串流平台，以及每秒能夠接收和處理數百萬個事件的事件內嵌服務。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="a5f5c-107">事件中樞可以處理及儲存分散式軟體和裝置所產生的事件、資料或遙測。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="a5f5c-108">傳送至事件中樞的資料可以透過任何即時分析提供者或批次/儲存體配接器來轉換和儲存。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="a5f5c-109">藉由提供大規模的低延遲發佈訂閱功能，事件中樞能成為引進巨量資料的途徑。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="a5f5c-110">管理套件</span><span class="sxs-lookup"><span data-stu-id="a5f5c-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a5f5c-111">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="a5f5c-111">Install the npm module</span></span> 

<span data-ttu-id="a5f5c-112">使用 npm 來安裝適用於 Node.js 的 Azure 事件中樞模組</span><span class="sxs-lookup"><span data-stu-id="a5f5c-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="a5f5c-113">範例</span><span class="sxs-lookup"><span data-stu-id="a5f5c-113">Example</span></span>

<span data-ttu-id="a5f5c-114">此範例會擷取現有事件中樞的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-114">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="a5f5c-115">範例</span><span class="sxs-lookup"><span data-stu-id="a5f5c-115">Samples</span></span>

<span data-ttu-id="a5f5c-116">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="a5f5c-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
