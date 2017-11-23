---
title: "適用於 Node.js 的 Azure DevTest Labs 模組"
description: "適用於 Node.js 的 Azure DevTest Labs 模組參考"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="2bc55-104">適用於 Node.js 的 Azure DevTest Labs 模組</span><span class="sxs-lookup"><span data-stu-id="2bc55-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2bc55-105">概觀</span><span class="sxs-lookup"><span data-stu-id="2bc55-105">Overview</span></span>

<span data-ttu-id="2bc55-106">Azure DevTest Labs 是一項服務，可協助開發人員和測試人員在 Azure 中建立快速環境，同時將浪費降至最低並控制成本。</span><span class="sxs-lookup"><span data-stu-id="2bc55-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="2bc55-107">您可以利用可重複使用的範本和構件快速佈建 Windows 和 Linux 環境，來測試最新版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2bc55-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="2bc55-108">將您的部署管線與研發/測試實驗室輕鬆整合，來佈建隨選環境。</span><span class="sxs-lookup"><span data-stu-id="2bc55-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="2bc55-109">藉由佈建多個測試代理程式來相應增加您的負載測試，並建立預先佈建的環境來進行訓練和示範。</span><span class="sxs-lookup"><span data-stu-id="2bc55-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="2bc55-110">管理套件</span><span class="sxs-lookup"><span data-stu-id="2bc55-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2bc55-111">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="2bc55-111">Install the npm module</span></span>

<span data-ttu-id="2bc55-112">安裝 Azure DevTest Labs npm 模組</span><span class="sxs-lookup"><span data-stu-id="2bc55-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="2bc55-113">範例</span><span class="sxs-lookup"><span data-stu-id="2bc55-113">Example</span></span>

<span data-ttu-id="2bc55-114">此範例會取得並列印實驗室的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2bc55-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="2bc55-115">範例</span><span class="sxs-lookup"><span data-stu-id="2bc55-115">Samples</span></span>

<span data-ttu-id="2bc55-116">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="2bc55-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
