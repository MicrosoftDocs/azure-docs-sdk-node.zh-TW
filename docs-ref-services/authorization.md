---
title: 適用於 Node.js 的 Azure 授權模組
description: 適用於 Node.js 的 Azure 授權模組參考
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "49735063"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="020a1-103">適用於 Node.js 的 Azure 授權模組</span><span class="sxs-lookup"><span data-stu-id="020a1-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="020a1-104">概觀</span><span class="sxs-lookup"><span data-stu-id="020a1-104">Overview</span></span>

<span data-ttu-id="020a1-105">Azure App Service 驗證/授權是可讓應用程式接受使用者登入的一種功能，而不需要在應用程式後端變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="020a1-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="020a1-106">授權提供簡單的方法來保護您的應用程式，以及使用每位使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="020a1-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="020a1-107">管理封裝</span><span class="sxs-lookup"><span data-stu-id="020a1-107">Management package</span></span>

<span data-ttu-id="020a1-108">使用 npm 來安裝適用於 Node.js 的 Azure 授權模組</span><span class="sxs-lookup"><span data-stu-id="020a1-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="020a1-109">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="020a1-109">Install the npm module</span></span>

<span data-ttu-id="020a1-110">安裝 Azure 授權 npm 模組</span><span class="sxs-lookup"><span data-stu-id="020a1-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="020a1-111">範例</span><span class="sxs-lookup"><span data-stu-id="020a1-111">Example</span></span>

<span data-ttu-id="020a1-112">此範例會列出所要求資源群組的所有角色指派。</span><span class="sxs-lookup"><span data-stu-id="020a1-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="020a1-113">範例</span><span class="sxs-lookup"><span data-stu-id="020a1-113">Samples</span></span>

<span data-ttu-id="020a1-114">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="020a1-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
