---
title: 適用於 Node.js 的 Azure DNS 模組
description: 適用於 Node.js 的 Azure DNS 模組參考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52106325"
---
# <a name="azure-dns-modules-for-nodejs"></a>適用於 Node.js 的 Azure DNS 模組

使用 Azure DNS 在 Azure 中代管您的網域名稱系統 (DNS) 網域。 您可以使用其他 Azure 服務所使用的同一組認證、帳單及支援合約來管理您的 DNS 記錄。 將 Azure 服務與對應的 DNS 更新相整合，讓您的端對端部署程序得以簡化。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure DNS npm 模組

```bash
npm install azure-arm-dns
```

### <a name="example"></a>範例

此範例會列出 DNS 管理區域。

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
