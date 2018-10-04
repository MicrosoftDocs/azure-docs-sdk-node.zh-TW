---
title: Node.js 適用的 Azure Active Directory 模組
description: Node.js 適用的 Azure Active Directory 模組參考
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48534486"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="4a168-103">Node.js 適用的 Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="4a168-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4a168-104">概觀</span><span class="sxs-lookup"><span data-stu-id="4a168-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a168-105">強烈建議您使用 [Microsoft Graph](https://graph.microsoft.io/) 取代 Azure AD Graph API 來存取 Azure Active Directory 資源。</span><span class="sxs-lookup"><span data-stu-id="4a168-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="4a168-106">我們的開發工作現在是針對 Microsoft Graph，並沒有針對 Azure AD Graph API 規劃的進一步增強功能 。</span><span class="sxs-lookup"><span data-stu-id="4a168-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="4a168-107">有極少數的案例可能仍適用 Azure AD Graph API；如需詳細資訊，請參閱 Office 開發人員中心的 [Microsoft Graph 或 Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="4a168-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="4a168-108">[適用於 Node.js 的 Azure Active Directory 驗證程式庫 (ADAL)](https://www.npmjs.com/package/adal-node) 可讓 Node.js 應用程式向 AAD 驗證，以便存取 AAD 保護的 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="4a168-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="4a168-109">用戶端封裝</span><span class="sxs-lookup"><span data-stu-id="4a168-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="4a168-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="4a168-110">Install the npm modules</span></span>

<span data-ttu-id="4a168-111">使用 npm 來安裝 Azure 儲存體用戶端或管理模組。</span><span class="sxs-lookup"><span data-stu-id="4a168-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="4a168-112">範例</span><span class="sxs-lookup"><span data-stu-id="4a168-112">Example</span></span>

<span data-ttu-id="4a168-113">來自[用戶端認證範例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)的這個範例說明如何透過用戶端認證進行伺服器對伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="4a168-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4a168-114">範例</span><span class="sxs-lookup"><span data-stu-id="4a168-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="4a168-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="4a168-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
