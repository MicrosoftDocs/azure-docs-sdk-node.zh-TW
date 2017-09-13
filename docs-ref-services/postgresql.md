---
title: "適用於 Node.js 的 Azure PostgreSQL 模組"
description: "適用於 Node.js 的 Azure PostgreSQL 模組參考"
keywords: "Azure, Node, SDK, API, nodejs, javascript, 資料庫, PostgreSQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a>適用於 Node.js 的 Azure PostgreSQL 模組

## <a name="overview"></a>概觀

用於存取 Azure Database for PostgreSQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for PostgreSQL 的 Node.js 連線程式庫](https://www.npmjs.com/package/pg)。 此程式庫是適用於 Node.js 的非封鎖 PostgreSQL 用戶端，可支援純 JavaScript 和選擇性原生 libpq 繫結。

深入了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>用戶端套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝 PostgreSQL 用戶端模組。

```bash
npm install pg
```   

### <a name="example"></a>範例

此範例會開啟用戶端連線並執行簡單的查詢。

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>範例

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
