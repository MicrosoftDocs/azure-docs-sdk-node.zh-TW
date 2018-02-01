---
title: "適用於 Node.js 的 Azure SQL 模組"
description: "適用於 Node.js 的 Azure SQL 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 8ebcfbcbf39def1774a702c9f18a4e3f5ab86931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="5d704-103">適用於 Node.js 的 Azure SQL 模組</span><span class="sxs-lookup"><span data-stu-id="5d704-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="5d704-104">從 Node.js 使用儲存在 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) 中的資料。</span><span class="sxs-lookup"><span data-stu-id="5d704-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="5d704-105">管理程式庫提供的介面，可讓您輕鬆地管理 Microsoft Azure SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5d704-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="5d704-106">用戶端封裝</span><span class="sxs-lookup"><span data-stu-id="5d704-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5d704-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="5d704-107">Install the npm module</span></span>

<span data-ttu-id="5d704-108">安裝 SQL Server 用戶端 npm 模組</span><span class="sxs-lookup"><span data-stu-id="5d704-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="5d704-109">範例</span><span class="sxs-lookup"><span data-stu-id="5d704-109">Example</span></span>

<span data-ttu-id="5d704-110">此範例會連線到 SQL Server 資料庫並執行簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="5d704-110">This example connects to a SQL Server database and perform a simple query.</span></span>

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a><span data-ttu-id="5d704-111">管理封裝</span><span class="sxs-lookup"><span data-stu-id="5d704-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="5d704-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="5d704-112">Install npm modules</span></span>

<span data-ttu-id="5d704-113">安裝 Azure SQL Server 管理 npm 模組</span><span class="sxs-lookup"><span data-stu-id="5d704-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="5d704-114">範例</span><span class="sxs-lookup"><span data-stu-id="5d704-114">Example</span></span>

<span data-ttu-id="5d704-115">驗證、建立用戶端，並列出所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="5d704-115">Authenticate, create a client, and list all servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="5d704-116">範例</span><span class="sxs-lookup"><span data-stu-id="5d704-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="5d704-117">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="5d704-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
