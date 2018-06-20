---
title: 適用於 Node.js 的 Azure 快取模組
description: 適用於 Node.js 的 Azure 快取模組參考
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265059"
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>適用於 Node.js 的 Azure 快取模組

Azure Redis 快取是以常用的開放原始碼 Redis 專案作為基礎。 它可讓您從 Azure 應用程式存取由 Microsoft 管理的安全、專用 Redis 執行個體。

Redis 是一種進階的索引鍵值存放區，其中的索引鍵可以包含類似字串、雜湊、清單、集合和排序的集合等資料結構。 Redis 針對這些資料類型支援一組不可部分完成的操作。

深入了解 [Azure Redis 快取](https://docs.microsoft.com/azure/redis-cache/)。

## <a name="client-package"></a>用戶端封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝適用於 Node.js 的 Redis 模組

```bash
npm install redis
```

### <a name="example"></a>範例

此範例會連線到 Azure Redis 快取執行個體、儲存索引鍵/值組，然後依其索引鍵讀取所儲存的值。

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝適用於 Node.js 的 Azure Redis 快取模組

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>範例

此範例會向 Azure 驗證，並列出指定之源群組中的所有 Redis 快取執行個體。

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a>範例

* [如何搭配使用 Azure Redis 快取與 Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
