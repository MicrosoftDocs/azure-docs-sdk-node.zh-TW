---
title: "適用於 Node.js 的 Azure 服務匯流排模組"
description: "適用於 Node.js 的 Azure 服務匯流排模組參考"
keywords: "Azure,SDK,API,服務匯流排, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="03393-104">適用於 Node.js 的 Azure 服務匯流排模組</span><span class="sxs-lookup"><span data-stu-id="03393-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="03393-105">概觀</span><span class="sxs-lookup"><span data-stu-id="03393-105">Overview</span></span>

<span data-ttu-id="03393-106">Azure 服務匯流排是非同步的訊息雲端平台，可讓您在彼此分離的系統之間傳送資料。</span><span class="sxs-lookup"><span data-stu-id="03393-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="03393-107">深入了解 [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)。</span><span class="sxs-lookup"><span data-stu-id="03393-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="03393-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="03393-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="03393-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="03393-109">Install the npm module</span></span>

<span data-ttu-id="03393-110">使用 npm 來安裝適用於 Node.js 的 Azure 服務匯流排模組</span><span class="sxs-lookup"><span data-stu-id="03393-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="03393-111">範例</span><span class="sxs-lookup"><span data-stu-id="03393-111">Example</span></span>

<span data-ttu-id="03393-112">此範例會建立用戶端，然後列出所有與指定之訂用帳戶相關聯的服務匯流排命名空間。</span><span class="sxs-lookup"><span data-stu-id="03393-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="03393-113">範例</span><span class="sxs-lookup"><span data-stu-id="03393-113">Samples</span></span>

<span data-ttu-id="03393-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="03393-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
