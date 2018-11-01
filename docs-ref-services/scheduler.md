---
title: 適用於 Node.js 的 Azure 排程器模組
description: 適用於 Node.js 的 Azure 排程器模組參考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406474"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="f757f-103">適用於 Node.js 的 Azure 排程器模組</span><span class="sxs-lookup"><span data-stu-id="f757f-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="f757f-104">Azure 排程器會透過 HTTP、HTTPS、儲存體佇列或 [Azure 服務匯流排](/azure/service-bus-messaging/service-bus-messaging-overview)，建立、維護和叫用已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f757f-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="f757f-105">深入了解 [Azure 排程器](/azure/scheduler/scheduler-intro)。</span><span class="sxs-lookup"><span data-stu-id="f757f-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="f757f-106">管理封裝</span><span class="sxs-lookup"><span data-stu-id="f757f-106">Management package</span></span>

<span data-ttu-id="f757f-107">透過管理 API，跨各種通訊通道建立、維護及叫用已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f757f-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f757f-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f757f-108">Install the npm module</span></span>

<span data-ttu-id="f757f-109">安裝 Azure 排程器 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f757f-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="f757f-110">範例</span><span class="sxs-lookup"><span data-stu-id="f757f-110">Example</span></span>

<span data-ttu-id="f757f-111">此範例會列出目前的排程器。</span><span class="sxs-lookup"><span data-stu-id="f757f-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="f757f-112">範例</span><span class="sxs-lookup"><span data-stu-id="f757f-112">Samples</span></span>

<span data-ttu-id="f757f-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f757f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
