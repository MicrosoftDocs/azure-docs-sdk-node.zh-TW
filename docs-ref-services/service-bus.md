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
# <a name="azure-service-bus-modules-for-nodejs"></a>適用於 Node.js 的 Azure 服務匯流排模組

## <a name="overview"></a>概觀

Azure 服務匯流排是非同步的訊息雲端平台，可讓您在彼此分離的系統之間傳送資料。

深入了解 [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝適用於 Node.js 的 Azure 服務匯流排模組

```bash
npm install azure-arm-sb
```

### <a name="example"></a>範例

此範例會建立用戶端，然後列出所有與指定之訂用帳戶相關聯的服務匯流排命名空間。

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

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
