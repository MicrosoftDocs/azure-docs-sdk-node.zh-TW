---
title: "適用於 Node.js 的 Azure 辨識服務模組"
description: "適用於 Node.js 的 Azure 辨識服務模組參考"
keywords: "Azure,SDK,API,辨識服務, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>適用於 Node.js 的 Azure 辨識服務模組

## <a name="overview"></a>概觀

Microsoft 辨識服務是一組可供開發人員使用的 API、SDK 和服務，可讓其應用程式更具智能、吸引力且更容易探索。 Microsoft 辨識服務詳述 Microsoft 不斷演變的機器學習 API 發展產品組合，可讓開發人員輕鬆地將智慧型功能 (例如情緒和影片偵測；臉部、語音和視覺辨識；以及語音和語言理解) 新增至其應用程式。 我們的願景是在可逐漸看到、聽到、說出和理解，甚至開始推理之系統的輔助之下，提供更多個人運算體驗並提升生產力。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 辨識服務 npm 模組

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>範例

此範例會列出所有的辨識服務帳戶。

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
