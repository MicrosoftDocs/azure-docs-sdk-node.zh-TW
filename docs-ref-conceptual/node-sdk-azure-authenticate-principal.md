---
title: "使用 Node.js 來建立 Azure 服務主體"
description: "了解如何透過 Node.js 使用服務主體驗證"
keywords: "Azure, Node, SDK, API, 驗證, Active Directory, 服務主體"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="92f8a-104">使用 Node.js 來建立 Azure 服務主體</span><span class="sxs-lookup"><span data-stu-id="92f8a-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="92f8a-105">當應用程式需要存取資源時，您可以設定應用程式的身分識別，並使用應用程式本身的認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="92f8a-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="92f8a-106">此身分識別就是所謂的*服務主體*。</span><span class="sxs-lookup"><span data-stu-id="92f8a-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="92f8a-107">基本上，您會建立 Azure Active Directory 帳戶的金鑰，以提供給 SDK 進行驗證，而不需要使用者介入或使用者名稱/密碼。</span><span class="sxs-lookup"><span data-stu-id="92f8a-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="92f8a-108">服務主體方法可讓您：</span><span class="sxs-lookup"><span data-stu-id="92f8a-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="92f8a-109">將權限指派給不同於您自己權限的 App 身分識別。</span><span class="sxs-lookup"><span data-stu-id="92f8a-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="92f8a-110">一般而言，這些權限只會限制為 App 必須執行的確切權限。</span><span class="sxs-lookup"><span data-stu-id="92f8a-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="92f8a-111">使用憑證在執行無人看管的指令碼時進行驗證。</span><span class="sxs-lookup"><span data-stu-id="92f8a-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="92f8a-112">本主題說明建立服務主體的三種技巧。</span><span class="sxs-lookup"><span data-stu-id="92f8a-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="92f8a-113">Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="92f8a-113">Azure portal</span></span>
- <span data-ttu-id="92f8a-114">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="92f8a-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="92f8a-115">Azure SDK for Node.js</span><span class="sxs-lookup"><span data-stu-id="92f8a-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="92f8a-116">使用 Azure 入口網站建立服務主體</span><span class="sxs-lookup"><span data-stu-id="92f8a-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="92f8a-117">遵循[使用入口網站來建立可存取資源的 Active Directory 應用程式和服務主體](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)主題中所述的步驟，產生服務主體。</span><span class="sxs-lookup"><span data-stu-id="92f8a-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="92f8a-118">使用 Azure CLI 2.0 建立服務主體</span><span class="sxs-lookup"><span data-stu-id="92f8a-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="92f8a-119">利用下列步驟完成使用 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) 建立服務主體：</span><span class="sxs-lookup"><span data-stu-id="92f8a-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="92f8a-120">下載 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。</span><span class="sxs-lookup"><span data-stu-id="92f8a-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="92f8a-121">開啟終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="92f8a-121">Open a terminal window.</span></span>

3. <span data-ttu-id="92f8a-122">輸入下列命令以啟動登入程序：</span><span class="sxs-lookup"><span data-stu-id="92f8a-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="92f8a-123">呼叫 `az login` 會產生 URL 和程式碼。</span><span class="sxs-lookup"><span data-stu-id="92f8a-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="92f8a-124">瀏覽至指定的 URL，輸入程式碼，並使用您的 Azure 身分識別登入 (如果您已經登入，這可能會發生自動)。</span><span class="sxs-lookup"><span data-stu-id="92f8a-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="92f8a-125">您接著可以透過 CLI 存取您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="92f8a-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="92f8a-126">取得您的訂用帳戶和租用戶識別碼：</span><span class="sxs-lookup"><span data-stu-id="92f8a-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="92f8a-127">以下顯示輸出的範例：</span><span class="sxs-lookup"><span data-stu-id="92f8a-127">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="92f8a-128">**請記下訂用帳戶識別碼，因為該識別碼將使用於步驟 7。**</span><span class="sxs-lookup"><span data-stu-id="92f8a-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="92f8a-129">建立服務主體以取得 JSON 物件，包含您需要向 Azure 驗證的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="92f8a-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="92f8a-130">以下顯示輸出的範例：</span><span class="sxs-lookup"><span data-stu-id="92f8a-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="92f8a-131">**請記下租用戶、名稱和密碼值，因為這些值將使用於步驟 7。**</span><span class="sxs-lookup"><span data-stu-id="92f8a-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="92f8a-132">設定環境變數 - 以您在步驟 4 和 5 取得的值取代 &lt;subscriptionId>、&lt;tenant>、&lt;name> 和 &lt;password> 預留位置。</span><span class="sxs-lookup"><span data-stu-id="92f8a-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="92f8a-133">**使用 Bash**</span><span class="sxs-lookup"><span data-stu-id="92f8a-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="92f8a-134">**使用 PowerShell**</span><span class="sxs-lookup"><span data-stu-id="92f8a-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="92f8a-135">使用 Azure SDK for Node.js 建立服務主體</span><span class="sxs-lookup"><span data-stu-id="92f8a-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="92f8a-136">若要使用 JavaScript 以程式設計方式建立服務主體，請使用 [ServicePrincipal 指令碼](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)。</span><span class="sxs-lookup"><span data-stu-id="92f8a-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="92f8a-137">使用服務主體</span><span class="sxs-lookup"><span data-stu-id="92f8a-137">Using the service principal</span></span>

<span data-ttu-id="92f8a-138">一旦擁有服務主體，下列 JavaScript 程式碼片段說明如何使用服務主要金鑰來向 Azure SDK for Node.js 驗證。</span><span class="sxs-lookup"><span data-stu-id="92f8a-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="92f8a-139">修改下列預留位置：&lt;clientId or appId>、&lt;secret or password> 和 &lt;domain or tenant>。</span><span class="sxs-lookup"><span data-stu-id="92f8a-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
