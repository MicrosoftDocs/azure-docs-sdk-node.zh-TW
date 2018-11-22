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
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52060253"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js 適用的 Azure Active Directory 模組

## <a name="overview"></a>概觀

> [!IMPORTANT]
> 強烈建議您使用 [Microsoft Graph](https://graph.microsoft.io/) 取代 Azure AD Graph API 來存取 Azure Active Directory 資源。 我們的開發工作現在是針對 Microsoft Graph，並沒有針對 Azure AD Graph API 規劃的進一步增強功能 。 有極少數的案例可能仍適用 Azure AD Graph API；如需詳細資訊，請參閱 Office 開發人員中心的 [Microsoft Graph 或 Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) 部落格文章。

[適用於 Node.js 的 Azure Active Directory 驗證程式庫 (ADAL)](https://www.npmjs.com/package/adal-node) 可讓 Node.js 應用程式向 AAD 驗證，以便存取 AAD 保護的 Web 資源。

## <a name="client-package"></a>用戶端封裝

### <a name="install-the-npm-modules"></a>安裝 npm 模組

使用 npm 來安裝 Azure 儲存體用戶端或管理模組。

```bash
npm install adal-node
```   

### <a name="example"></a>範例

來自[用戶端認證範例](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)的這個範例說明如何透過用戶端認證進行伺服器對伺服器驗證。

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

## <a name="samples"></a>範例

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
