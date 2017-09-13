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
# <a name="create-an-azure-service-principal-with-nodejs"></a>使用 Node.js 來建立 Azure 服務主體 

當應用程式需要存取資源時，您可以設定應用程式的身分識別，並使用應用程式本身的認證進行驗證。 此身分識別就是所謂的*服務主體*。 基本上，您會建立 Azure Active Directory 帳戶的金鑰，以提供給 SDK 進行驗證，而不需要使用者介入或使用者名稱/密碼。

服務主體方法可讓您：
- 將權限指派給不同於您自己權限的 App 身分識別。 一般而言，這些權限只會限制為 App 必須執行的確切權限。
- 使用憑證在執行無人看管的指令碼時進行驗證。

本主題說明建立服務主體的三種技巧。

- Azure 入口網站
- Azure CLI 2.0
- Azure SDK for Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>使用 Azure 入口網站建立服務主體

遵循[使用入口網站來建立可存取資源的 Active Directory 應用程式和服務主體](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/)主題中所述的步驟，產生服務主體。

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>使用 Azure CLI 2.0 建立服務主體

利用下列步驟完成使用 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) 建立服務主體：

1. 下載 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。

2. 開啟終端機視窗。

3. 輸入下列命令以啟動登入程序：

    ```shell
    $ az login
    ```

4. 呼叫 `az login` 會產生 URL 和程式碼。 瀏覽至指定的 URL，輸入程式碼，並使用您的 Azure 身分識別登入 (如果您已經登入，這可能會發生自動)。 您接著可以透過 CLI 存取您的帳戶。

5. 取得您的訂用帳戶和租用戶識別碼：

    ```shell
    $ az account list
    ```

    以下顯示輸出的範例：

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

    **請記下訂用帳戶識別碼，因為該識別碼將使用於步驟 7。**

6. 建立服務主體以取得 JSON 物件，包含您需要向 Azure 驗證的其他資訊。

    ```shell
    $ az ad sp create-for-rbac
    ```

    以下顯示輸出的範例：

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **請記下租用戶、名稱和密碼值，因為這些值將使用於步驟 7。**

7. 設定環境變數 - 以您在步驟 4 和 5 取得的值取代 &lt;subscriptionId>、&lt;tenant>、&lt;name> 和 &lt;password> 預留位置。 

    **使用 Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **使用 PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>使用 Azure SDK for Node.js 建立服務主體

若要使用 JavaScript 以程式設計方式建立服務主體，請使用 [ServicePrincipal 指令碼](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)。   

## <a name="using-the-service-principal"></a>使用服務主體

一旦擁有服務主體，下列 JavaScript 程式碼片段說明如何使用服務主要金鑰來向 Azure SDK for Node.js 驗證。 修改下列預留位置：&lt;clientId or appId>、&lt;secret or password> 和 &lt;domain or tenant>。

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
