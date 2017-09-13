---
title: "適用於 Node.js 的 Azure DNS 模組"
description: "適用於 Node.js 的 Azure DNS 模組參考"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>適用於 Node.js 的 Azure DNS 模組

## <a name="overview"></a>概觀

使用 Azure DNS 在 Azure 中代管您的網域名稱系統 (DNS) 網域。 您可以使用其他 Azure 服務所使用的同一組認證、帳單及支援合約來管理您的 DNS 記錄。 將 Azure 服務與對應的 DNS 更新相整合，讓您的端對端部署程序得以簡化。

## <a name="management-package"></a>管理套件

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
