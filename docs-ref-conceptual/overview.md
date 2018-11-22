---
title: 適用於 JavaScript 的 Azure 模組
description: 適用於 JavaScript 的 Azure 管理和服務模組概觀
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2018
ms.locfileid: "52064549"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="79c03-103">適用於 JavaScript 的 Azure 模組</span><span class="sxs-lookup"><span data-stu-id="79c03-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="79c03-104">使用適用於 JavaScript 的 Azure 模組，管理 Azure 資源並從 JavaScript 應用程式連線至服務。</span><span class="sxs-lookup"><span data-stu-id="79c03-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="79c03-105">此程式碼可以 [npm 模組](node-sdk-azure-install.md)提供，以便在您的專案中使用。</span><span class="sxs-lookup"><span data-stu-id="79c03-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="79c03-106">管理 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="79c03-106">Manage Azure resources</span></span>

<span data-ttu-id="79c03-107">使用管理模組從您的應用程式建立及查詢資源，或建置自己的 Azure 自動化工具。</span><span class="sxs-lookup"><span data-stu-id="79c03-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="79c03-108">例如，若要使用現有的網路介面來建立 Linux VM，您需要撰寫下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="79c03-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="79c03-109">請檢閱[安裝指示](node-sdk-azure-install.md)以取得完整的模組清單和[開始使用文章](node-sdk-azure-get-started.md)，以設定驗證和執行程式碼範例，進而針對您自己的 Azure 訂用帳戶建立和更新資源。</span><span class="sxs-lookup"><span data-stu-id="79c03-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="79c03-110">連線到 Azure 服務</span><span class="sxs-lookup"><span data-stu-id="79c03-110">Connect to Azure services</span></span>

<span data-ttu-id="79c03-111">除了使用 Azure 模組在 Azure 中建立和管理資源外，您也可以使用套件來連線到應用程式中的 Azure 雲端服務並加以使用。</span><span class="sxs-lookup"><span data-stu-id="79c03-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="79c03-112">例如，您可以更新資料表 SQL Database，或將檔案上傳至 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="79c03-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="79c03-113">從[完整清單](node-sdk-azure-install.md)選取特定服務所需的套件，然後瀏覽 [JavaScript 開發人員中心](https://azure.microsoft.com/develop/nodejs/)，以取得可供了解如何在應用程式中使用模組的教學課程和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="79c03-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="79c03-114">例如，若要在 Azure 儲存體容器中列印出每個 blob 的內容：</span><span class="sxs-lookup"><span data-stu-id="79c03-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="79c03-115">程式碼範例和參考</span><span class="sxs-lookup"><span data-stu-id="79c03-115">Sample code and reference</span></span>

<span data-ttu-id="79c03-116">下列範例涵蓋了可使用 Azure 管理模組來執行的常見工作，並已備有程式碼可供您自己的應用程式使用：</span><span class="sxs-lookup"><span data-stu-id="79c03-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="79c03-117">虛擬機器</span><span class="sxs-lookup"><span data-stu-id="79c03-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="79c03-118">Web Apps</span><span class="sxs-lookup"><span data-stu-id="79c03-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="79c03-119">SQL Database</span><span class="sxs-lookup"><span data-stu-id="79c03-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="79c03-120">我們提供了一個適用於服務和管理模組中所有模組的[參考](https://docs.microsoft.com/javascript/api)。</span><span class="sxs-lookup"><span data-stu-id="79c03-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="79c03-121">新功能、重大變更以及從先前版本移轉的指示則會在[版本資訊](https://github.com/Azure/azure-sdk-for-node/releases)中提供。</span><span class="sxs-lookup"><span data-stu-id="79c03-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>