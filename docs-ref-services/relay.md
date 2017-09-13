---
title: "適用於 Node.js 的 Azure Relay 模組"
description: "適用於 Node.js 的 Azure Relay 模組參考"
keywords: Azure,SDK,API,Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a>適用於 Node.js 的 Azure Relay 模組

## <a name="overview"></a>概觀

Azure 轉送服務可建立混合式應用程式，方法是讓您以安全的方式向公用雲端公開位於企業網路內部的服務，而無需開啟防火牆連線或要求對企業網路基礎結構的進行侵入式變更。 轉送支援各種不同的傳輸通訊協定和 Web 服務標準。

深入了解 [Azure 轉送](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Relay npm 模組

```bash
npm install azure-arm-relay
```

### <a name="example"></a>範例

此範例會列出 Relay 用戶端的命名空間。

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
