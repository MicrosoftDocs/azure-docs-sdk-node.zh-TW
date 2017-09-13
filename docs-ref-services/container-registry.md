---
title: "適用於 Node.js 的 Azure Container Registry 模組"
description: "適用於 Node.js 的 Azure Container Registry 模組參考"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="f7b23-104">適用於 Node.js 的 Azure Container Registry 模組</span><span class="sxs-lookup"><span data-stu-id="f7b23-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f7b23-105">概觀</span><span class="sxs-lookup"><span data-stu-id="f7b23-105">Overview</span></span>

<span data-ttu-id="f7b23-106">Azure Container Registry 是受管理的 Docker 登錄服務，架構於開放原始碼的 Docker Registry 2.0。</span><span class="sxs-lookup"><span data-stu-id="f7b23-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="f7b23-107">建立及維護 Azure 容器登錄庫，以儲存和管理您的私人 Docker 容器映像。</span><span class="sxs-lookup"><span data-stu-id="f7b23-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="f7b23-108">使用 Azure 的容器登錄庫進行現有容器的開發與部署管線，並利用 Docker 社群的專業知識。</span><span class="sxs-lookup"><span data-stu-id="f7b23-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="f7b23-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="f7b23-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f7b23-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f7b23-110">Install the npm module</span></span>

<span data-ttu-id="f7b23-111">安裝 Azure Container Registry npm 模組</span><span class="sxs-lookup"><span data-stu-id="f7b23-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="f7b23-112">範例</span><span class="sxs-lookup"><span data-stu-id="f7b23-112">Example</span></span>

<span data-ttu-id="f7b23-113">此範例會取得可用容器的清單。</span><span class="sxs-lookup"><span data-stu-id="f7b23-113">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="f7b23-114">範例</span><span class="sxs-lookup"><span data-stu-id="f7b23-114">Samples</span></span>

<span data-ttu-id="f7b23-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f7b23-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
