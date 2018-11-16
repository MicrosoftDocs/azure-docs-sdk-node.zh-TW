---
title: 適用於 Node.js 的 Azure Analysis Services 模組
description: 適用於 Node.js 的 Azure Analysis Services 模組參考
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51450342"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>適用於 Node.js 的 Azure Analysis Services 模組

## <a name="overview"></a>概觀
此套件提供可讓您輕鬆管理 Microsoft Azure Analysis Services 的 Node.js 模組。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Analysis Services npm 模組

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>範例

此範例會列出所有可用的 Analysis Service 伺服器。

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
