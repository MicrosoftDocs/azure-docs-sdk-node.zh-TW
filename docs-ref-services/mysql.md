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
# <a name="azure-mysql-modules-for-nodejs"></a>適用於 Node.js 的 Azure MySQL 模組

## <a name="overview"></a>概觀

用於存取 Azure Database for MySQL 的建議用戶端程式庫是開放原始碼之 [Azure Database for MySQL 的 Node.js 連線程式庫](https://github.com/sidorares/node-mysql2)。 

深入了解 [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>用戶端套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝 MySQL 用戶端模組。

```bash
npm install mysql2
```   

### <a name="example"></a>範例

此範例會連線到 MySQL 資料庫，並執行簡單查詢來擷取所有客戶。

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

## <a name="samples"></a>範例

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
