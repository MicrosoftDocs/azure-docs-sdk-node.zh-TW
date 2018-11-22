---
title: 適用於 Node.js 的 Azure Container Registry 模組
description: 適用於 Node.js 的 Azure Container Registry 模組參考
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52155013"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="d8e08-103">適用於 Node.js 的 Azure Container Registry 模組</span><span class="sxs-lookup"><span data-stu-id="d8e08-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="d8e08-104">Azure Container Registry 是受控 Docker 登錄服務，架構於開放原始碼的 Docker Registry 2.0。</span><span class="sxs-lookup"><span data-stu-id="d8e08-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="d8e08-105">建立及維護 Azure 容器登錄庫，以儲存和管理您的私人 Docker 容器映像。</span><span class="sxs-lookup"><span data-stu-id="d8e08-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="d8e08-106">使用 Azure 的容器登錄庫進行現有容器的開發與部署管線，並利用 Docker 社群的專業知識。</span><span class="sxs-lookup"><span data-stu-id="d8e08-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="d8e08-107">管理套件</span><span class="sxs-lookup"><span data-stu-id="d8e08-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d8e08-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="d8e08-108">Install the npm module</span></span>

<span data-ttu-id="d8e08-109">安裝 Azure Container Registry npm 模組</span><span class="sxs-lookup"><span data-stu-id="d8e08-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="d8e08-110">範例</span><span class="sxs-lookup"><span data-stu-id="d8e08-110">Example</span></span>

<span data-ttu-id="d8e08-111">此範例會取得可用容器的清單。</span><span class="sxs-lookup"><span data-stu-id="d8e08-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d8e08-112">範例</span><span class="sxs-lookup"><span data-stu-id="d8e08-112">Samples</span></span>

<span data-ttu-id="d8e08-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d8e08-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
