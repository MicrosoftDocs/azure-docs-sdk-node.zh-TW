---
title: 適用於 Node.js 的 Azure Relay 模組
description: 適用於 Node.js 的 Azure Relay 模組參考
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406374"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="d3ecf-103">適用於 Node.js 的 Azure Relay 模組</span><span class="sxs-lookup"><span data-stu-id="d3ecf-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="d3ecf-104">Azure 轉送服務可建立混合式應用程式，方法是讓您以安全的方式向公用雲端公開位於企業網路內部的服務，而無需開啟防火牆連線或要求對企業網路基礎結構的進行侵入式變更。</span><span class="sxs-lookup"><span data-stu-id="d3ecf-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="d3ecf-105">轉送支援各種不同的傳輸通訊協定和 Web 服務標準。</span><span class="sxs-lookup"><span data-stu-id="d3ecf-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="d3ecf-106">深入了解 [Azure 轉送](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)。</span><span class="sxs-lookup"><span data-stu-id="d3ecf-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="d3ecf-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="d3ecf-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d3ecf-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="d3ecf-108">Install the npm module</span></span>

<span data-ttu-id="d3ecf-109">安裝 Azure Relay npm 模組</span><span class="sxs-lookup"><span data-stu-id="d3ecf-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="d3ecf-110">範例</span><span class="sxs-lookup"><span data-stu-id="d3ecf-110">Example</span></span>

<span data-ttu-id="d3ecf-111">此範例會列出 Relay 用戶端的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d3ecf-111">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d3ecf-112">範例</span><span class="sxs-lookup"><span data-stu-id="d3ecf-112">Samples</span></span>

<span data-ttu-id="d3ecf-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d3ecf-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
