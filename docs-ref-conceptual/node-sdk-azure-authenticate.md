---
title: "使用適用於 Node.js 的 Azure 管理模組進行驗證"
description: "使用用來進入適用於 Node.js 之 Azure 管理模組的服務主體進行驗證"
keywords: "Azure, Node, SDK, API, 驗證, Active Directory, 服務主體"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="4ad11-104">使用適用於 Node.js 的 Azure 模組進行驗證</span><span class="sxs-lookup"><span data-stu-id="4ad11-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="4ad11-105">所有服務 API 在具現化時都需要透過 `credentials` 物件驗證。</span><span class="sxs-lookup"><span data-stu-id="4ad11-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="4ad11-106">透過 Azure SDK for Node.js 驗證並建立所需認證的方法有三種：</span><span class="sxs-lookup"><span data-stu-id="4ad11-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="4ad11-107">基本驗證</span><span class="sxs-lookup"><span data-stu-id="4ad11-107">Basic authentication</span></span>
- <span data-ttu-id="4ad11-108">互動式登入</span><span class="sxs-lookup"><span data-stu-id="4ad11-108">Interactive login</span></span>
- <span data-ttu-id="4ad11-109">服務主體驗證</span><span class="sxs-lookup"><span data-stu-id="4ad11-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="4ad11-110">基本驗證</span><span class="sxs-lookup"><span data-stu-id="4ad11-110">Basic authentication</span></span>

<span data-ttu-id="4ad11-111">若要以程式設計方式使用您的 Azure 帳戶的認證驗證，請使用 `loginWithUsernamePassword` 函式。</span><span class="sxs-lookup"><span data-stu-id="4ad11-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="4ad11-112">下列 JavaScript 程式碼片段說明如何使用儲存為環境變數的認證進行基本驗證。</span><span class="sxs-lookup"><span data-stu-id="4ad11-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="4ad11-113">互動式登入</span><span class="sxs-lookup"><span data-stu-id="4ad11-113">Interactive login</span></span>

<span data-ttu-id="4ad11-114">互動式登入提供的連結和程式碼可讓使用者從瀏覽器驗證。</span><span class="sxs-lookup"><span data-stu-id="4ad11-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="4ad11-115">相同指令碼使用多個帳戶或偏好使用者介入時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="4ad11-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="4ad11-116">服務主體驗證</span><span class="sxs-lookup"><span data-stu-id="4ad11-116">Service principal authentication</span></span>

<span data-ttu-id="4ad11-117">[互動式登入](#interactive-login)是最簡單的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="4ad11-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="4ad11-118">不過，使用 Node.js SDK 時，建議您使用服務主體驗證，而非提供您的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="4ad11-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="4ad11-119">[使用 Node.js 建立 Azure 服務主體](./node-sdk-azure-authenticate-principal.md)主題說明用於建立 (和使用) 服務主體的各種技術。</span><span class="sxs-lookup"><span data-stu-id="4ad11-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 