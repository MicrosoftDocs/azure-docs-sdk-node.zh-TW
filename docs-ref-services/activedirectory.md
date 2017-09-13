---
title: "Node.js 適用的 Azure Active Directory 模組"
description: "Node.js 適用的 Azure Active Directory 模組參考"
keywords: "Azure, Node, SDK, API, 儲存體, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="f9953-104">Node.js 適用的 Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="f9953-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f9953-105">概觀</span><span class="sxs-lookup"><span data-stu-id="f9953-105">Overview</span></span>

<span data-ttu-id="f9953-106">[適用於 Node.js 的 Azure Active Directory 驗證程式庫 (ADAL)](https://www.npmjs.com/package/adal-node) 可讓 Node.js 應用程式向 AAD 驗證，以便存取 AAD 保護的 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="f9953-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="f9953-107">用戶端套件</span><span class="sxs-lookup"><span data-stu-id="f9953-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="f9953-108">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f9953-108">Install the npm modules</span></span>

<span data-ttu-id="f9953-109">使用 npm 來安裝 Azure 儲存體用戶端或管理模組。</span><span class="sxs-lookup"><span data-stu-id="f9953-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="f9953-110">範例</span><span class="sxs-lookup"><span data-stu-id="f9953-110">Example</span></span>

<span data-ttu-id="f9953-111">來自[用戶端認證範例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)的這個範例說明如何透過用戶端認證進行伺服器對伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="f9953-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="f9953-112">範例</span><span class="sxs-lookup"><span data-stu-id="f9953-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="f9953-113">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f9953-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
