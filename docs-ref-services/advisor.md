---
title: 適用於 Node.js 的 Azure Advisor 模組
description: 適用於 Node.js 的 Azure Advisor 模組參考
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52116543"
---
# <a name="azure-advisor-modules-for-nodejs"></a>適用於 Node.js 的 Azure Advisor 模組

## <a name="overview"></a>概觀

Azure 建議程式是個人化的雲端顧問，可協助您依最佳做法來最佳化您的 Azure 部署。 Advisor 可分析您的資源組態和使用量遙測，然後建議可協助您改善 Azure 資源的成本效益、效能、高可用性和安全性的解決方案。

使用 Advisor，您可以：
- 取得主動式、可採取動作且個人化的最佳做法建議。
- 改善資源的效能、安全性及高可用性，同時尋找降低整體 Azure 費用的機會。
- 取得內嵌了提議動作的建議。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Advisor npm 模組

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>範例

此範例會顯示來自 Azure Advisor 的建議清單。

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
