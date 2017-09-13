---
title: "適用於 Node.js 的 Azure 虛擬機器模組"
description: "適用於 Node.js 的 Azure 虛擬機器模組參考"
keywords: "Azure, Node, SDK, API, 虛擬機器, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>適用於 Node.js 的 Azure 虛擬機器模組

## <a name="overview"></a>概觀

透過適用於 Node.js 的 Azure 管理模組，從您的程式碼定義、設定及部署新的 Windows 和 Linux 虛擬機器和虛擬機器擴展集。 這些模組可讓您啟動和停止現有的虛擬機器，以及對您 Azure 訂用帳戶中已停止的 VM 連結或卸離磁碟。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 計算 npm 模組

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>範例

下列範例說明如何登入 Azure、建立管理用戶端，並列出所指定位置、發行者、供應項目和 SKU 的所有 VM 映像。

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>範例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
