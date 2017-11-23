---
title: "適用於 Node.js 的 Azure Data Lake Store 模組"
description: "適用於 Node.js 的 Azure Data Lake Store 模組參考"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="8e17e-104">適用於 Node.js 的 Azure Data Lake Store 模組</span><span class="sxs-lookup"><span data-stu-id="8e17e-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="8e17e-105">概觀</span><span class="sxs-lookup"><span data-stu-id="8e17e-105">Overview</span></span>
<span data-ttu-id="8e17e-106">Azure Data Lake Store 是容納巨量資料分析工作負載的企業級超大規模存放庫。</span><span class="sxs-lookup"><span data-stu-id="8e17e-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="8e17e-107">Azure Data Lake 可讓您在單一位置擷取任何大小、類型和擷取速度的資料，以便進行運作和探究分析。</span><span class="sxs-lookup"><span data-stu-id="8e17e-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="8e17e-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="8e17e-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8e17e-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="8e17e-109">Install the npm module</span></span>

<span data-ttu-id="8e17e-110">使用 npm 來安裝適用於 Node.js 的 Azure Data Lake Store 模組</span><span class="sxs-lookup"><span data-stu-id="8e17e-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="8e17e-111">範例</span><span class="sxs-lookup"><span data-stu-id="8e17e-111">Example</span></span>

<span data-ttu-id="8e17e-112">下列範例列出指定之 Azure 訂用帳戶中的所有 Data Lake Store 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8e17e-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="8e17e-113">範例</span><span class="sxs-lookup"><span data-stu-id="8e17e-113">Samples</span></span>

<span data-ttu-id="8e17e-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="8e17e-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
