---
title: 適用於 Node.js 的 Azure 自動化模組
description: 適用於 Node.js 的 Azure 自動化模組參考
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 281b5081163fc3b0b74219c766ff9be5c421296b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052599"
---
# <a name="azure-automation-modules-for-nodejs"></a>適用於 Node.js 的 Azure 自動化模組

## <a name="overview"></a>概觀

Azure 自動化可讓使用者將雲端和企業環境中執行的手動、長時間執行、易發生錯誤且重複性高的工作加以自動化。 自動化可以節省時間並提高日常管理工作的可靠性，甚至將它們排程為定期自動執行。 您可以使用 Runbook 自動執行程序，或使用「期望狀態設定」自動進行組態管理。

## <a name="management-package"></a>管理封裝

### <a name="install-the-modules-with-npm"></a>使用 npm 安裝模組

使用 npm 來安裝適用於 Node.js 的 Azure 自動化模組

```bash
npm install azure-arm-automation
```

### <a name="example"></a>範例

此範例會列出自動化帳戶。

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
