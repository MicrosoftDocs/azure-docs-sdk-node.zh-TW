---
title: 適用於 Node.js 的 Azure 自動化模組
description: 適用於 Node.js 的 Azure 自動化模組參考
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "49779249"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="19d06-103">適用於 Node.js 的 Azure 自動化模組</span><span class="sxs-lookup"><span data-stu-id="19d06-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="19d06-104">概觀</span><span class="sxs-lookup"><span data-stu-id="19d06-104">Overview</span></span>

<span data-ttu-id="19d06-105">Azure 自動化可讓使用者將雲端和企業環境中執行的手動、長時間執行、易發生錯誤且重複性高的工作加以自動化。</span><span class="sxs-lookup"><span data-stu-id="19d06-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="19d06-106">自動化可以節省時間並提高日常管理工作的可靠性，甚至將它們排程為定期自動執行。</span><span class="sxs-lookup"><span data-stu-id="19d06-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="19d06-107">您可以使用 Runbook 自動執行程序，或使用「期望狀態設定」自動進行組態管理。</span><span class="sxs-lookup"><span data-stu-id="19d06-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="19d06-108">管理封裝</span><span class="sxs-lookup"><span data-stu-id="19d06-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="19d06-109">使用 npm 安裝模組</span><span class="sxs-lookup"><span data-stu-id="19d06-109">Install the modules with npm</span></span>

<span data-ttu-id="19d06-110">使用 npm 來安裝適用於 Node.js 的 Azure 自動化模組</span><span class="sxs-lookup"><span data-stu-id="19d06-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="19d06-111">範例</span><span class="sxs-lookup"><span data-stu-id="19d06-111">Example</span></span>

<span data-ttu-id="19d06-112">此範例會列出自動化帳戶。</span><span class="sxs-lookup"><span data-stu-id="19d06-112">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="19d06-113">範例</span><span class="sxs-lookup"><span data-stu-id="19d06-113">Samples</span></span>

<span data-ttu-id="19d06-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="19d06-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
