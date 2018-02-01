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
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js 適用的 Azure Active Directory 模組

## <a name="overview"></a>概觀

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
