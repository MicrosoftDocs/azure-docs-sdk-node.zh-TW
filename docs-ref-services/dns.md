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
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="c389f-104">適用於 Node.js 的 Azure DNS 模組</span><span class="sxs-lookup"><span data-stu-id="c389f-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c389f-105">概觀</span><span class="sxs-lookup"><span data-stu-id="c389f-105">Overview</span></span>

<span data-ttu-id="c389f-106">使用 Azure DNS 在 Azure 中代管您的網域名稱系統 (DNS) 網域。</span><span class="sxs-lookup"><span data-stu-id="c389f-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="c389f-107">您可以使用其他 Azure 服務所使用的同一組認證、帳單及支援合約來管理您的 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="c389f-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="c389f-108">將 Azure 服務與對應的 DNS 更新相整合，讓您的端對端部署程序得以簡化。</span><span class="sxs-lookup"><span data-stu-id="c389f-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="c389f-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="c389f-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c389f-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="c389f-110">Install the npm module</span></span>

<span data-ttu-id="c389f-111">安裝 Azure DNS npm 模組</span><span class="sxs-lookup"><span data-stu-id="c389f-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="c389f-112">範例</span><span class="sxs-lookup"><span data-stu-id="c389f-112">Example</span></span>

<span data-ttu-id="c389f-113">此範例會列出 DNS 管理區域。</span><span class="sxs-lookup"><span data-stu-id="c389f-113">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c389f-114">範例</span><span class="sxs-lookup"><span data-stu-id="c389f-114">Samples</span></span>

<span data-ttu-id="c389f-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="c389f-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
