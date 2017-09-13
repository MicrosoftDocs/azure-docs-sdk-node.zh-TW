---
title: "適用於 Node.js 的 Azure 授權模組"
description: "適用於 Node.js 的 Azure 授權模組參考"
keywords: "Azure,SDK,API,授權, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="f40f8-104">適用於 Node.js 的 Azure 授權模組</span><span class="sxs-lookup"><span data-stu-id="f40f8-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f40f8-105">概觀</span><span class="sxs-lookup"><span data-stu-id="f40f8-105">Overview</span></span>

<span data-ttu-id="f40f8-106">Azure App Service 驗證/授權是可讓應用程式接受使用者登入的一種功能，而不需要在應用程式後端變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="f40f8-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="f40f8-107">授權提供簡單的方法來保護您的應用程式，以及使用每位使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="f40f8-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="f40f8-108">管理套件</span><span class="sxs-lookup"><span data-stu-id="f40f8-108">Management package</span></span>

<span data-ttu-id="f40f8-109">使用 npm 來安裝適用於 Node.js 的 Azure 授權模組</span><span class="sxs-lookup"><span data-stu-id="f40f8-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f40f8-110">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f40f8-110">Install the npm module</span></span>

<span data-ttu-id="f40f8-111">安裝 Azure 授權 npm 模組</span><span class="sxs-lookup"><span data-stu-id="f40f8-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="f40f8-112">範例</span><span class="sxs-lookup"><span data-stu-id="f40f8-112">Example</span></span>

<span data-ttu-id="f40f8-113">此範例會列出所要求資源群組的所有角色指派。</span><span class="sxs-lookup"><span data-stu-id="f40f8-113">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f40f8-114">範例</span><span class="sxs-lookup"><span data-stu-id="f40f8-114">Samples</span></span>

<span data-ttu-id="f40f8-115">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f40f8-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
