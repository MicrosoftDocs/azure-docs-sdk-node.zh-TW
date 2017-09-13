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
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="64412-104">適用於 Node.js 的 Azure 計費模組</span><span class="sxs-lookup"><span data-stu-id="64412-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="64412-105">概觀</span><span class="sxs-lookup"><span data-stu-id="64412-105">Overview</span></span>
<span data-ttu-id="64412-106">Azure 計費 API 可供存取您的 Azure 計費資訊和發票。</span><span class="sxs-lookup"><span data-stu-id="64412-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="64412-107">若要使用此 API，帳戶管理員必須透過 Azure 入口網站選擇加入。</span><span class="sxs-lookup"><span data-stu-id="64412-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="64412-108">請參閱[使用角色來管理對 Azure 帳單的存取](https://docs.microsoft.com/azure/billing/billing-manage-access)。</span><span class="sxs-lookup"><span data-stu-id="64412-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="64412-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="64412-109">Install the npm module</span></span> 

<span data-ttu-id="64412-110">安裝 Azure 計費 npm 模組</span><span class="sxs-lookup"><span data-stu-id="64412-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="64412-111">範例</span><span class="sxs-lookup"><span data-stu-id="64412-111">Example</span></span> 
 
<span data-ttu-id="64412-112">此範例會列印您過去所有發票的清單。</span><span class="sxs-lookup"><span data-stu-id="64412-112">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="64412-113">範例</span><span class="sxs-lookup"><span data-stu-id="64412-113">Samples</span></span>

<span data-ttu-id="64412-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="64412-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
