---
title: 使用適用於 Node.js 的 Azure 管理模組進行驗證
description: 使用用來進入適用於 Node.js 之 Azure 管理模組的服務主體進行驗證
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220510"
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="51af5-103">使用適用於 Node.js 的 Azure 模組進行驗證</span><span class="sxs-lookup"><span data-stu-id="51af5-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="51af5-104">所有服務 API 在具現化時都需要透過 `credentials` 物件驗證。</span><span class="sxs-lookup"><span data-stu-id="51af5-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="51af5-105">透過 Azure SDK for Node.js 驗證並建立所需認證的方法有三種：</span><span class="sxs-lookup"><span data-stu-id="51af5-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="51af5-106">基本驗證</span><span class="sxs-lookup"><span data-stu-id="51af5-106">Basic authentication</span></span>
- <span data-ttu-id="51af5-107">互動式登入</span><span class="sxs-lookup"><span data-stu-id="51af5-107">Interactive login</span></span>
- <span data-ttu-id="51af5-108">服務主體驗證</span><span class="sxs-lookup"><span data-stu-id="51af5-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="51af5-109">基本驗證</span><span class="sxs-lookup"><span data-stu-id="51af5-109">Basic authentication</span></span>

<span data-ttu-id="51af5-110">若要以程式設計方式使用您的 Azure 帳戶的認證驗證，請使用 `loginWithUsernamePassword` 函式。</span><span class="sxs-lookup"><span data-stu-id="51af5-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="51af5-111">下列 JavaScript 程式碼片段說明如何使用儲存為環境變數的認證進行基本驗證。</span><span class="sxs-lookup"><span data-stu-id="51af5-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="51af5-112">互動式登入</span><span class="sxs-lookup"><span data-stu-id="51af5-112">Interactive login</span></span>

<span data-ttu-id="51af5-113">互動式登入提供的連結和程式碼可讓使用者從瀏覽器驗證。</span><span class="sxs-lookup"><span data-stu-id="51af5-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="51af5-114">相同指令碼使用多個帳戶或偏好使用者介入時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="51af5-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="51af5-115">服務主體驗證</span><span class="sxs-lookup"><span data-stu-id="51af5-115">Service principal authentication</span></span>

<span data-ttu-id="51af5-116">[互動式登入](#interactive-login)是最簡單的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="51af5-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="51af5-117">不過，使用 Node.js SDK 時，建議您使用服務主體驗證，而非提供您的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="51af5-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="51af5-118">[使用 Node.js 建立 Azure 服務主體](./node-sdk-azure-authenticate-principal.md)主題說明用於建立 (和使用) 服務主體的各種技術。</span><span class="sxs-lookup"><span data-stu-id="51af5-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 