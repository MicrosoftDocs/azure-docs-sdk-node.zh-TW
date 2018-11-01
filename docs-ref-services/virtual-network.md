---
title: 適用於 Node.js 的 Azure 虛擬網路模組
description: 適用於 Node.js 的 Azure 虛擬網路模組參考
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406444"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="b456c-103">適用於 Node.js 的 Azure 虛擬網路模組</span><span class="sxs-lookup"><span data-stu-id="b456c-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b456c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="b456c-104">Overview</span></span>

<span data-ttu-id="b456c-105">Azure 虛擬網路服務可讓 Azure 資源與虛擬網路 (VNet) 安全地彼此連接。</span><span class="sxs-lookup"><span data-stu-id="b456c-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="b456c-106">VNet 是您的網路在雲端中的身分。</span><span class="sxs-lookup"><span data-stu-id="b456c-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="b456c-107">VNet 是專屬於您訂用帳戶的 Azure 雲端邏輯隔離。</span><span class="sxs-lookup"><span data-stu-id="b456c-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="b456c-108">您也可以將 VNet 連線到內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="b456c-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="b456c-109">深入了解 [Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)。</span><span class="sxs-lookup"><span data-stu-id="b456c-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b456c-110">管理封裝</span><span class="sxs-lookup"><span data-stu-id="b456c-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b456c-111">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b456c-111">Install the npm module</span></span>

<span data-ttu-id="b456c-112">安裝 Azure 虛擬網路 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b456c-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="b456c-113">範例</span><span class="sxs-lookup"><span data-stu-id="b456c-113">Example</span></span>

<span data-ttu-id="b456c-114">此範例會取得並列印虛擬網路的清單</span><span class="sxs-lookup"><span data-stu-id="b456c-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="b456c-115">範例</span><span class="sxs-lookup"><span data-stu-id="b456c-115">Samples</span></span>

<span data-ttu-id="b456c-116">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b456c-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
