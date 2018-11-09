---
title: 適用於 Node.js 的 Azure 事件中樞模組
description: 適用於 Node.js 的 Azure 事件中樞模組參考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: cf50d0e69e336dac9addc85625599fbbefd1902e
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121827"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="b0b2b-103">適用於 Node.js 的 Azure 事件中樞模組</span><span class="sxs-lookup"><span data-stu-id="b0b2b-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="b0b2b-104">Azure 事件中樞是可高度調整的資料串流平台，以及每秒能夠接收和處理數百萬個事件的事件內嵌服務。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="b0b2b-105">事件中樞可以處理及儲存分散式軟體和裝置所產生的事件、資料或遙測。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="b0b2b-106">傳送至事件中樞的資料可以透過任何即時分析提供者或批次/儲存體配接器來轉換和儲存。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="b0b2b-107">藉由提供大規模的低延遲發佈訂閱功能，事件中樞能成為引進巨量資料的途徑。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="b0b2b-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="b0b2b-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b0b2b-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b0b2b-109">Install the npm module</span></span> 

<span data-ttu-id="b0b2b-110">使用 npm 來安裝適用於 Node.js 的 Azure 事件中樞模組</span><span class="sxs-lookup"><span data-stu-id="b0b2b-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="b0b2b-111">範例</span><span class="sxs-lookup"><span data-stu-id="b0b2b-111">Example</span></span>

<span data-ttu-id="b0b2b-112">此範例會擷取現有事件中樞的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-112">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b0b2b-113">範例</span><span class="sxs-lookup"><span data-stu-id="b0b2b-113">Samples</span></span>

<span data-ttu-id="b0b2b-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b0b2b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
