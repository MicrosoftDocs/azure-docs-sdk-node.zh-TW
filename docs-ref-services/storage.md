---
title: 適用於 Node.js 的 Azure 儲存體模組
description: 適用於 Node.js 的 Azure 儲存體模組參考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116893"
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="46c9e-103">適用於 Node.js 的 Azure 儲存體模組</span><span class="sxs-lookup"><span data-stu-id="46c9e-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="46c9e-104">使用 Azure 儲存體用戶端模組：</span><span class="sxs-lookup"><span data-stu-id="46c9e-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="46c9e-105">從 [Azure Blob 儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)讀取和寫入物件及檔案</span><span class="sxs-lookup"><span data-stu-id="46c9e-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="46c9e-106">使用 [Azure 佇列儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)在雲端連線的應用程式之間傳送和接收訊息</span><span class="sxs-lookup"><span data-stu-id="46c9e-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="46c9e-107">使用 [Azure 資料表儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)讀取及寫入大型的結構化資料</span><span class="sxs-lookup"><span data-stu-id="46c9e-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="46c9e-108">使用管理模組來建立、更新和管理 Azure 儲存體帳戶，並從 Node.js 應用程式查詢及重新產生存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="46c9e-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="46c9e-109">用戶端套件</span><span class="sxs-lookup"><span data-stu-id="46c9e-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="46c9e-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="46c9e-110">Install the npm module</span></span>

<span data-ttu-id="46c9e-111">安裝 Azure 儲存體用戶端 npm 模組</span><span class="sxs-lookup"><span data-stu-id="46c9e-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="46c9e-112">範例</span><span class="sxs-lookup"><span data-stu-id="46c9e-112">Example</span></span>

<span data-ttu-id="46c9e-113">此範例會建立儲存體容器，並將本機檔案 `data.txt` 上傳至該容器。</span><span class="sxs-lookup"><span data-stu-id="46c9e-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a><span data-ttu-id="46c9e-114">管理套件</span><span class="sxs-lookup"><span data-stu-id="46c9e-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="46c9e-115">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="46c9e-115">Install the npm module</span></span> 

<span data-ttu-id="46c9e-116">安裝 Azure 儲存體管理 npm 模組</span><span class="sxs-lookup"><span data-stu-id="46c9e-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="46c9e-117">範例</span><span class="sxs-lookup"><span data-stu-id="46c9e-117">Example</span></span>

<span data-ttu-id="46c9e-118">此範例會列出儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="46c9e-118">This example list the storage accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="46c9e-119">範例</span><span class="sxs-lookup"><span data-stu-id="46c9e-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="46c9e-120">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="46c9e-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
