---
title: "使用 Azure 資料庫搭配 Node.js 的範例程式碼"
description: "說明如何使用 Azure 資料庫搭配 Node.js 的範例程式碼。"
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="aca4a-103">使用 Azure 資料庫搭配 Node.js 的範例程式碼</span><span class="sxs-lookup"><span data-stu-id="aca4a-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="aca4a-104">下列範例程式碼說明如何使用 Azure 資料庫搭配 Node.js。</span><span class="sxs-lookup"><span data-stu-id="aca4a-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="aca4a-105">如果您需要其他工作的程式碼，您可以瀏覽 [Azure Node.js 範例](https://azure.microsoft.com/resources/samples/?term=nodejs)的完整清單。</span><span class="sxs-lookup"><span data-stu-id="aca4a-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="aca4a-106">**Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="aca4a-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="aca4a-107">使用 Azure Cosmos DB 和圖形 API</span><span class="sxs-lookup"><span data-stu-id="aca4a-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="aca4a-108">說明如何使用 Azure Cosmos DB 搭配圖形 API，從 Node.js 應用程式儲存和存取資料。</span><span class="sxs-lookup"><span data-stu-id="aca4a-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="aca4a-109">使用 Azure Cosmos DB 和 Document DB API</span><span class="sxs-lookup"><span data-stu-id="aca4a-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="aca4a-110">說明如何使用 Azure Cosmos DB 搭配 DocumentDB API，從 Node.js 應用程式儲存和存取資料。</span><span class="sxs-lookup"><span data-stu-id="aca4a-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="aca4a-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="aca4a-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="aca4a-112">使用 DocumentDB 透過 Node.js 與 Express 進行 Web 應用程式開發</span><span class="sxs-lookup"><span data-stu-id="aca4a-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="aca4a-113">說明如何使用 Azure DocumentDB，從 Azure 上的 Node.js Express 應用程式儲存和存取資料。</span><span class="sxs-lookup"><span data-stu-id="aca4a-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="aca4a-114">使用 DocumentDB 部署 Node.js 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="aca4a-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="aca4a-115">此範例示範如何快速開始使用 Microsoft Azure DocumentDB 服務和 Node.js。</span><span class="sxs-lookup"><span data-stu-id="aca4a-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="aca4a-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="aca4a-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="aca4a-117">Azure 中的 Node.js 和 MongoDB Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="aca4a-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="aca4a-118">您可以遵循本教學課程用於[在 Azure 中建置 Node.js 和 MongoDB web 應用程式](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json)的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="aca4a-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="aca4a-119">**SQL Database**</span><span class="sxs-lookup"><span data-stu-id="aca4a-119">**SQL Database**</span></span> ||
| [<span data-ttu-id="aca4a-120">Azure SQL Database︰使用 Node.js 連線及查詢資料</span><span class="sxs-lookup"><span data-stu-id="aca4a-120">Azure SQL Database: Use Node.js to connect and query data</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | <span data-ttu-id="aca4a-121">示範如何使用 Node.js 連線至 Azure SQL Database，然後從 Windows、Ubuntu Linux 和 Mac 平台使用 Transact-SQL 陳述式來查詢、插入、更新和刪除資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="aca4a-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |