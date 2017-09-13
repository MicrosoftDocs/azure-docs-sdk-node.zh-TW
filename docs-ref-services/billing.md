---
title: "適用於 Node.js 的 Azure 計費模組"
description: "適用於 Node.js 的 Azure 計畫模組參考"
keywords: Azure,SDK,API,Billing, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a>適用於 Node.js 的 Azure 計費模組

## <a name="overview"></a>概觀
Azure 計費 API 可供存取您的 Azure 計費資訊和發票。

若要使用此 API，帳戶管理員必須透過 Azure 入口網站選擇加入。 請參閱[使用角色來管理對 Azure 帳單的存取](https://docs.microsoft.com/azure/billing/billing-manage-access)。

### <a name="install-the-npm-module"></a>安裝 npm 模組 

安裝 Azure 計費 npm 模組 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>範例 
 
此範例會列印您過去所有發票的清單。
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
