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
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="9b411-103">適用於 Node.js 的 Azure 快取模組</span><span class="sxs-lookup"><span data-stu-id="9b411-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="9b411-104">Azure Redis 快取是以常用的開放原始碼 Redis 專案作為基礎。</span><span class="sxs-lookup"><span data-stu-id="9b411-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="9b411-105">它可讓您從 Azure 應用程式存取由 Microsoft 管理的安全、專用 Redis 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b411-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="9b411-106">Redis 是一種進階的索引鍵值存放區，其中的索引鍵可以包含類似字串、雜湊、清單、集合和排序的集合等資料結構。</span><span class="sxs-lookup"><span data-stu-id="9b411-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="9b411-107">Redis 針對這些資料類型支援一組不可部分完成的操作。</span><span class="sxs-lookup"><span data-stu-id="9b411-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="9b411-108">深入了解 [Azure Redis 快取](https://docs.microsoft.com/azure/redis-cache/)。</span><span class="sxs-lookup"><span data-stu-id="9b411-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="9b411-109">用戶端封裝</span><span class="sxs-lookup"><span data-stu-id="9b411-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9b411-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="9b411-110">Install the npm module</span></span>

<span data-ttu-id="9b411-111">使用 npm 來安裝適用於 Node.js 的 Redis 模組</span><span class="sxs-lookup"><span data-stu-id="9b411-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="9b411-112">範例</span><span class="sxs-lookup"><span data-stu-id="9b411-112">Example</span></span>

<span data-ttu-id="9b411-113">此範例會連線到 Azure Redis 快取執行個體、儲存索引鍵/值組，然後依其索引鍵讀取所儲存的值。</span><span class="sxs-lookup"><span data-stu-id="9b411-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="9b411-114">管理封裝</span><span class="sxs-lookup"><span data-stu-id="9b411-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9b411-115">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="9b411-115">Install the npm module</span></span>

<span data-ttu-id="9b411-116">使用 npm 來安裝適用於 Node.js 的 Azure Redis 快取模組</span><span class="sxs-lookup"><span data-stu-id="9b411-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="9b411-117">範例</span><span class="sxs-lookup"><span data-stu-id="9b411-117">Example</span></span>

<span data-ttu-id="9b411-118">此範例會向 Azure 驗證，並列出指定之源群組中的所有 Redis 快取執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b411-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="9b411-119">範例</span><span class="sxs-lookup"><span data-stu-id="9b411-119">Samples</span></span>

* [<span data-ttu-id="9b411-120">如何搭配使用 Azure Redis 快取與 Node.js</span><span class="sxs-lookup"><span data-stu-id="9b411-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="9b411-121">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="9b411-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
