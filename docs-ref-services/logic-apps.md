---
title: 適用於 Node.js 的 Azure Logic Apps 模組
description: 適用於 Node.js 的 Azure Logic Apps 模組參考
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261549"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>適用於 Node.js 的 Azure Logic Apps 模組

Logic Apps 提供簡化和實作雲端中可擴充整合和工作流程的途徑。 它提供視覺化設計工具，以一系列的步驟 (也稱為工作流程) 為您的程序建立模型並加以自動化。 雲端和內部部署中有 許多連接器可快速整合各項服務和通訊協定。 邏輯應用程式是以觸發程序為開端 (如「當帳戶新增至 Dynamics CRM 時」)，而在觸發後可以開始處理各種組合的動作、轉換和條件邏輯。

使用 Logic Apps 的優點包括︰
- 使用易於了解的設計工具來設計複雜程序以節省時間
- 順暢地實作難以在程式碼中實作的模式和工作流程。
- 從範本快速開始使用
- 使用自己的自訂 API、程式碼和動作來自訂邏輯應用程式
- 連接並同步處理跨內部部署與雲端的不同系統
- 利用頂級整合支援打造 BizTalk Server、API 管理、Azure Functions 和 Azure 服務匯流排

Logic Apps 是完全受控的 iPaaS (整合平台即服務)，可讓開發人員不必擔心建置裝載、延展性、可用性和管理。 邏輯應用程式會自動相應增加以滿足需求。

## <a name="management-package"></a>管理封裝

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝適用於 Node.js 的 Azure 邏輯模組

```bash
npm install azure-arm-logic
```

### <a name="example"></a>範例

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
