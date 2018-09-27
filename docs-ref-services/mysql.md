---
title: 適用於 Node.js 的 Azure MySQL 模組
description: 適用於 Node.js 的 Azure MySQL 模組參考
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47358777"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="b009f-103">適用於 Node.js 的 Azure MySQL 模組</span><span class="sxs-lookup"><span data-stu-id="b009f-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="b009f-104">用於存取 Azure Database for MySQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for MySQL 的 Node.js 連線程式庫](https://github.com/sidorares/node-mysql2)。</span><span class="sxs-lookup"><span data-stu-id="b009f-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="b009f-105">深入了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="b009f-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="b009f-106">用戶端套件</span><span class="sxs-lookup"><span data-stu-id="b009f-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b009f-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b009f-107">Install the npm module</span></span>

<span data-ttu-id="b009f-108">使用 npm 來安裝 MySQL 用戶端模組。</span><span class="sxs-lookup"><span data-stu-id="b009f-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="b009f-109">範例</span><span class="sxs-lookup"><span data-stu-id="b009f-109">Example</span></span>

<span data-ttu-id="b009f-110">此範例會連線到 MySQL 資料庫，並執行簡單查詢來擷取所有客戶。</span><span class="sxs-lookup"><span data-stu-id="b009f-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b009f-111">範例</span><span class="sxs-lookup"><span data-stu-id="b009f-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="b009f-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b009f-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
