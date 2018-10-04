---
title: 適用於 Node.js 的 Azure PostgreSQL 模組
description: 適用於 Node.js 的 Azure PostgreSQL 模組參考
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48514666"
---
# <a name="azure-postgresql-modules-for-nodejs"></a>適用於 Node.js 的 Azure PostgreSQL 模組

用於存取 Azure Database for PostgreSQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for PostgreSQL 的 Node.js 連線程式庫](https://www.npmjs.com/package/pg)。 此程式庫是適用於 Node.js 的非封鎖 PostgreSQL 用戶端，可支援純 JavaScript 和選擇性原生 libpq 繫結。

深入了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>用戶端封裝

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
