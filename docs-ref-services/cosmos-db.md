---
title: 適用於 Node.js 的 Azure Cosmos DB 模組
description: 適用於 Node.js 的 Azure Cosmos DB 模組參考
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 4064f9f6c0e1369c8d6261a70709102e7492b340
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260754"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>適用於 Node.js 的 Azure Cosmos DB 模組

Azure Cosmos DB 是 Microsoft 的全球散發多模型資料庫。 Azure Cosmos DB 可讓您有彈性且獨立地跨任意數目的 Azure 地理區域調整輸送量和儲存體。 它利用完整的服務等級協定 (SLA) 提供了輸送量、延遲、可用性和一致性的保證，這是其他資料庫服務無法提供的。

Azure Cosmos DB 包含已最佳化寫入、已管理資源、無結構描述的資料庫引擎，它原生支援多重資料模型：機碼值、文件、圖形和單欄式。 它也支援許多以可延伸的方式用來存取資料的 API，包括 MongoDB、SQL、Gremlin/Graph、Azure 資料表以及 Cassandra (預覽版)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組 

安裝 Azure Cosmos DB npm 模組。

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>範例

此範例會列出所有的 Azure Cosmos DB 帳戶。

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a>範例

* [使用 Azure Cosmos DB 開發 Node.js 應用程式](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [使用 Azure Cosmos DB 開發 Node.js 應用程式 - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
