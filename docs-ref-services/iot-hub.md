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
ms.openlocfilehash: 77dd4c30da43af7cace048b43b7997fb1952abf1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>適用於 Node.js 的 Azure IoT 中樞模組

Azure IoT 中樞是一項完全受控的服務，可在數百萬個 IoT 裝置和一個解決方案後端之間啟用可靠且安全的雙向通訊。 Azure IoT 中樞：
- 提供多個裝置到雲端和雲端到裝置通訊選項，包括單向傳訊、檔案傳輸，以及要求-回覆方法。
- 向其他 Azure 服務提供內建宣告式訊息路由。
- 針對裝置中繼資料與同步化狀態資訊提供可查詢存放區。
- 使用每一裝置的安全性金鑰或 X.509 憑證啟用安全通訊與存取控制。
- 可廣泛監視裝置的連線情況和裝置的身分識別管理事件。
- 包括適用於最受歡迎的語言和平台的裝置程式庫。

使用 npm 來安裝 Node.js 的 Azure IoT 中樞模組

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure IoT 中樞 npm 模組

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>範例

此範例會建立並命名 IoT 中樞。

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

此範例會取得現有的 IoT 中樞中 (依名稱排列)。

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

## <a name="samples"></a>範例

- [開始使用 Raspberry Pi Azure IoT 入門套件](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Azure IoT 服務在來自執行 Node.js 之 Intel Edison 的資料上偵測到的資料推文震動異常](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
