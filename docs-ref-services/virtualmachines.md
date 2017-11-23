---
title: "適用於 Node.js 的 Azure 虛擬機器模組"
description: "適用於 Node.js 的 Azure 虛擬機器模組參考"
keywords: "Azure, Node, SDK, API, 虛擬機器, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="0d7b8-104">適用於 Node.js 的 Azure 虛擬機器模組</span><span class="sxs-lookup"><span data-stu-id="0d7b8-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0d7b8-105">概觀</span><span class="sxs-lookup"><span data-stu-id="0d7b8-105">Overview</span></span>

<span data-ttu-id="0d7b8-106">透過適用於 Node.js 的 Azure 管理模組，從您的程式碼定義、設定及部署新的 Windows 和 Linux 虛擬機器和虛擬機器擴展集。</span><span class="sxs-lookup"><span data-stu-id="0d7b8-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="0d7b8-107">這些模組可讓您啟動和停止現有的虛擬機器，以及對您 Azure 訂用帳戶中已停止的 VM 連結或卸離磁碟。</span><span class="sxs-lookup"><span data-stu-id="0d7b8-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="0d7b8-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="0d7b8-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0d7b8-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="0d7b8-109">Install the npm module</span></span>

<span data-ttu-id="0d7b8-110">安裝 Azure 計算 npm 模組</span><span class="sxs-lookup"><span data-stu-id="0d7b8-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="0d7b8-111">範例</span><span class="sxs-lookup"><span data-stu-id="0d7b8-111">Example</span></span>

<span data-ttu-id="0d7b8-112">下列範例說明如何登入 Azure、建立管理用戶端，並列出所指定位置、發行者、供應項目和 SKU 的所有 VM 映像。</span><span class="sxs-lookup"><span data-stu-id="0d7b8-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="0d7b8-113">範例</span><span class="sxs-lookup"><span data-stu-id="0d7b8-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="0d7b8-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="0d7b8-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
