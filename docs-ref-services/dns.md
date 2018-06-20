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
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262215"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="f5fdf-103">適用於 Node.js 的 Azure DNS 模組</span><span class="sxs-lookup"><span data-stu-id="f5fdf-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="f5fdf-104">使用 Azure DNS 在 Azure 中代管您的網域名稱系統 (DNS) 網域。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="f5fdf-105">您可以使用其他 Azure 服務所使用的同一組認證、帳單及支援合約來管理您的 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="f5fdf-106">將 Azure 服務與對應的 DNS 更新相整合，讓您的端對端部署程序得以簡化。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="f5fdf-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="f5fdf-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f5fdf-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f5fdf-108">Install the npm module</span></span>

<span data-ttu-id="f5fdf-109">安裝 Azure DNS npm 模組</span><span class="sxs-lookup"><span data-stu-id="f5fdf-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="f5fdf-110">範例</span><span class="sxs-lookup"><span data-stu-id="f5fdf-110">Example</span></span>

<span data-ttu-id="f5fdf-111">此範例會列出 DNS 管理區域。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f5fdf-112">範例</span><span class="sxs-lookup"><span data-stu-id="f5fdf-112">Samples</span></span>

<span data-ttu-id="f5fdf-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
