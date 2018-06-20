---
title: 適用於 Node.js 的 Azure 服務對應模組
description: 適用於 Node.js 的 Azure 服務對應模組參考
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265979"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="cc056-103">適用於 Node.js 的 Azure 服務對應模組</span><span class="sxs-lookup"><span data-stu-id="cc056-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="cc056-104">服務對應可自動探索 Windows 和 Linux 系統上的應用程式元件，並對應服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="cc056-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="cc056-105">不需要進行任何設定，只要安裝了代理程式，服務對應就會顯示橫跨任何 TCP 連線架構的伺服器、處理序和連接埠之間的連線。</span><span class="sxs-lookup"><span data-stu-id="cc056-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="cc056-106">深入了解 [Azure 服務對應](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)。</span><span class="sxs-lookup"><span data-stu-id="cc056-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="cc056-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="cc056-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cc056-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="cc056-108">Install the npm module</span></span>

<span data-ttu-id="cc056-109">安裝 Azure 服務對應 npm 模組</span><span class="sxs-lookup"><span data-stu-id="cc056-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="cc056-110">範例</span><span class="sxs-lookup"><span data-stu-id="cc056-110">Example</span></span>

<span data-ttu-id="cc056-111">此範例會列出指定資源群組和工作區的所有服務對應。</span><span class="sxs-lookup"><span data-stu-id="cc056-111">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="cc056-112">範例</span><span class="sxs-lookup"><span data-stu-id="cc056-112">Samples</span></span>

<span data-ttu-id="cc056-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="cc056-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
