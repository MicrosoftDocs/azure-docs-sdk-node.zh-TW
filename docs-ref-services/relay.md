---
title: "適用於 Node.js 的 Azure Relay 模組"
description: "適用於 Node.js 的 Azure Relay 模組參考"
keywords: Azure,SDK,API,Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="75ed1-104">適用於 Node.js 的 Azure Relay 模組</span><span class="sxs-lookup"><span data-stu-id="75ed1-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="75ed1-105">概觀</span><span class="sxs-lookup"><span data-stu-id="75ed1-105">Overview</span></span>

<span data-ttu-id="75ed1-106">Azure 轉送服務可建立混合式應用程式，方法是讓您以安全的方式向公用雲端公開位於企業網路內部的服務，而無需開啟防火牆連線或要求對企業網路基礎結構的進行侵入式變更。</span><span class="sxs-lookup"><span data-stu-id="75ed1-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="75ed1-107">轉送支援各種不同的傳輸通訊協定和 Web 服務標準。</span><span class="sxs-lookup"><span data-stu-id="75ed1-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="75ed1-108">深入了解 [Azure 轉送](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)。</span><span class="sxs-lookup"><span data-stu-id="75ed1-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="75ed1-109">管理套件</span><span class="sxs-lookup"><span data-stu-id="75ed1-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="75ed1-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="75ed1-110">Install the npm module</span></span>

<span data-ttu-id="75ed1-111">安裝 Azure Relay npm 模組</span><span class="sxs-lookup"><span data-stu-id="75ed1-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="75ed1-112">範例</span><span class="sxs-lookup"><span data-stu-id="75ed1-112">Example</span></span>

<span data-ttu-id="75ed1-113">此範例會列出 Relay 用戶端的命名空間。</span><span class="sxs-lookup"><span data-stu-id="75ed1-113">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="75ed1-114">範例</span><span class="sxs-lookup"><span data-stu-id="75ed1-114">Samples</span></span>

<span data-ttu-id="75ed1-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="75ed1-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
