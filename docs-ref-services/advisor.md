---
title: "適用於 Node.js 的 Azure Advisor 模組"
description: "適用於 Node.js 的 Azure Advisor 模組參考"
keywords: Azure,SDK,API,Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="cbaca-104">適用於 Node.js 的 Azure Advisor 模組</span><span class="sxs-lookup"><span data-stu-id="cbaca-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="cbaca-105">概觀</span><span class="sxs-lookup"><span data-stu-id="cbaca-105">Overview</span></span>

<span data-ttu-id="cbaca-106">Azure 建議程式是個人化的雲端顧問，可協助您依最佳做法來最佳化您的 Azure 部署。</span><span class="sxs-lookup"><span data-stu-id="cbaca-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="cbaca-107">Advisor 可分析您的資源組態和使用量遙測，然後建議可協助您改善 Azure 資源的成本效益、效能、高可用性和安全性的解決方案。</span><span class="sxs-lookup"><span data-stu-id="cbaca-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="cbaca-108">使用 Advisor，您可以：</span><span class="sxs-lookup"><span data-stu-id="cbaca-108">With Advisor, you can:</span></span>
- <span data-ttu-id="cbaca-109">取得主動式、可採取動作且個人化的最佳做法建議。</span><span class="sxs-lookup"><span data-stu-id="cbaca-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="cbaca-110">改善資源的效能、安全性及高可用性，同時尋找降低整體 Azure 費用的機會。</span><span class="sxs-lookup"><span data-stu-id="cbaca-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="cbaca-111">取得內嵌了提議動作的建議。</span><span class="sxs-lookup"><span data-stu-id="cbaca-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="cbaca-112">管理套件</span><span class="sxs-lookup"><span data-stu-id="cbaca-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cbaca-113">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="cbaca-113">Install the npm module</span></span>

<span data-ttu-id="cbaca-114">安裝 Azure Advisor npm 模組</span><span class="sxs-lookup"><span data-stu-id="cbaca-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="cbaca-115">範例</span><span class="sxs-lookup"><span data-stu-id="cbaca-115">Example</span></span>

<span data-ttu-id="cbaca-116">此範例會顯示來自 Azure Advisor 的建議清單。</span><span class="sxs-lookup"><span data-stu-id="cbaca-116">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="cbaca-117">範例</span><span class="sxs-lookup"><span data-stu-id="cbaca-117">Samples</span></span>

<span data-ttu-id="cbaca-118">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="cbaca-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
