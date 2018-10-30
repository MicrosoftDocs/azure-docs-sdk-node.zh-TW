---
title: Azure 上適用於 JavaScript 開發人員的工具 | Microsoft Docs
description: 在 Azure 上安裝適用於 JavaScript 開發的個別工具
services: multiple
author: rloutlaw
manager: routlaw
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/07/2017
ms.author: routlaw
ms.openlocfilehash: 1c676b1f31fde7b14a16031b78f767a2c59edd5a
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "49726663"
---
# <a name="azure-tools-for-javascript-developers"></a><span data-ttu-id="bc285-103">適用於 JavaScript 開發人員的 Azure 工具</span><span class="sxs-lookup"><span data-stu-id="bc285-103">Azure tools for JavaScript developers</span></span>
<span data-ttu-id="bc285-104">建議使用下列工具，在 Azure 上開發 JavaScript 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc285-104">The following tools are recommended for developing JavaScript apps on Azure.</span></span>

## <a name="azure-cli"></a><span data-ttu-id="bc285-105">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="bc285-105">Azure CLI</span></span>
<span data-ttu-id="bc285-106">Azure CLI 已針對從命令列管理 Azure 資源進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="bc285-106">Azure CLI is optimized for managing Azure resources from the command line.</span></span>

![CLI](media/node-azure-tools/cli.png)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="bc285-108">安裝 Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="bc285-108">Install the Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)

## <a name="visual-studio-code"></a><span data-ttu-id="bc285-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bc285-109">Visual Studio Code</span></span>
<span data-ttu-id="bc285-110">在任何作業系統上編輯和偵錯 JavaScript 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc285-110">Edit and debug JavaScript apps on any OS.</span></span>

![Visual Studio Code](media/node-azure-tools/vs-code.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="bc285-112">下載 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bc285-112">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="azure-extensions"></a><span data-ttu-id="bc285-113">Azure 延伸模組</span><span class="sxs-lookup"><span data-stu-id="bc285-113">Azure Extensions</span></span>
<span data-ttu-id="bc285-114">使用下列免費延伸模組作為介面，直接在 Visual Studio Code 中使用 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="bc285-114">Use the following free extensions to interface with Azure services directly in Visual Studio Code.</span></span>

| <span data-ttu-id="bc285-115">工具</span><span class="sxs-lookup"><span data-stu-id="bc285-115">Tool</span></span> | <span data-ttu-id="bc285-116">說明</span><span class="sxs-lookup"><span data-stu-id="bc285-116">Description</span></span>  |
|:---------:|---------|
| [<span data-ttu-id="bc285-117">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="bc285-117">Azure Functions</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) <br> <span data-ttu-id="bc285-118">[![Azure Functions 工具](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span><span class="sxs-lookup"><span data-stu-id="bc285-118">[![Azure Functions Tools](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span></span> | <span data-ttu-id="bc285-119">建立、管理、檢視、偵錯，以及部署函式</span><span class="sxs-lookup"><span data-stu-id="bc285-119">Create, manage, view, debug, and deploy functions</span></span>|
| [<span data-ttu-id="bc285-120">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="bc285-120">Azure App Service</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) <br> <span data-ttu-id="bc285-121">[![App Service 工具](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span><span class="sxs-lookup"><span data-stu-id="bc285-121">[![App Service Tools](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span></span> | <span data-ttu-id="bc285-122">瀏覽網站和 Azure 入口網站、建立新網站並部署到各個位置</span><span class="sxs-lookup"><span data-stu-id="bc285-122">Browse sites and the Azure portal, create new sites and deploy to slots</span></span> |
| [<span data-ttu-id="bc285-123">Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="bc285-123">Cosmos DB </span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)  <br> <span data-ttu-id="bc285-124">[![Cosmos DB 工具](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span><span class="sxs-lookup"><span data-stu-id="bc285-124">[![Cosmos DB Tools](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span></span>| <span data-ttu-id="bc285-125">在 Azure 中建立、瀏覽，並更新散佈全球的多模型資料庫</span><span class="sxs-lookup"><span data-stu-id="bc285-125">Create, browse, and update globally distributed, multi-model databases in Azure</span></span> |
| [<span data-ttu-id="bc285-126">Docker</span><span class="sxs-lookup"><span data-stu-id="bc285-126">Docker</span></span>](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)   <br> <span data-ttu-id="bc285-127">[![Cosmos DB 工具](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span><span class="sxs-lookup"><span data-stu-id="bc285-127">[![Cosmos DB Tools](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span></span>| <span data-ttu-id="bc285-128">管理 Docker 容器和映像、Docker 中樞和 Azure 容器登錄</span><span class="sxs-lookup"><span data-stu-id="bc285-128">Manage Docker containers and images, Docker Hub, and Azure container registry</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="bc285-129">在 Visual Studio Code 市集中取得更多的 Azure 擴充功能</span><span class="sxs-lookup"><span data-stu-id="bc285-129">Get more Azure extensions in the Visual Studio Code marketplace</span></span>](https://marketplace.visualstudio.com/search?term=azure&target=VSCode&category=All%20categories&sortBy=Relevance)