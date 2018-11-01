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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50284222"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="ee22f-103">適用於 Node.js 的 Azure Data Lake Analytics 模組</span><span class="sxs-lookup"><span data-stu-id="ee22f-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="ee22f-104">Azure Data Lake Analytics 是隨選分析作業服務，可簡化巨量資料分析。</span><span class="sxs-lookup"><span data-stu-id="ee22f-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="ee22f-105">您可以著重於撰寫、執行和管理作業，而非操作分散式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ee22f-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="ee22f-106">無需部署、設定及調整硬體，您只需寫入查詢便可轉換資料並擷取寶貴的深入見解。</span><span class="sxs-lookup"><span data-stu-id="ee22f-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="ee22f-107">透過針對所需的功能設定級別，此項分析服務便可立即處理任何規模的工作。</span><span class="sxs-lookup"><span data-stu-id="ee22f-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="ee22f-108">只有在作業進行時您才需要支付費用，十分符合成本效益。</span><span class="sxs-lookup"><span data-stu-id="ee22f-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="ee22f-109">分析服務支援 Azure Active Directory，讓您管理存取權及角色，且其與您的內部部署身分識別系統整合。</span><span class="sxs-lookup"><span data-stu-id="ee22f-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="ee22f-110">分析服務支援還包括 U-SQL，該語言可將 SQL 的優勢與使用者程式碼的運算能力結合在一起。</span><span class="sxs-lookup"><span data-stu-id="ee22f-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="ee22f-111">U-SQL 的可調整分散式執行階段可讓您有效地分析資料，範圍遍及存放區以及 Azure、Azure SQL Database 以及 Azure SQL 資料倉儲中的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ee22f-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="ee22f-112">管理封裝</span><span class="sxs-lookup"><span data-stu-id="ee22f-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ee22f-113">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="ee22f-113">Install the npm module</span></span>

<span data-ttu-id="ee22f-114">使用 npm 來安裝適用於 Node.js 的 Azure Data Lake Analytics 模組</span><span class="sxs-lookup"><span data-stu-id="ee22f-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="ee22f-115">範例</span><span class="sxs-lookup"><span data-stu-id="ee22f-115">Example</span></span>

<span data-ttu-id="ee22f-116">此範例會列出指定之訂用帳戶的所有分析帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee22f-116">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ee22f-117">範例</span><span class="sxs-lookup"><span data-stu-id="ee22f-117">Samples</span></span>

<span data-ttu-id="ee22f-118">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="ee22f-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
