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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="d32ff-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="d32ff-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="d32ff-104">此專案提供用於存取 Azure 的 Node.js 套件。</span><span class="sxs-lookup"><span data-stu-id="d32ff-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="d32ff-105">它目前支援︰</span><span class="sxs-lookup"><span data-stu-id="d32ff-105">Right now it supports:</span></span>
- <span data-ttu-id="d32ff-106">**Node.js 6.x.x 版或更新版本**</span><span class="sxs-lookup"><span data-stu-id="d32ff-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="d32ff-107">特性</span><span class="sxs-lookup"><span data-stu-id="d32ff-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="d32ff-108">如何安裝</span><span class="sxs-lookup"><span data-stu-id="d32ff-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="d32ff-109">使用方式</span><span class="sxs-lookup"><span data-stu-id="d32ff-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="d32ff-110">驗證、用戶端建立，以及以範例形式列出 containerServices。</span><span class="sxs-lookup"><span data-stu-id="d32ff-110">Authentication, client creation and list containerServices as an example.</span></span>

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

## <a name="related-projects"></a><span data-ttu-id="d32ff-111">相關專案</span><span class="sxs-lookup"><span data-stu-id="d32ff-111">Related projects</span></span>

- [<span data-ttu-id="d32ff-112">Microsoft Azure SDK for Node.js</span><span class="sxs-lookup"><span data-stu-id="d32ff-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)