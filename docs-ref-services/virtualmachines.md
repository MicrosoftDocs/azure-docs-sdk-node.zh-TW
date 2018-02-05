---
title: "適用於 Node.js 的虛擬機器模組 - Azure"
description: "適用於 Node.js 的 Azure 虛擬機器模組參考指南"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>適用於 Node.js 的 Azure 虛擬機器模組

## <a name="overview"></a>概觀

透過適用於 Node.js 的 Azure 管理模組，從您的程式碼定義、設定及部署新的 Windows 和 Linux 虛擬機器和虛擬機器擴展集。 這些模組可讓您啟動和停止現有的虛擬機器，以及對您 Azure 訂用帳戶中已停止的 VM 連結或卸離磁碟。

## <a name="management-package"></a>管理封裝

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
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>範例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
