---
title: "適用於 Node.js 的 Azure 通知中樞模組"
description: "適用於 Node.js 的 Azure 通知中樞模組參考"
keywords: "Azure,SDK,API,通知中樞, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="bd015-104">適用於 Node.js 的 Azure 通知中樞模組</span><span class="sxs-lookup"><span data-stu-id="bd015-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bd015-105">概觀</span><span class="sxs-lookup"><span data-stu-id="bd015-105">Overview</span></span>

<span data-ttu-id="bd015-106">Azure 通知中樞提供方便使用、多平台、可相應放大的推播引擎。</span><span class="sxs-lookup"><span data-stu-id="bd015-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="bd015-107">利用單一的跨平台 API 呼叫，您就可以輕鬆地將鎖定目標且個人化的推播通知，從任何雲端或內部部署後端傳送到任何行動平台。</span><span class="sxs-lookup"><span data-stu-id="bd015-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="bd015-108">通知中樞很適合企業和消費者案例。</span><span class="sxs-lookup"><span data-stu-id="bd015-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="bd015-109">以下是一些客戶使用通知中樞之用途的範例︰</span><span class="sxs-lookup"><span data-stu-id="bd015-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="bd015-110">傳送即時新聞通知給數百萬人，且延遲時間很低。</span><span class="sxs-lookup"><span data-stu-id="bd015-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="bd015-111">將位置型折價券傳送給感興趣的使用者區段。</span><span class="sxs-lookup"><span data-stu-id="bd015-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="bd015-112">將事件相關通知傳送給媒體/運動/財金/遊戲應用程式的使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="bd015-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="bd015-113">將促銷內容推播到應用程式來吸引客戶並進行銷售。</span><span class="sxs-lookup"><span data-stu-id="bd015-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="bd015-114">對使用者發送企業事件通知，例如新訊息和工作項目。</span><span class="sxs-lookup"><span data-stu-id="bd015-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="bd015-115">傳送 Multi-Factor Authentication 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd015-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd015-116">管理套件</span><span class="sxs-lookup"><span data-stu-id="bd015-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd015-117">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="bd015-117">Install the npm module</span></span>

<span data-ttu-id="bd015-118">安裝 Azure 通知中樞模組</span><span class="sxs-lookup"><span data-stu-id="bd015-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="bd015-119">範例</span><span class="sxs-lookup"><span data-stu-id="bd015-119">Example</span></span>

<span data-ttu-id="bd015-120">此範例會列出所有的通知中樞。</span><span class="sxs-lookup"><span data-stu-id="bd015-120">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="bd015-121">範例</span><span class="sxs-lookup"><span data-stu-id="bd015-121">Samples</span></span>

* [<span data-ttu-id="bd015-122">適用於 Node.js 後端的 App Service Mobile 快速入門</span><span class="sxs-lookup"><span data-stu-id="bd015-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="bd015-123">Azure IoT 服務在來自執行 Node.js 之 Intel Edison 的資料上偵測到的資料推文震動異常</span><span class="sxs-lookup"><span data-stu-id="bd015-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="bd015-124">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="bd015-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
