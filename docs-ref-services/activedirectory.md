---
title: "Node.js 適用的 Azure Active Directory 模組"
description: "Node.js 適用的 Azure Active Directory 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="733cf-103">Node.js 適用的 Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="733cf-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="733cf-104">概觀</span><span class="sxs-lookup"><span data-stu-id="733cf-104">Overview</span></span>

<span data-ttu-id="733cf-105">[適用於 Node.js 的 Azure Active Directory 驗證程式庫 (ADAL)](https://www.npmjs.com/package/adal-node) 可讓 Node.js 應用程式向 AAD 驗證，以便存取 AAD 保護的 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="733cf-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="733cf-106">用戶端封裝</span><span class="sxs-lookup"><span data-stu-id="733cf-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="733cf-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="733cf-107">Install the npm modules</span></span>

<span data-ttu-id="733cf-108">使用 npm 來安裝 Azure 儲存體用戶端或管理模組。</span><span class="sxs-lookup"><span data-stu-id="733cf-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="733cf-109">範例</span><span class="sxs-lookup"><span data-stu-id="733cf-109">Example</span></span>

<span data-ttu-id="733cf-110">來自[用戶端認證範例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)的這個範例說明如何透過用戶端認證進行伺服器對伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="733cf-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="733cf-111">範例</span><span class="sxs-lookup"><span data-stu-id="733cf-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="733cf-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="733cf-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
