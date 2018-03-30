---
title: 適用於 Node.js 的 Azure Cosmos DB 模組
description: 適用於 Node.js 的 Azure Cosmos DB 模組參考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 02d4729d72cba8628ac98de0bf41c30f54c75e85
ms.sourcegitcommit: 178734fbd3784ade4d8bdb5141be6d7ca7e017f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="fdcde-103">適用於 Node.js 的 Azure Cosmos DB 模組</span><span class="sxs-lookup"><span data-stu-id="fdcde-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="fdcde-104">Azure Cosmos DB 是 Microsoft 的全球散發多模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="fdcde-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="fdcde-105">Azure Cosmos DB 可讓您有彈性且獨立地跨任意數目的 Azure 地理區域調整輸送量和儲存體。</span><span class="sxs-lookup"><span data-stu-id="fdcde-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="fdcde-106">它利用完整的服務等級協定 (SLA) 提供了輸送量、延遲、可用性和一致性的保證，這是其他資料庫服務無法提供的。</span><span class="sxs-lookup"><span data-stu-id="fdcde-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="fdcde-107">Azure Cosmos DB 包含已最佳化寫入、已管理資源、無結構描述的資料庫引擎，它原生支援多重資料模型：機碼值、文件、圖形和單欄式。</span><span class="sxs-lookup"><span data-stu-id="fdcde-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="fdcde-108">它也支援許多以可延伸的方式用來存取資料的 API，包括 MongoDB、SQL、Gremlin/Graph、Azure 資料表以及 Cassandra (預覽版)。</span><span class="sxs-lookup"><span data-stu-id="fdcde-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="fdcde-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="fdcde-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fdcde-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="fdcde-110">Install the npm module</span></span> 

<span data-ttu-id="fdcde-111">安裝 Azure Cosmos DB npm 模組。</span><span class="sxs-lookup"><span data-stu-id="fdcde-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="fdcde-112">範例</span><span class="sxs-lookup"><span data-stu-id="fdcde-112">Example</span></span>

<span data-ttu-id="fdcde-113">此範例會列出所有的 Azure Cosmos DB 帳戶。</span><span class="sxs-lookup"><span data-stu-id="fdcde-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fdcde-114">範例</span><span class="sxs-lookup"><span data-stu-id="fdcde-114">Samples</span></span>

* [<span data-ttu-id="fdcde-115">使用 Azure Cosmos DB 開發 Node.js 應用程式</span><span class="sxs-lookup"><span data-stu-id="fdcde-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="fdcde-116">使用 Azure Cosmos DB 開發 Node.js 應用程式 - Gremlin</span><span class="sxs-lookup"><span data-stu-id="fdcde-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="fdcde-117">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="fdcde-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
