---
title: "適用於 Node.js 的 Azure DevTest Labs 模組"
description: "適用於 Node.js 的 Azure DevTest Labs 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 7754280741c09d47e138518d33628c667944c651
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="f640f-103">適用於 Node.js 的 Azure DevTest Labs 模組</span><span class="sxs-lookup"><span data-stu-id="f640f-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="f640f-104">Azure DevTest Labs 是一項服務，可協助開發人員和測試人員在 Azure 中建立快速環境，同時將浪費降至最低並控制成本。</span><span class="sxs-lookup"><span data-stu-id="f640f-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="f640f-105">您可以利用可重複使用的範本和構件快速佈建 Windows 和 Linux 環境，來測試最新版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f640f-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="f640f-106">將您的部署管線與研發/測試實驗室輕鬆整合，來佈建隨選環境。</span><span class="sxs-lookup"><span data-stu-id="f640f-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="f640f-107">藉由佈建多個測試代理程式來相應增加您的負載測試，並建立預先佈建的環境來進行訓練和示範。</span><span class="sxs-lookup"><span data-stu-id="f640f-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="f640f-108">管理封裝</span><span class="sxs-lookup"><span data-stu-id="f640f-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f640f-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f640f-109">Install the npm module</span></span>

<span data-ttu-id="f640f-110">安裝 Azure DevTest Labs npm 模組</span><span class="sxs-lookup"><span data-stu-id="f640f-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="f640f-111">範例</span><span class="sxs-lookup"><span data-stu-id="f640f-111">Example</span></span>

<span data-ttu-id="f640f-112">此範例會取得並列印實驗室的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f640f-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f640f-113">範例</span><span class="sxs-lookup"><span data-stu-id="f640f-113">Samples</span></span>

<span data-ttu-id="f640f-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f640f-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
