---
title: 適用於 Node.js 的 Azure Data Lake Store 模組
description: 適用於 Node.js 的 Azure Data Lake Store 模組參考
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51185137"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="b6158-103">適用於 Node.js 的 Azure Data Lake Store 模組</span><span class="sxs-lookup"><span data-stu-id="b6158-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="b6158-104">Azure Data Lake Store 是容納巨量資料分析工作負載的企業級超大規模存放庫。</span><span class="sxs-lookup"><span data-stu-id="b6158-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="b6158-105">Azure Data Lake 可讓您在單一位置擷取任何大小、類型和擷取速度的資料，以便進行運作和探究分析。</span><span class="sxs-lookup"><span data-stu-id="b6158-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="b6158-106">管理套件</span><span class="sxs-lookup"><span data-stu-id="b6158-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b6158-107">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="b6158-107">Install the npm module</span></span>

<span data-ttu-id="b6158-108">使用 npm 來安裝適用於 Node.js 的 Azure Data Lake Store 模組</span><span class="sxs-lookup"><span data-stu-id="b6158-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="b6158-109">範例</span><span class="sxs-lookup"><span data-stu-id="b6158-109">Example</span></span>

<span data-ttu-id="b6158-110">下列範例列出指定之 Azure 訂用帳戶中的所有 Data Lake Store 帳戶。</span><span class="sxs-lookup"><span data-stu-id="b6158-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="b6158-111">範例</span><span class="sxs-lookup"><span data-stu-id="b6158-111">Samples</span></span>

<span data-ttu-id="b6158-112">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="b6158-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
