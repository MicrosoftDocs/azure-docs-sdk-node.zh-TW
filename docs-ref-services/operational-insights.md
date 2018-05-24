---
title: 適用於 Node.js 的 Azure Operational Insights 模組
description: 適用於 Node.js 的 Azure Operational Insights 模組參考
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>適用於 Node.js 的 Azure Operational Insights 模組

使用 npm 來安裝適用於 Node.js 的 Azure Operational Insights 模組參考

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>範例 

此範例會建立用戶端，連線到 Operational Insights 以及擷取所指定資源群組的工作區清單。

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
