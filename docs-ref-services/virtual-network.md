---
title: "適用於 Node.js 的 Azure 虛擬網路模組"
description: "適用於 Node.js 的 Azure 虛擬網路模組參考"
keywords: "Azure,SDK,API,虛擬網路, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>適用於 Node.js 的 Azure 虛擬網路模組

## <a name="overview"></a>概觀

Azure 虛擬網路服務可讓 Azure 資源與虛擬網路 (VNet) 安全地彼此連接。 VNet 是您的網路在雲端中的身分。 VNet 是專屬於您訂用帳戶的 Azure 雲端邏輯隔離。 您也可以將 VNet 連線到內部部署網路。

深入了解 [Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 虛擬網路 npm 模組

```bash
npm install azure-arm-network
```

### <a name="example"></a>範例

此範例會取得並列印虛擬網路的清單

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
