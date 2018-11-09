---
title: 適用於 Node.js 的 Azure 流量管理員模組
description: 供 Node.js 參照使用的 Azure 流量管理員模組
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121817"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="ae447-103">適用於 Node.js 的 Azure 流量管理員模組</span><span class="sxs-lookup"><span data-stu-id="ae447-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ae447-104">概觀</span><span class="sxs-lookup"><span data-stu-id="ae447-104">Overview</span></span>

<span data-ttu-id="ae447-105">Microsoft Azure 流量管理員可讓您控制使用者流量，將流量分散到不同資料中心的服務端點。</span><span class="sxs-lookup"><span data-stu-id="ae447-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="ae447-106">流量管理員支援的服務端點包括 Azure VM、Web Apps 和雲端服務。</span><span class="sxs-lookup"><span data-stu-id="ae447-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="ae447-107">您也可以將流量管理員使用於外部、非 Azure 端點。</span><span class="sxs-lookup"><span data-stu-id="ae447-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="ae447-108">深入了解 [Azure 流量管理員](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。</span><span class="sxs-lookup"><span data-stu-id="ae447-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="ae447-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="ae447-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ae447-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ae447-110">Install the npm module</span></span>

<span data-ttu-id="ae447-111">安裝 Azure 流量管理員 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ae447-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="ae447-112">範例</span><span class="sxs-lookup"><span data-stu-id="ae447-112">Example</span></span>

<span data-ttu-id="ae447-113">此範例會列出指定之資源群組的所有流量管理員。</span><span class="sxs-lookup"><span data-stu-id="ae447-113">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="ae447-114">範例</span><span class="sxs-lookup"><span data-stu-id="ae447-114">Samples</span></span>

<span data-ttu-id="ae447-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ae447-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
