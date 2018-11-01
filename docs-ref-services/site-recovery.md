---
title: 適用於 Node.js 的 Azure Site Recovery 模組
description: 適用於 Node.js 的 Azure Site Recovery 模組參考
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50273411"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="2d5f8-103">適用於 Node.js 的 Azure Site Recovery 模組</span><span class="sxs-lookup"><span data-stu-id="2d5f8-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="2d5f8-104">Site Recovery 可讓您自動執行區域、內部部署虛擬機器和實體伺服器之間至 Azure 的 Azure VM 複寫，以及自動執行內部部署機器至次要資料中心的複寫。</span><span class="sxs-lookup"><span data-stu-id="2d5f8-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="2d5f8-105">深入了解 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)。</span><span class="sxs-lookup"><span data-stu-id="2d5f8-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="2d5f8-106">管理封裝</span><span class="sxs-lookup"><span data-stu-id="2d5f8-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2d5f8-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="2d5f8-107">Install the npm module</span></span>

<span data-ttu-id="2d5f8-108">安裝 Azure Site Recovery 服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="2d5f8-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="2d5f8-109">範例</span><span class="sxs-lookup"><span data-stu-id="2d5f8-109">Example</span></span>

<span data-ttu-id="2d5f8-110">此範例會列出資源群組的 Site Recovery 服務。</span><span class="sxs-lookup"><span data-stu-id="2d5f8-110">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="2d5f8-111">範例</span><span class="sxs-lookup"><span data-stu-id="2d5f8-111">Samples</span></span>

<span data-ttu-id="2d5f8-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="2d5f8-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
