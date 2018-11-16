---
title: 適用於 Node.js 的 Azure IoT 中樞模組
description: 適用於 Node.js 的 Azure IoT 中樞模組參考
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51410412"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="e9044-103">適用於 Node.js 的 Azure IoT 中樞模組</span><span class="sxs-lookup"><span data-stu-id="e9044-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="e9044-104">Azure IoT 中樞是一項完全受控的服務，可在數百萬個 IoT 裝置和一個解決方案後端之間啟用可靠且安全的雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="e9044-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="e9044-105">Azure IoT 中樞：</span><span class="sxs-lookup"><span data-stu-id="e9044-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="e9044-106">提供多個裝置到雲端和雲端到裝置通訊選項，包括單向傳訊、檔案傳輸，以及要求-回覆方法。</span><span class="sxs-lookup"><span data-stu-id="e9044-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="e9044-107">向其他 Azure 服務提供內建宣告式訊息路由。</span><span class="sxs-lookup"><span data-stu-id="e9044-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="e9044-108">針對裝置中繼資料與同步化狀態資訊提供可查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="e9044-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="e9044-109">使用每一裝置的安全性金鑰或 X.509 憑證啟用安全通訊與存取控制。</span><span class="sxs-lookup"><span data-stu-id="e9044-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="e9044-110">可廣泛監視裝置的連線情況和裝置的身分識別管理事件。</span><span class="sxs-lookup"><span data-stu-id="e9044-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="e9044-111">包括適用於最受歡迎的語言和平台的裝置程式庫。</span><span class="sxs-lookup"><span data-stu-id="e9044-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="e9044-112">使用 npm 來安裝 Node.js 的 Azure IoT 中樞模組</span><span class="sxs-lookup"><span data-stu-id="e9044-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="e9044-113">管理套件</span><span class="sxs-lookup"><span data-stu-id="e9044-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e9044-114">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="e9044-114">Install the npm module</span></span>

<span data-ttu-id="e9044-115">安裝 Azure IoT 中樞 npm 模組</span><span class="sxs-lookup"><span data-stu-id="e9044-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="e9044-116">範例</span><span class="sxs-lookup"><span data-stu-id="e9044-116">Example</span></span>

<span data-ttu-id="e9044-117">此範例會建立並命名 IoT 中樞。</span><span class="sxs-lookup"><span data-stu-id="e9044-117">This example creates and names an IoT hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

<span data-ttu-id="e9044-118">此範例會取得現有的 IoT 中樞中 (依名稱排列)。</span><span class="sxs-lookup"><span data-stu-id="e9044-118">This example gets the existing IoT hub, by name.</span></span>

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a><span data-ttu-id="e9044-119">範例</span><span class="sxs-lookup"><span data-stu-id="e9044-119">Samples</span></span>

- [<span data-ttu-id="e9044-120">開始使用 Raspberry Pi Azure IoT 入門套件</span><span class="sxs-lookup"><span data-stu-id="e9044-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="e9044-121">Azure IoT 服務在來自執行 Node.js 之 Intel Edison 的資料上偵測到的資料推文震動異常</span><span class="sxs-lookup"><span data-stu-id="e9044-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="e9044-122">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="e9044-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
