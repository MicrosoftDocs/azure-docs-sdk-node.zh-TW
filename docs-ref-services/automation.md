---
title: "適用於 Node.js 的 Azure 自動化模組"
description: "適用於 Node.js 的 Azure 自動化模組參考"
keywords: "Azure,SDK,API,自動化, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="df764-104">適用於 Node.js 的 Azure 自動化模組</span><span class="sxs-lookup"><span data-stu-id="df764-104">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="df764-105">概觀</span><span class="sxs-lookup"><span data-stu-id="df764-105">Overview</span></span>

<span data-ttu-id="df764-106">Azure 自動化可讓使用者將雲端和企業環境中執行的手動、長時間執行、易發生錯誤且重複性高的工作加以自動化。</span><span class="sxs-lookup"><span data-stu-id="df764-106">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="df764-107">自動化可以節省時間並提高日常管理工作的可靠性，甚至將它們排程為定期自動執行。</span><span class="sxs-lookup"><span data-stu-id="df764-107">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="df764-108">您可以使用 Runbook 自動執行程序，或使用「期望狀態設定」自動進行組態管理。</span><span class="sxs-lookup"><span data-stu-id="df764-108">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="df764-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="df764-109">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="df764-110">使用 npm 安裝模組</span><span class="sxs-lookup"><span data-stu-id="df764-110">Install the modules with npm</span></span>

<span data-ttu-id="df764-111">使用 npm 來安裝適用於 Node.js 的 Azure 自動化模組</span><span class="sxs-lookup"><span data-stu-id="df764-111">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="df764-112">範例</span><span class="sxs-lookup"><span data-stu-id="df764-112">Example</span></span>

<span data-ttu-id="df764-113">此範例會列出自動化帳戶。</span><span class="sxs-lookup"><span data-stu-id="df764-113">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="df764-114">範例</span><span class="sxs-lookup"><span data-stu-id="df764-114">Samples</span></span>

<span data-ttu-id="df764-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="df764-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
