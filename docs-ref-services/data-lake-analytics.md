---
title: 適用於 Node.js 的 Azure Data Lake Analytics 模組
description: 適用於 Node.js 的 Azure Data Lake Analytics 模組參考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "49797453"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>適用於 Node.js 的 Azure Data Lake Analytics 模組

Azure Data Lake Analytics 是隨選分析作業服務，可簡化巨量資料分析。 您可以著重於撰寫、執行和管理作業，而非操作分散式基礎結構。 無需部署、設定及調整硬體，您只需寫入查詢便可轉換資料並擷取寶貴的深入見解。 透過針對所需的功能設定級別，此項分析服務便可立即處理任何規模的工作。 只有在作業進行時您才需要支付費用，十分符合成本效益。 分析服務支援 Azure Active Directory，讓您管理存取權及角色，且其與您的內部部署身分識別系統整合。 分析服務支援還包括 U-SQL，該語言可將 SQL 的優勢與使用者程式碼的運算能力結合在一起。 U-SQL 的可調整分散式執行階段可讓您有效地分析資料，範圍遍及存放區以及 Azure、Azure SQL Database 以及 Azure SQL 資料倉儲中的 SQL Server。

### <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

使用 npm 來安裝適用於 Node.js 的 Azure Data Lake Analytics 模組

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>範例

此範例會列出指定之訂用帳戶的所有分析帳戶。

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
