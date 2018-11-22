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
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52003752"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="04def-103">適用於 Node.js 的 Azure PostgreSQL 模組</span><span class="sxs-lookup"><span data-stu-id="04def-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="04def-104">用於存取 Azure Database for PostgreSQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for PostgreSQL 的 Node.js 連線程式庫](https://www.npmjs.com/package/pg)。</span><span class="sxs-lookup"><span data-stu-id="04def-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="04def-105">此程式庫是適用於 Node.js 的非封鎖 PostgreSQL 用戶端，可支援純 JavaScript 和選擇性原生 libpq 繫結。</span><span class="sxs-lookup"><span data-stu-id="04def-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="04def-106">深入了解 [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="04def-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="04def-107">用戶端封裝</span><span class="sxs-lookup"><span data-stu-id="04def-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="04def-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="04def-108">Install the npm module</span></span>

<span data-ttu-id="04def-109">使用 npm 來安裝 PostgreSQL 用戶端模組。</span><span class="sxs-lookup"><span data-stu-id="04def-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="04def-110">範例</span><span class="sxs-lookup"><span data-stu-id="04def-110">Example</span></span>

<span data-ttu-id="04def-111">此範例會開啟用戶端連線並執行簡單的查詢。</span><span class="sxs-lookup"><span data-stu-id="04def-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="04def-112">範例</span><span class="sxs-lookup"><span data-stu-id="04def-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="04def-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="04def-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
