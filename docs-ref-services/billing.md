---
title: "適用於 Node.js 的 Azure 計費模組"
description: "適用於 Node.js 的 Azure 計畫模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="6e864-103">適用於 Node.js 的 Azure 計費模組</span><span class="sxs-lookup"><span data-stu-id="6e864-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6e864-104">概觀</span><span class="sxs-lookup"><span data-stu-id="6e864-104">Overview</span></span>
<span data-ttu-id="6e864-105">Azure 計費 API 可供存取您的 Azure 計費資訊和發票。</span><span class="sxs-lookup"><span data-stu-id="6e864-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="6e864-106">若要使用此 API，帳戶管理員必須透過 Azure 入口網站選擇加入。</span><span class="sxs-lookup"><span data-stu-id="6e864-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="6e864-107">請參閱[使用角色來管理對 Azure 帳單的存取](https://docs.microsoft.com/azure/billing/billing-manage-access)。</span><span class="sxs-lookup"><span data-stu-id="6e864-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6e864-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="6e864-108">Install the npm module</span></span> 

<span data-ttu-id="6e864-109">安裝 Azure 計費 npm 模組</span><span class="sxs-lookup"><span data-stu-id="6e864-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="6e864-110">範例</span><span class="sxs-lookup"><span data-stu-id="6e864-110">Example</span></span> 
 
<span data-ttu-id="6e864-111">此範例會列印您過去所有發票的清單。</span><span class="sxs-lookup"><span data-stu-id="6e864-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="6e864-112">範例</span><span class="sxs-lookup"><span data-stu-id="6e864-112">Samples</span></span>

<span data-ttu-id="6e864-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="6e864-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
