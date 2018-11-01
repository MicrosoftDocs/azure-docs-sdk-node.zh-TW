---
title: 適用於 Node.js 的 Azure 服務對應模組
description: 適用於 Node.js 的 Azure 服務對應模組參考
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50330016"
---
# <a name="azure-service-map-modules-for-nodejs"></a>適用於 Node.js 的 Azure 服務對應模組

服務對應可自動探索 Windows 和 Linux 系統上的應用程式元件，並對應服務之間的通訊。 不需要進行任何設定，只要安裝了代理程式，服務對應就會顯示橫跨任何 TCP 連線架構的伺服器、處理序和連接埠之間的連線。

深入了解 [Azure 服務對應](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 服務對應 npm 模組

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>範例

此範例會列出指定資源群組和工作區的所有服務對應。

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
