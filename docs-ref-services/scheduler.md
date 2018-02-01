---
title: "適用於 Node.js 的 Azure 排程器模組"
description: "適用於 Node.js 的 Azure 排程器模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 539337abd2fff3830cb022a49aff374e877a08ee
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-scheduler-modules-for-nodejs"></a>適用於 Node.js 的 Azure 排程器模組

Azure 排程器會透過 HTTP、HTTPS、儲存體佇列或 [Azure 服務匯流排](/azure/service-bus-messaging/service-bus-messaging-overview)，建立、維護和叫用已排程的工作。

深入了解 [Azure 排程器](/azure/scheduler/scheduler-intro)。

## <a name="management-package"></a>管理封裝

透過管理 API，跨各種通訊通道建立、維護及叫用已排程的工作。

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 排程器 npm 模組

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>範例

此範例會列出目前的排程器。

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

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
