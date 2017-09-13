---
title: "適用於 Node.js 的 Azure SQL 模組"
description: "適用於 Node.js 的 Azure SQL 模組參考"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a>適用於 Node.js 的 Azure SQL 模組

## <a name="overview"></a>概觀

從 Node.js 使用儲存在 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) 中的資料。
管理程式庫提供的介面，可讓您輕鬆地管理 Microsoft Azure SQL 資料庫。

## <a name="client-package"></a>用戶端套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 SQL Server 用戶端 npm 模組

```bash
npm install tedious
```

### <a name="example"></a>範例

此範例會連線到 SQL Server 資料庫並執行簡單查詢。

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

## <a name="management-package"></a>管理套件

### <a name="install-npm-modules"></a>安裝 npm 模組

安裝 Azure SQL Server 管理 npm 模組

```
npm install azure-arm-sql
```   

### <a name="example"></a>範例

驗證、建立用戶端，並列出所有伺服器。

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

## <a name="samples"></a>範例

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
