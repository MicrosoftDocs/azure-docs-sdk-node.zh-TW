---
title: "適用於 Node.js 的 Azure Key Vault 模組"
description: "適用於 Node.js 的 Azure Key Vault 模組參考"
keywords: Azure,SDK,API,Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a>適用於 Node.js 的 Azure Key Vault 模組

## <a name="overview"></a>概觀

Azure 金鑰保存庫可協助保護雲端應用程式和服務所使用的密碼編譯金鑰和密碼。 使用金鑰保存庫之後，您可以加密金鑰和密碼 (例如驗證金鑰、儲存體帳戶金鑰、資料加密金鑰、.PFX 檔案和密碼)，方法是使用受硬體安全模組 (HSM) 保護的金鑰。 為了加強保證，您可以在 HSM 中匯入或產生金鑰。 如果您選擇這麼做，Microsoft 會在進行過 FIPS 140-2 Level 2 驗證的 HSM (硬體和韌體) 中處理您的金鑰。

金鑰保存庫簡化了金鑰管理程序，並可讓您控管存取和加密資料的金鑰。 開發人員可以在幾分鐘內建立開發和測試的金鑰，然後順利地將他們移轉至生產金鑰。 安全性系統管理員可以視需要授與 (和撤銷) 存取金鑰的權限。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組 

安裝 Azure Key Vault npm 模組

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>範例

此範例會在 Azure 中建立新的 Key Vault 服務。

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>範例

- [開始在 Node.js 中使用 Key Vault](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [使用 Node.js 管理 Azure 資源和資源群組](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [將 Azure AD 整合到 NodeJS Web 應用程式中](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
