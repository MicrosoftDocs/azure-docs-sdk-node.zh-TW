---
title: 適用於 Node.js 的 Azure Container Service 模組
description: 適用於 Node.js 的 Azure Container Service 模組參考
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689822"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Microsoft Azure SDK for Node.js - ContainerServiceClient
此專案提供用於存取 Azure 的 Node.js 套件。 它目前支援︰
- **Node.js 6.x.x 版或更新版本**

## <a name="features"></a>特性


## <a name="how-to-install"></a>如何安裝

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>使用方式

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>驗證、用戶端建立，以及以範例形式列出 containerServices。

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a>相關專案

- [Microsoft Azure SDK for Node.js](https://github.com/Azure/azure-sdk-for-node)