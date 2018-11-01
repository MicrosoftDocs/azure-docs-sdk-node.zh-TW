---
title: 適用於 Node.js 的 Azure Advisor 模組
description: 適用於 Node.js 的 Azure Advisor 模組參考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50310925"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="61acd-103">適用於 Node.js 的 Azure Advisor 模組</span><span class="sxs-lookup"><span data-stu-id="61acd-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="61acd-104">概觀</span><span class="sxs-lookup"><span data-stu-id="61acd-104">Overview</span></span>

<span data-ttu-id="61acd-105">Azure 建議程式是個人化的雲端顧問，可協助您依最佳做法來最佳化您的 Azure 部署。</span><span class="sxs-lookup"><span data-stu-id="61acd-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="61acd-106">Advisor 可分析您的資源組態和使用量遙測，然後建議可協助您改善 Azure 資源的成本效益、效能、高可用性和安全性的解決方案。</span><span class="sxs-lookup"><span data-stu-id="61acd-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="61acd-107">使用 Advisor，您可以：</span><span class="sxs-lookup"><span data-stu-id="61acd-107">With Advisor, you can:</span></span>
- <span data-ttu-id="61acd-108">取得主動式、可採取動作且個人化的最佳做法建議。</span><span class="sxs-lookup"><span data-stu-id="61acd-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="61acd-109">改善資源的效能、安全性及高可用性，同時尋找降低整體 Azure 費用的機會。</span><span class="sxs-lookup"><span data-stu-id="61acd-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="61acd-110">取得內嵌了提議動作的建議。</span><span class="sxs-lookup"><span data-stu-id="61acd-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="61acd-111">管理封裝</span><span class="sxs-lookup"><span data-stu-id="61acd-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="61acd-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="61acd-112">Install the npm module</span></span>

<span data-ttu-id="61acd-113">安裝 Azure Advisor npm 模組</span><span class="sxs-lookup"><span data-stu-id="61acd-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="61acd-114">範例</span><span class="sxs-lookup"><span data-stu-id="61acd-114">Example</span></span>

<span data-ttu-id="61acd-115">此範例會顯示來自 Azure Advisor 的建議清單。</span><span class="sxs-lookup"><span data-stu-id="61acd-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="61acd-116">範例</span><span class="sxs-lookup"><span data-stu-id="61acd-116">Samples</span></span>

<span data-ttu-id="61acd-117">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="61acd-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
