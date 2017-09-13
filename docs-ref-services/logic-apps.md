---
title: "適用於 Node.js 的 Azure Logic Apps 模組"
description: "適用於 Node.js 的 Azure Logic Apps 模組參考"
keywords: Azure,SDK,API,Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="7710d-104">適用於 Node.js 的 Azure Logic Apps 模組</span><span class="sxs-lookup"><span data-stu-id="7710d-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7710d-105">概觀</span><span class="sxs-lookup"><span data-stu-id="7710d-105">Overview</span></span>
<span data-ttu-id="7710d-106">Logic Apps 提供簡化和實作雲端中可擴充整合和工作流程的途徑。</span><span class="sxs-lookup"><span data-stu-id="7710d-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="7710d-107">它提供視覺化設計工具，以一系列的步驟 (也稱為工作流程) 為您的程序建立模型並加以自動化。</span><span class="sxs-lookup"><span data-stu-id="7710d-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="7710d-108">雲端和內部部署中有 許多連接器可快速整合各項服務和通訊協定。</span><span class="sxs-lookup"><span data-stu-id="7710d-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="7710d-109">邏輯應用程式是以觸發程序為開端 (如「當帳戶新增至 Dynamics CRM 時」)，而在觸發後可以開始處理各種組合的動作、轉換和條件邏輯。</span><span class="sxs-lookup"><span data-stu-id="7710d-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="7710d-110">使用 Logic Apps 的優點包括︰</span><span class="sxs-lookup"><span data-stu-id="7710d-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="7710d-111">使用易於了解的設計工具來設計複雜程序以節省時間</span><span class="sxs-lookup"><span data-stu-id="7710d-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="7710d-112">順暢地實作難以在程式碼中實作的模式和工作流程。</span><span class="sxs-lookup"><span data-stu-id="7710d-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="7710d-113">從範本快速開始使用</span><span class="sxs-lookup"><span data-stu-id="7710d-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="7710d-114">使用自己的自訂 API、程式碼和動作來自訂邏輯應用程式</span><span class="sxs-lookup"><span data-stu-id="7710d-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="7710d-115">連接並同步處理跨內部部署與雲端的不同系統</span><span class="sxs-lookup"><span data-stu-id="7710d-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="7710d-116">利用頂級整合支援打造 BizTalk Server、API 管理、Azure Functions 和 Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="7710d-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="7710d-117">Logic Apps 是完全受管理的 iPaaS (整合平台即服務)，可讓開發人員不必擔心建置裝載、延展性、可用性和管理。</span><span class="sxs-lookup"><span data-stu-id="7710d-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="7710d-118">邏輯應用程式會自動相應增加以滿足需求。</span><span class="sxs-lookup"><span data-stu-id="7710d-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="7710d-119">管理套件</span><span class="sxs-lookup"><span data-stu-id="7710d-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7710d-120">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="7710d-120">Install the npm module</span></span>

<span data-ttu-id="7710d-121">安裝適用於 Node.js 的 Azure 邏輯模組</span><span class="sxs-lookup"><span data-stu-id="7710d-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="7710d-122">範例</span><span class="sxs-lookup"><span data-stu-id="7710d-122">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="7710d-123">範例</span><span class="sxs-lookup"><span data-stu-id="7710d-123">Samples</span></span>

<span data-ttu-id="7710d-124">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="7710d-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
