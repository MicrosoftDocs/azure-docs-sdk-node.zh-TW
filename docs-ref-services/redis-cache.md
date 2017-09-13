---
title: "適用於 Node.js 的 Azure 快取模組"
description: "適用於 Node.js 的 Azure 快取模組參考"
keywords: "Azure,SDK,API,Redis 快取, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="ff10a-104">適用於 Node.js 的 Azure 快取模組</span><span class="sxs-lookup"><span data-stu-id="ff10a-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ff10a-105">概觀</span><span class="sxs-lookup"><span data-stu-id="ff10a-105">Overview</span></span>

<span data-ttu-id="ff10a-106">Azure Redis 快取是以常用的開放原始碼 Redis 專案作為基礎。</span><span class="sxs-lookup"><span data-stu-id="ff10a-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="ff10a-107">它可讓您從 Azure 應用程式存取由 Microsoft 管理的安全、專用 Redis 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff10a-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="ff10a-108">Redis 是一種進階的索引鍵值存放區，其中的索引鍵可以包含類似字串、雜湊、清單、集合和排序的集合等資料結構。</span><span class="sxs-lookup"><span data-stu-id="ff10a-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="ff10a-109">Redis 針對這些資料類型支援一組不可部分完成的操作。</span><span class="sxs-lookup"><span data-stu-id="ff10a-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="ff10a-110">深入了解 [Azure Redis 快取](https://docs.microsoft.com/azure/redis-cache/)。</span><span class="sxs-lookup"><span data-stu-id="ff10a-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="ff10a-111">用戶端套件</span><span class="sxs-lookup"><span data-stu-id="ff10a-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ff10a-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ff10a-112">Install the npm module</span></span>

<span data-ttu-id="ff10a-113">使用 npm 來安裝適用於 Node.js 的 Redis 模組</span><span class="sxs-lookup"><span data-stu-id="ff10a-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="ff10a-114">範例</span><span class="sxs-lookup"><span data-stu-id="ff10a-114">Example</span></span>

<span data-ttu-id="ff10a-115">此範例會連線到 Azure Redis 快取執行個體、儲存索引鍵/值組，然後依其索引鍵讀取所儲存的值。</span><span class="sxs-lookup"><span data-stu-id="ff10a-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="ff10a-116">管理套件</span><span class="sxs-lookup"><span data-stu-id="ff10a-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ff10a-117">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ff10a-117">Install the npm module</span></span>

<span data-ttu-id="ff10a-118">使用 npm 來安裝適用於 Node.js 的 Azure Redis 快取模組</span><span class="sxs-lookup"><span data-stu-id="ff10a-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="ff10a-119">範例</span><span class="sxs-lookup"><span data-stu-id="ff10a-119">Example</span></span>

<span data-ttu-id="ff10a-120">此範例會向 Azure 驗證，並列出指定之源群組中的所有 Redis 快取執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff10a-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="ff10a-121">範例</span><span class="sxs-lookup"><span data-stu-id="ff10a-121">Samples</span></span>

* [<span data-ttu-id="ff10a-122">如何搭配使用 Azure Redis 快取與 Node.js</span><span class="sxs-lookup"><span data-stu-id="ff10a-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="ff10a-123">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ff10a-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
