---
title: "適用於 Node.js 的 Azure App Service 模組"
description: "適用於 Node.js 的 Azure App Service 模組參考"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="76254-103">適用於 Node.js 的 Azure App Service 模組</span><span class="sxs-lookup"><span data-stu-id="76254-103">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="76254-104">概觀</span><span class="sxs-lookup"><span data-stu-id="76254-104">Overview</span></span>

<span data-ttu-id="76254-105">Azure App Service 是 Microsoft Azure 的平台即服務 (PaaS) 供應項目。</span><span class="sxs-lookup"><span data-stu-id="76254-105">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="76254-106">建立適用任何平台或裝置的 Web 與行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="76254-106">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="76254-107">整合您的應用程式與 SaaS 解決方案、與內部部署應用程式連接，並使您的商務程序自動化。</span><span class="sxs-lookup"><span data-stu-id="76254-107">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="76254-108">Azure 會使用您選擇的共用 VM 資源或專用 VM，在完全受控的虛擬機器 (VM) 上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="76254-108">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="76254-109">App Service 包含先前以 Azure 網站和 Azure 行動服務的形式來獨立提供的 Web 和行動功能。</span><span class="sxs-lookup"><span data-stu-id="76254-109">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="76254-110">此外，它也包含可用來自動執行商務程序及裝載雲端 API 的新功能。</span><span class="sxs-lookup"><span data-stu-id="76254-110">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="76254-111">App Service 是單一的整合式服務，可讓您將各種元件 (網站、行動應用程式後端、RESTful API 和商務程序) 撰寫成單一解決方案。</span><span class="sxs-lookup"><span data-stu-id="76254-111">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="76254-112">管理套件</span><span class="sxs-lookup"><span data-stu-id="76254-112">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="76254-113">安裝 npm 套件</span><span class="sxs-lookup"><span data-stu-id="76254-113">Install the npm package</span></span>

<span data-ttu-id="76254-114">安裝適用於 Node.js 的 Azure App Service 模組</span><span class="sxs-lookup"><span data-stu-id="76254-114">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="76254-115">範例</span><span class="sxs-lookup"><span data-stu-id="76254-115">Example</span></span>

<span data-ttu-id="76254-116">此範例會使用 Node.js 在 Azure 上建立網站。</span><span class="sxs-lookup"><span data-stu-id="76254-116">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="76254-117">範例</span><span class="sxs-lookup"><span data-stu-id="76254-117">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="76254-118">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="76254-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
