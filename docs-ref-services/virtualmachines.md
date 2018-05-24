---
title: 適用於 Node.js 的虛擬機器模組 - Azure
description: 適用於 Node.js 的 Azure 虛擬機器模組參考指南
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="ed83c-103">適用於 Node.js 的 Azure 虛擬機器模組</span><span class="sxs-lookup"><span data-stu-id="ed83c-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ed83c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="ed83c-104">Overview</span></span>

<span data-ttu-id="ed83c-105">透過適用於 Node.js 的 Azure 管理模組，從您的程式碼定義、設定及部署新的 Windows 和 Linux 虛擬機器和虛擬機器擴展集。</span><span class="sxs-lookup"><span data-stu-id="ed83c-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="ed83c-106">這些模組可讓您啟動和停止現有的虛擬機器，以及對您 Azure 訂用帳戶中已停止的 VM 連結或卸離磁碟。</span><span class="sxs-lookup"><span data-stu-id="ed83c-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="ed83c-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="ed83c-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ed83c-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ed83c-108">Install the npm module</span></span>

<span data-ttu-id="ed83c-109">安裝 Azure 計算 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ed83c-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="ed83c-110">範例</span><span class="sxs-lookup"><span data-stu-id="ed83c-110">Example</span></span>

<span data-ttu-id="ed83c-111">下列範例說明如何登入 Azure、建立管理用戶端，並列出所指定位置、發行者、供應項目和 SKU 的所有 VM 映像。</span><span class="sxs-lookup"><span data-stu-id="ed83c-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="ed83c-112">範例</span><span class="sxs-lookup"><span data-stu-id="ed83c-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="ed83c-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ed83c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
