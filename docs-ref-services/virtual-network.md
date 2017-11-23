---
title: "適用於 Node.js 的 Azure 虛擬網路模組"
description: "適用於 Node.js 的 Azure 虛擬網路模組參考"
keywords: "Azure,SDK,API,虛擬網路, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="c5cea-104">適用於 Node.js 的 Azure 虛擬網路模組</span><span class="sxs-lookup"><span data-stu-id="c5cea-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c5cea-105">概觀</span><span class="sxs-lookup"><span data-stu-id="c5cea-105">Overview</span></span>

<span data-ttu-id="c5cea-106">Azure 虛擬網路服務可讓 Azure 資源與虛擬網路 (VNet) 安全地彼此連接。</span><span class="sxs-lookup"><span data-stu-id="c5cea-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="c5cea-107">VNet 是您的網路在雲端中的身分。</span><span class="sxs-lookup"><span data-stu-id="c5cea-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="c5cea-108">VNet 是專屬於您訂用帳戶的 Azure 雲端邏輯隔離。</span><span class="sxs-lookup"><span data-stu-id="c5cea-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="c5cea-109">您也可以將 VNet 連線到內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="c5cea-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="c5cea-110">深入了解 [Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。</span><span class="sxs-lookup"><span data-stu-id="c5cea-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c5cea-111">管理套件</span><span class="sxs-lookup"><span data-stu-id="c5cea-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c5cea-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="c5cea-112">Install the npm module</span></span>

<span data-ttu-id="c5cea-113">安裝 Azure 虛擬網路 npm 模組</span><span class="sxs-lookup"><span data-stu-id="c5cea-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="c5cea-114">範例</span><span class="sxs-lookup"><span data-stu-id="c5cea-114">Example</span></span>

<span data-ttu-id="c5cea-115">此範例會取得並列印虛擬網路的清單</span><span class="sxs-lookup"><span data-stu-id="c5cea-115">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="c5cea-116">範例</span><span class="sxs-lookup"><span data-stu-id="c5cea-116">Samples</span></span>

<span data-ttu-id="c5cea-117">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="c5cea-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
