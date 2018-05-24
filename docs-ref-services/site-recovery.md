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
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="279e0-103">適用於 Node.js 的 Azure Site Recovery 模組</span><span class="sxs-lookup"><span data-stu-id="279e0-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="279e0-104">Site Recovery 可讓您自動執行區域、內部部署虛擬機器和實體伺服器之間至 Azure 的 Azure VM 複寫，以及自動執行內部部署機器至次要資料中心的複寫。</span><span class="sxs-lookup"><span data-stu-id="279e0-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="279e0-105">深入了解 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)。</span><span class="sxs-lookup"><span data-stu-id="279e0-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="279e0-106">管理封裝</span><span class="sxs-lookup"><span data-stu-id="279e0-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="279e0-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="279e0-107">Install the npm module</span></span>

<span data-ttu-id="279e0-108">安裝 Azure Site Recovery 服務 npm 模組</span><span class="sxs-lookup"><span data-stu-id="279e0-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="279e0-109">範例</span><span class="sxs-lookup"><span data-stu-id="279e0-109">Example</span></span>

<span data-ttu-id="279e0-110">此範例會列出資源群組的 Site Recovery 服務。</span><span class="sxs-lookup"><span data-stu-id="279e0-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="279e0-111">範例</span><span class="sxs-lookup"><span data-stu-id="279e0-111">Samples</span></span>

<span data-ttu-id="279e0-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="279e0-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
