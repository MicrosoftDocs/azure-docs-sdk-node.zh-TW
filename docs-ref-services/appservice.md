---
title: 適用於 Node.js 的 Azure App Service 模組
description: 適用於 Node.js 的 Azure App Service 模組參考
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266609"
---
# <a name="azure-app-service-modules-for-nodejs"></a>適用於 Node.js 的 Azure App Service 模組

## <a name="overview"></a>概觀

Azure App Service 是 Microsoft Azure 的平台即服務 (PaaS) 供應項目。 建立適用任何平台或裝置的 Web 與行動應用程式。 整合您的應用程式與 SaaS 解決方案、與內部部署應用程式連接，並使您的商務程序自動化。 Azure 會使用您選擇的共用 VM 資源或專用 VM，在完全受控的虛擬機器 (VM) 上執行您的應用程式。

App Service 包含先前以 Azure 網站和 Azure 行動服務的形式來獨立提供的 Web 和行動功能。 此外，它也包含可用來自動執行商務程序及裝載雲端 API 的新功能。 App Service 是單一的整合式服務，可讓您將各種元件 (網站、行動應用程式後端、RESTful API 和商務程序) 撰寫成單一解決方案。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-package"></a>安裝 npm 套件

安裝適用於 Node.js 的 Azure App Service 模組

```bash
npm install azure-arm-website
```

### <a name="example"></a>範例

此範例會使用 Node.js 在 Azure 上建立網站。

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>範例

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
