---
title: 適用於 Node.js 的 Azure CDN 模組
description: 適用於 Node.js 的 Azure CDN 模組參考
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51178877"
---
# <a name="azure-cdn-modules-for-nodejs"></a>適用於 Node.js 的 Azure CDN 模組

## <a name="overview"></a>概觀

Azure 內容傳遞網路 (CDN) 為開發人員提供一套傳遞高頻寬內容 (裝載在 Azure 或任何其他位置中) 的通用解決方案。 使用 CDN，可讓您快取從 Azure Blob 儲存體、Web 應用程式、虛擬機器、應用程式資料夾或其他 HTTP/HTTPS 位置載入的公用物件。 CDN 快取可以保留在策略性位置上，以提供最大頻寬將內容傳遞給使用者。 CDN 通常用來傳遞靜態內容，例如影像、樣式表、文件、檔案、用戶端指令碼和 HTML 頁面。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure CDN npm 模組

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>範例

此範例會列出所有的 CDN 設定檔。

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
