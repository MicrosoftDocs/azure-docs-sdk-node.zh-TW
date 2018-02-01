---
title: "適用於 Node.js 的 Azure 授權模組"
description: "適用於 Node.js 的 Azure 授權模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>適用於 Node.js 的 Azure 授權模組

## <a name="overview"></a>概觀

Azure App Service 驗證/授權是可讓應用程式接受使用者登入的一種功能，而不需要在應用程式後端變更程式碼。 授權提供簡單的方法來保護您的應用程式，以及使用每位使用者的資料。

## <a name="management-package"></a>管理封裝

使用 npm 來安裝適用於 Node.js 的 Azure 授權模組

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 授權 npm 模組

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>範例

此範例會列出所要求資源群組的所有角色指派。

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
