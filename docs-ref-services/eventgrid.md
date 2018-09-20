---
title: 適用於 Node.js 的 Azure Event Grid 程式庫
description: 適用於 Node.js 的 Azure Event Grid 程式庫參考
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: f830f2f37429b32bbcfa856ad82a817ae2658341
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46275719"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>適用於 Node.js 的 Azure Event Grid 程式庫

建置事件導向的應用程式會傾聽並回應來自 Azure 服務和自訂來源的事件，這些事件會使用由 Azure Event Grid 處理的簡單型事件。

[進一步了解 ](/azure/event-grid/overview)Azure Event Grid 的相關資訊，並參考 [Azure Blob 儲存體教學課程](/azure/storage/blobs/storage-blob-event-quickstart)開始使用。 

## <a name="publish-sdk"></a>發佈 SDK

使用 Azure Event Grid 發佈 SDK 來建立事件、驗證並發佈至主題。

### <a name="installation"></a>安裝

使用 npm 將模組新增到您的專案中：

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>程式碼範例

下列程式碼片段會將模擬事件發佈至 Event Grid 主題。 您可以從 Azure 入口網站或透過 Azure CLI，擷取端點和主題存取金鑰：

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

此範例顯示如何從 Azure 儲存體處理事件：

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [探索用戶端 API](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>管理 SDK

透過管理 SDK 來建立、更新或刪除 Event Grid 執行個體、主題和訂用帳戶。

### <a name="installation"></a>安裝

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>程式碼範例

下列程式碼會建立 Event Grid 主題 `topic1`，並傳回與新建立主題相關聯的存取金鑰。

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [探索管理 API](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>深入了解

- [使用 Event Grid SDK 接收事件](/azure/event-grid/receive-events)
