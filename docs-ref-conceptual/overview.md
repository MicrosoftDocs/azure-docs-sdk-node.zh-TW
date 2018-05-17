---
title: 適用於 Node.js 的 Azure 模組
description: 適用於 Node.js 的 Azure 管理和服務模組概觀
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-modules-for-nodejs"></a>適用於 Node.js 的 Azure 模組

使用適用於 Node.js 的 Azure 模組，管理 Azure 資源並從 Node.js 應用程式連線至服務。 此程式碼可以 [npm 模組](node-sdk-azure-install.md)提供，以便在您的專案中使用。 

## <a name="manage-azure-resources"></a>管理 Azure 資源

使用管理模組從您的應用程式建立及查詢資源，或建置自己的 Azure 自動化工具。 

例如，若要使用現有的網路介面來建立 Linux VM，您需要撰寫下列程式碼：

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

請檢閱[安裝指示](node-sdk-azure-install.md)以取得完整的模組清單和[開始使用文章](node-sdk-azure-get-started.md)，以設定驗證和執行程式碼範例，進而針對您自己的 Azure 訂用帳戶建立和更新資源。 

## <a name="connect-to-azure-services"></a>連線到 Azure 服務

除了使用 Azure 模組在 Azure 中建立和管理資源外，您也可以使用套件來連線到應用程式中的 Azure 雲端服務並加以使用。 例如，您可以更新資料表 SQL Database，或將檔案上傳至 Azure 儲存體。 從[完整清單](node-sdk-azure-install.md)選取特定服務所需的套件，然後瀏覽 [Node.js 開發人員中心](https://azure.microsoft.com/develop/nodejs/)，以取得可供了解如何在應用程式中使用模組的教學課程和程式碼範例。

例如，若要在 Azure 儲存體容器中列印出每個 blob 的內容：

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>程式碼範例和參考

下列範例涵蓋了可使用 Azure 管理模組來執行的常見工作，並已備有程式碼可供您自己的應用程式使用：

- [虛擬機器](node-samples-services-compute.md)
- [Web Apps](node-samples-services-web-and-mobile.md)
- [SQL Database](node-samples-services-database.md)
   
我們提供了一個適用於服務和管理模組中所有模組的[參考](https://docs.microsoft.com/javascript/api)。 新功能、重大變更以及從先前版本移轉的指示則會在[版本資訊](https://github.com/Azure/azure-sdk-for-node/releases)中提供。