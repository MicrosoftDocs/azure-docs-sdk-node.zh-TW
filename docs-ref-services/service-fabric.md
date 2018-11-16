---
title: 適用於 Node.js 的 Azure Service Fabric 模組
description: 供 Node.js 參照使用的 Azure Service Fabric 模組
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51438402"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a>適用於 Node.js 的 Azure Service Fabric 模組

## <a name="overview"></a>概觀

Azure Service Fabric 是一個分散式系統平台，可讓您輕鬆封裝、部署及管理可調整和可信賴的微服務與容器。

深入了解 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Service Fabric npm 模組

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a>範例

此範例會示範如何列出 Azure 訂用帳戶的叢集。

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

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
