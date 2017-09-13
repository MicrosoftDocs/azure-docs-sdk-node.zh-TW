---
title: "適用於 Node.js 的 Azure HDInsight 模組"
description: "適用於 Node.js 的 Azure HDInsight 模組參考"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="63445-104">適用於 Node.js 的 Azure HDInsight 模組</span><span class="sxs-lookup"><span data-stu-id="63445-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="63445-105">概觀</span><span class="sxs-lookup"><span data-stu-id="63445-105">Overview</span></span>

<span data-ttu-id="63445-106">Azure HDInsight 是 Hortonworks Data Platform (HDP) 中 Hadoop 元件的雲端發佈。</span><span class="sxs-lookup"><span data-stu-id="63445-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="63445-107">Apache Hadoop 是原始的開放原始碼建構，用於分散式處理和分析電腦叢集上的巨量資料集。</span><span class="sxs-lookup"><span data-stu-id="63445-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="63445-108">HDInsight 透過下列方式讓 Hadoop 技術更容易使用︰</span><span class="sxs-lookup"><span data-stu-id="63445-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="63445-109">較少的安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="63445-109">Less setup and configuration.</span></span> <span data-ttu-id="63445-110">請參閱「在 HDInsight 中佈建 Hadoop 叢集」。</span><span class="sxs-lookup"><span data-stu-id="63445-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="63445-111">高可用性和可靠性。</span><span class="sxs-lookup"><span data-stu-id="63445-111">High availability and reliability.</span></span> <span data-ttu-id="63445-112">請參閱「HDInsight 可用性和可靠性」。</span><span class="sxs-lookup"><span data-stu-id="63445-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="63445-113">透過與 Active Directory 整合提供安全性和治理。</span><span class="sxs-lookup"><span data-stu-id="63445-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="63445-114">請參閱「已加入網域的叢集」。</span><span class="sxs-lookup"><span data-stu-id="63445-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="63445-115">不需中斷作業的動態調整</span><span class="sxs-lookup"><span data-stu-id="63445-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="63445-116">元件更新和目前版本。</span><span class="sxs-lookup"><span data-stu-id="63445-116">Component updates and current versions.</span></span> <span data-ttu-id="63445-117">請參閱「HDInsight 上的 Hadoop 元件和版本」。</span><span class="sxs-lookup"><span data-stu-id="63445-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="63445-118">與其他 Azure 服務整合，包括 Web 應用程式和 SQL Database</span><span class="sxs-lookup"><span data-stu-id="63445-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="63445-119">Hadoop 技術堆疊包含相關的軟體和公用程式，其中包括 Apache Hive、HBase、Spark、Kafka 和其他許多軟體。</span><span class="sxs-lookup"><span data-stu-id="63445-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="63445-120">管理套件</span><span class="sxs-lookup"><span data-stu-id="63445-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="63445-121">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="63445-121">Install the npm modules</span></span>

<span data-ttu-id="63445-122">使用 npm 來安裝適用於 Node.js 的 Azure HDInsight 模組</span><span class="sxs-lookup"><span data-stu-id="63445-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="63445-123">範例</span><span class="sxs-lookup"><span data-stu-id="63445-123">Example</span></span> 

<span data-ttu-id="63445-124">此範例會建立 HD Insight 用戶端，並列出所有可用的叢集。</span><span class="sxs-lookup"><span data-stu-id="63445-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="63445-125">範例</span><span class="sxs-lookup"><span data-stu-id="63445-125">Samples</span></span>

<span data-ttu-id="63445-126">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="63445-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
