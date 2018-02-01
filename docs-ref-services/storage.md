---
title: "適用於 Node.js 的 Azure 儲存體模組"
description: "適用於 Node.js 的 Azure 儲存體模組參考"
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
---
# <a name="azure-storage-modules-for-nodejs"></a>適用於 Node.js 的 Azure 儲存體模組

使用 Azure 儲存體用戶端模組：

- 從 [Azure Blob 儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)讀取和寫入物件及檔案
- 使用 [Azure 佇列儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)在雲端連線的應用程式之間傳送和接收訊息
- 使用 [Azure 資料表儲存體](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)讀取及寫入大型的結構化資料

使用管理模組來建立、更新和管理 Azure 儲存體帳戶，並從 Node.js 應用程式查詢及重新產生存取金鑰。

## <a name="client-package"></a>用戶端套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 儲存體用戶端 npm 模組

```bash
npm install azure-storage
```

### <a name="example"></a>範例

此範例會建立儲存體容器，並將本機檔案 `data.txt` 上傳至該容器。

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

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組 

安裝 Azure 儲存體管理 npm 模組

```bash
npm install azure-arm-storage
```

### <a name="example"></a>範例

此範例會列出儲存體帳戶。

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

## <a name="samples"></a>範例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
