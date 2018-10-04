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
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48425746"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="08a26-103">適用於 Node.js 的 Azure Event Grid 程式庫</span><span class="sxs-lookup"><span data-stu-id="08a26-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="08a26-104">建置事件導向的應用程式會傾聽並回應來自 Azure 服務和自訂來源的事件，這些事件會使用由 Azure Event Grid 處理的簡單型事件。</span><span class="sxs-lookup"><span data-stu-id="08a26-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="08a26-105">[進一步了解 ](/azure/event-grid/overview)Azure Event Grid 的相關資訊，並參考 [Azure Blob 儲存體教學課程](/azure/storage/blobs/storage-blob-event-quickstart)開始使用。</span><span class="sxs-lookup"><span data-stu-id="08a26-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="08a26-106">發佈 SDK</span><span class="sxs-lookup"><span data-stu-id="08a26-106">Publish SDK</span></span>

<span data-ttu-id="08a26-107">使用 Azure Event Grid 發佈 SDK 來建立事件、驗證並發佈至主題。</span><span class="sxs-lookup"><span data-stu-id="08a26-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="08a26-108">安裝</span><span class="sxs-lookup"><span data-stu-id="08a26-108">Installation</span></span>

<span data-ttu-id="08a26-109">使用 npm 將模組新增到您的專案中：</span><span class="sxs-lookup"><span data-stu-id="08a26-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="08a26-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="08a26-110">Example code</span></span>

<span data-ttu-id="08a26-111">下列程式碼片段會將模擬事件發佈至 Event Grid 主題。</span><span class="sxs-lookup"><span data-stu-id="08a26-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="08a26-112">您可以從 Azure 入口網站或透過 Azure CLI，擷取端點和主題存取金鑰：</span><span class="sxs-lookup"><span data-stu-id="08a26-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

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

<span data-ttu-id="08a26-113">此範例顯示如何從 Azure 儲存體處理事件：</span><span class="sxs-lookup"><span data-stu-id="08a26-113">This sample shows how to handle an event from Azure Storage:</span></span>

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
> [<span data-ttu-id="08a26-114">探索用戶端 API</span><span class="sxs-lookup"><span data-stu-id="08a26-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="08a26-115">管理 SDK</span><span class="sxs-lookup"><span data-stu-id="08a26-115">Management SDK</span></span>

<span data-ttu-id="08a26-116">透過管理 SDK 來建立、更新或刪除 Event Grid 執行個體、主題和訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="08a26-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="08a26-117">安裝</span><span class="sxs-lookup"><span data-stu-id="08a26-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="08a26-118">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="08a26-118">Example code</span></span>

<span data-ttu-id="08a26-119">下列程式碼會建立 Event Grid 主題 `topic1`，並傳回與新建立主題相關聯的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="08a26-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

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
> [<span data-ttu-id="08a26-120">探索管理 API</span><span class="sxs-lookup"><span data-stu-id="08a26-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="08a26-121">深入了解</span><span class="sxs-lookup"><span data-stu-id="08a26-121">Learn more</span></span>

- [<span data-ttu-id="08a26-122">使用 Event Grid SDK 接收事件</span><span class="sxs-lookup"><span data-stu-id="08a26-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
