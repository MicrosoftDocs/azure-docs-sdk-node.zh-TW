---
title: "適用於 Node.js 的 Azure MySQL 模組"
description: "適用於 Node.js 的 Azure MySQL 模組參考"
keywords: "Azure, Node, SDK, API, nodejs, javascript, 資料庫, MySQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="e7a90-104">適用於 Node.js 的 Azure MySQL 模組</span><span class="sxs-lookup"><span data-stu-id="e7a90-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e7a90-105">概觀</span><span class="sxs-lookup"><span data-stu-id="e7a90-105">Overview</span></span>

<span data-ttu-id="e7a90-106">用於存取 Azure Database for MySQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for MySQL 的 Node.js 連線程式庫](https://github.com/sidorares/node-mysql2)。</span><span class="sxs-lookup"><span data-stu-id="e7a90-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="e7a90-107">深入了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="e7a90-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="e7a90-108">用戶端套件</span><span class="sxs-lookup"><span data-stu-id="e7a90-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e7a90-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="e7a90-109">Install the npm module</span></span>

<span data-ttu-id="e7a90-110">使用 npm 來安裝 MySQL 用戶端模組。</span><span class="sxs-lookup"><span data-stu-id="e7a90-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="e7a90-111">範例</span><span class="sxs-lookup"><span data-stu-id="e7a90-111">Example</span></span>

<span data-ttu-id="e7a90-112">此範例會連線到 MySQL 資料庫，並執行簡單查詢來擷取所有客戶。</span><span class="sxs-lookup"><span data-stu-id="e7a90-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a><span data-ttu-id="e7a90-113">範例</span><span class="sxs-lookup"><span data-stu-id="e7a90-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="e7a90-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="e7a90-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
