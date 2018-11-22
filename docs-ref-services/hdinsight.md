---
title: 適用於 Node.js 的 Azure HDInsight 模組
description: 適用於 Node.js 的 Azure HDInsight 模組參考
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: e35e0d487efce2a591130403f8b72a43c638fdec
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52101723"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>適用於 Node.js 的 Azure HDInsight 模組

Azure HDInsight 是 Hortonworks Data Platform (HDP) 中 Hadoop 元件的雲端發佈。 Apache Hadoop 是原始的開放原始碼建構，用於分散式處理和分析電腦叢集上的巨量資料集。

HDInsight 透過下列方式讓 Hadoop 技術更容易使用︰
- 較少的安裝和設定。 請參閱「在 HDInsight 中佈建 Hadoop 叢集」。
- 高可用性和可靠性。 請參閱「HDInsight 可用性和可靠性」。
- 透過與 Active Directory 整合提供安全性和治理。 請參閱「已加入網域的叢集」。
- 不需中斷作業的動態調整
- 元件更新和目前版本。 請參閱「HDInsight 上的 Hadoop 元件和版本」。
- 與其他 Azure 服務整合，包括 Web 應用程式和 SQL Database

Hadoop 技術堆疊包含相關的軟體和公用程式，其中包括 Apache Hive、HBase、Spark、Kafka 和其他許多軟體。 

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-modules"></a>安裝 npm 模組

使用 npm 來安裝適用於 Node.js 的 Azure HDInsight 模組

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>範例 

此範例會建立 HD Insight 用戶端，並列出所有可用的叢集。 

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

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
