---
title: 適用於 Node.js 的 Azure 通知中樞模組
description: 適用於 Node.js 的 Azure 通知中樞模組參考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 30b8caa07111f9ceb5fa58f92649e4670aa6bee6
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>適用於 Node.js 的 Azure 通知中樞模組

Azure 通知中樞提供方便使用、多平台、可相應放大的推播引擎。 利用單一的跨平台 API 呼叫，您就可以輕鬆地將鎖定目標且個人化的推播通知，從任何雲端或內部部署後端傳送到任何行動平台。

通知中樞很適合企業和消費者案例。 以下是一些客戶使用通知中樞之用途的範例︰
- 傳送即時新聞通知給數百萬人，且延遲時間很低。
- 將位置型折價券傳送給感興趣的使用者區段。
- 將事件相關通知傳送給媒體/運動/財金/遊戲應用程式的使用者或群組。
- 將促銷內容推播到應用程式來吸引客戶並進行銷售。
- 對使用者發送企業事件通知，例如新訊息和工作項目。
- 傳送 Multi-Factor Authentication 的程式碼。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 通知中樞模組 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>範例

此範例會列出所有的通知中樞。

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

## <a name="samples"></a>範例

* [適用於 Node.js 後端的 App Service Mobile 快速入門](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Azure IoT 服務在來自執行 Node.js 之 Intel Edison 的資料上偵測到的資料推文震動異常](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
