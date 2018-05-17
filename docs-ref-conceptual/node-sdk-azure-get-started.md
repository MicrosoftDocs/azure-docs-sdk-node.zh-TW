---
title: 開始使用適用於 Node.js 的 Azure 模組
description: 以適用於 Node.js 的 Azure 模組開始驗證和資源管理
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a>開始使用適用於 Node.js 的 Azure 模組

本指南會逐步引導您安裝 Azure Node.js 模組、使用服務主體向 Azure 進行驗證，以及執行可在 Azure 訂用帳戶中建立資源並連線至 Azure 雲端服務的範例程式碼。

## <a name="prerequisites"></a>先決條件

- 一個 Azure 帳戶。 如果您沒有帳戶，請[取得免費試用帳戶](https://azure.microsoft.com/free/)
- [Node.js](https://nodejs.org)
- [Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) 或 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)。

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a>準備您的環境

在空的目錄中建立新的專案，並安裝下列 npm 模組：

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a>設定驗證

Node.js 應用程式必須有 Azure 訂用帳戶的讀取和建立權限，才能在此指南中執行程式碼範例。 請建立服務主體，並將應用程式設定為使用其認證來執行。 服務主體是與身分識別相關聯的非互動式帳戶，而您只會對此身分識別授與執行應用程式所需的權限。

[使用 Azure CLI 2.0 建立服務主體](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli)並擷取輸出。 您必須在 password 引數中提供[安全的密碼](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy)，而不是提供 `MY_SECURE_PASSWORD`。

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

匯出 appId、password 和 tenant 的值作為環境變數：

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

使用 [az account show](https://docs.microsoft.com/cli/azure/account#show) 來取得訂用帳戶的識別碼

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

匯出訂用帳戶識別碼作為環境變數

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a>建立 Linux 虛擬機器

使用下列程式碼，在目前的目錄中建立新檔案 *createVM.js*。 使用良好的密碼來更新 `adminPass` 的值。

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

從命令列執行程式碼：

```bash
node createVM.js
```

程式碼完成後，使用您程式碼中的 `adminPass` 值取得新虛擬機器的識別碼並利用 SSH 登入。

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a>將 Blob 寫入至 Azure 儲存體

使用下列程式碼，在目前的目錄中建立新檔案 *uploadFile.js*。

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

執行命令，然後複製輸出中的 URL 並貼到網頁瀏覽器中，以檢視 Azure 儲存體中的檔案：

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a>清除資源

刪除資源群組，可移除在本指南中建立的資源。

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a>後續步驟

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。

## <a name="reference"></a>參考 

我們針對所有套件提供了[參考資料](/javascript/api/overview/azure/)。

## <a name="get-help-and-give-feedback"></a>獲得協助及提供意見

您可以在 [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js) 的社群中張貼問題。 在[專案 GitHub](https://github.com/Azure/azure-sdk-for-node) 上，針對適用於 Node.js 的 Azure 模組回報錯誤和提出問題。

