---
title: 適用於 Node.js 的 Azure 備份模組
description: 適用於 Node.js 的 Azure 備份模組參考
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 6daeb443c2f1d8560a6a455cb6d174462b483f79
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="f354d-103">適用於 Node.js 的 Azure 備份模組</span><span class="sxs-lookup"><span data-stu-id="f354d-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f354d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="f354d-104">Overview</span></span>

<span data-ttu-id="f354d-105">Azure 備份是您可用來備份 (或保護) 和還原 Microsoft Cloud 資料的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="f354d-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="f354d-106">Azure 備份將以一個可靠、安全及具成本競爭力的雲端架構解決方案，取代您現有的內部部署或異地備份解決方案。</span><span class="sxs-lookup"><span data-stu-id="f354d-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="f354d-107">Azure 備份提供多個元件，您可以下載並部署在適當的電腦、伺服器或雲端中。</span><span class="sxs-lookup"><span data-stu-id="f354d-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="f354d-108">您部署的元件或代理程式，取決於您想要保護的項目。</span><span class="sxs-lookup"><span data-stu-id="f354d-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="f354d-109">所有 Azure 備份的元件 (無論您要保護的是內部部署或雲端資料) 都可以將資料備份至 Azure 中的復原服務保存庫。</span><span class="sxs-lookup"><span data-stu-id="f354d-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="f354d-110">管理封裝</span><span class="sxs-lookup"><span data-stu-id="f354d-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="f354d-111">使用 npm 安裝模組</span><span class="sxs-lookup"><span data-stu-id="f354d-111">Install the modules with npm</span></span>

<span data-ttu-id="f354d-112">使用 npm 來安裝適用於 Node.js 的 Azure 備份模組</span><span class="sxs-lookup"><span data-stu-id="f354d-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="f354d-113">範例</span><span class="sxs-lookup"><span data-stu-id="f354d-113">Example</span></span>

<span data-ttu-id="f354d-114">此範例會列出指定之保存庫與資源群組的復原作業。</span><span class="sxs-lookup"><span data-stu-id="f354d-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="f354d-115">範例</span><span class="sxs-lookup"><span data-stu-id="f354d-115">Samples</span></span>

<span data-ttu-id="f354d-116">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="f354d-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
