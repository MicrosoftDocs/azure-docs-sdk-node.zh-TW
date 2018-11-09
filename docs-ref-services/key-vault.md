---
title: 適用於 Node.js 的 Azure Key Vault 模組
description: 適用於 Node.js 的 Azure Key Vault 模組參考
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121847"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="756d7-103">適用於 Node.js 的 Azure Key Vault 模組</span><span class="sxs-lookup"><span data-stu-id="756d7-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="756d7-104">Azure 金鑰保存庫可協助保護雲端應用程式和服務所使用的密碼編譯金鑰和密碼。</span><span class="sxs-lookup"><span data-stu-id="756d7-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="756d7-105">使用金鑰保存庫之後，您可以加密金鑰和密碼 (例如驗證金鑰、儲存體帳戶金鑰、資料加密金鑰、.PFX 檔案和密碼)，方法是使用受硬體安全模組 (HSM) 保護的金鑰。</span><span class="sxs-lookup"><span data-stu-id="756d7-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="756d7-106">為了加強保證，您可以在 HSM 中匯入或產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="756d7-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="756d7-107">如果您選擇這麼做，Microsoft 會在進行過 FIPS 140-2 Level 2 驗證的 HSM (硬體和韌體) 中處理您的金鑰。</span><span class="sxs-lookup"><span data-stu-id="756d7-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="756d7-108">金鑰保存庫簡化了金鑰管理程序，並可讓您控管存取和加密資料的金鑰。</span><span class="sxs-lookup"><span data-stu-id="756d7-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="756d7-109">開發人員可以在幾分鐘內建立開發和測試的金鑰，然後順利地將他們移轉至生產金鑰。</span><span class="sxs-lookup"><span data-stu-id="756d7-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="756d7-110">安全性系統管理員可以視需要授與 (和撤銷) 存取金鑰的權限。</span><span class="sxs-lookup"><span data-stu-id="756d7-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="756d7-111">管理套件</span><span class="sxs-lookup"><span data-stu-id="756d7-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="756d7-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="756d7-112">Install the npm module</span></span> 

<span data-ttu-id="756d7-113">安裝 Azure Key Vault npm 模組</span><span class="sxs-lookup"><span data-stu-id="756d7-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="756d7-114">範例</span><span class="sxs-lookup"><span data-stu-id="756d7-114">Example</span></span>

<span data-ttu-id="756d7-115">此範例會在 Azure 中建立新的 Key Vault 服務。</span><span class="sxs-lookup"><span data-stu-id="756d7-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="756d7-116">範例</span><span class="sxs-lookup"><span data-stu-id="756d7-116">Samples</span></span>

- [<span data-ttu-id="756d7-117">開始在 Node.js 中使用 Key Vault</span><span class="sxs-lookup"><span data-stu-id="756d7-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="756d7-118">使用 Node.js 管理 Azure 資源和資源群組</span><span class="sxs-lookup"><span data-stu-id="756d7-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="756d7-119">將 Azure AD 整合到 NodeJS Web 應用程式中</span><span class="sxs-lookup"><span data-stu-id="756d7-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="756d7-120">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="756d7-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
