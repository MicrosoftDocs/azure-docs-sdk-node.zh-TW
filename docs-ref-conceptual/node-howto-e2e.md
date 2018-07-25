---
title: 使用 Visual Studio Code 和 Azure 進行 Node.js 開發
description: 完整的端對端教學課程說明如何建立 Node.js 應用程式、將其 Docker 化及部署到 Azure
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
ms.locfileid: "20908138"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="30632-103">使用 Visual Studio Code 和 Azure 進行 Node.js 開發</span><span class="sxs-lookup"><span data-stu-id="30632-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="30632-104">本教學課程說明如何採用現有的 Node.js 應用程式，將它「容器化」 (使用 Docker)，然後使用 Visual Studio Code 將應用程式部署至 Azure。</span><span class="sxs-lookup"><span data-stu-id="30632-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="30632-105">本教學課程會使用 [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) 所建立及發佈的簡單待辦事項應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="30632-106">它是單一頁面的 MEAN 應用程式，因此會使用 MongoDB 作為其資料庫，Node/Express 作為其 REST API/Web 伺服器，以及 Angular.js 1.x 作為前端 UI。</span><span class="sxs-lookup"><span data-stu-id="30632-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="30632-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="30632-107">Prerequisites</span></span>

<span data-ttu-id="30632-108">若要依照示範操作，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="30632-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="30632-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="30632-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="30632-110">Docker</span><span class="sxs-lookup"><span data-stu-id="30632-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="30632-111">DockerHub 帳戶</span><span class="sxs-lookup"><span data-stu-id="30632-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="30632-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="30632-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="30632-113">Azure 帳戶</span><span class="sxs-lookup"><span data-stu-id="30632-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="30632-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="30632-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="30632-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - 用於對示範應用程式的前端進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="30632-116">MongoDB - 由於示範應用程式會使用 MongoDB，所以您必須有在本機執行並接聽標準 `27017` 連接埠的 MongoDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="30632-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="30632-117">安裝 Docker 之後，執行下列兩個命令是達成此目的的最簡單方式：依序執行 `docker pull mongo` 和 `docker run -it -p 27017:27017 mongo`。</span><span class="sxs-lookup"><span data-stu-id="30632-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="30632-118">專案設定</span><span class="sxs-lookup"><span data-stu-id="30632-118">Project setup</span></span>

<span data-ttu-id="30632-119">若要開始進行，請使用下列步驟下載範例專案：</span><span class="sxs-lookup"><span data-stu-id="30632-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="30632-120">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="30632-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="30632-121">按 **&lt;F1>** 以顯示命令選擇區。</span><span class="sxs-lookup"><span data-stu-id="30632-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="30632-122">在命令選擇區提示字元，輸入 `gitcl`，選取 **Git: Clone** 命令，然後按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="30632-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Visual Studio Code 命令選擇區提示字元中的 gitcl 命令](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="30632-124">當系統提示您輸入 [存放庫 URL] 時，輸入 `https://github.com/scotch-io/node-todo`，然後按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="30632-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="30632-125">選取 (或建立) 要將專案複製到其中的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="30632-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Visual Studio Code 總管](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="30632-127">整合式終端機</span><span class="sxs-lookup"><span data-stu-id="30632-127">Integrated terminal</span></span>

<span data-ttu-id="30632-128">由於這是一個 Node.js 專案，所以您需要做的第一件事就是確定已從 npm 安裝專案的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="30632-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="30632-129">按 **&lt;Ctrl>\`** 以顯示 Visual Studio Code 整合式終端機。</span><span class="sxs-lookup"><span data-stu-id="30632-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="30632-130">輸入 `yarn`，然後按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="30632-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![在 Visual Studio Code 中執行 yarn 命令](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="30632-132">整合式 Git 版本控制</span><span class="sxs-lookup"><span data-stu-id="30632-132">Integrated Git version control</span></span>

<span data-ttu-id="30632-133">透過 Yarn 安裝應用程式的相依性之後，就會建立 `yarn.lock` 檔案來提供可預測的方式，以在未來重新取得完全相同的相依性，而 CI (連續整合) 組建、生產部署或其他開發人員電腦都在意料之中。</span><span class="sxs-lookup"><span data-stu-id="30632-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="30632-134">下列步驟說明如何將 `yarn.lock` 檔案簽入原始檔控制中：</span><span class="sxs-lookup"><span data-stu-id="30632-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="30632-135">在 Visual Studio Code 中，切換至整合式 Git 索引標籤 (包含 Git 標誌的索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="30632-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="30632-136">在 [訊息] 方塊中，輸入認可訊息，並且按 **&lt;Ctrl>&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="30632-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![將 yarn.lock 檔案新增至 Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="30632-138">專案和程式碼瀏覽</span><span class="sxs-lookup"><span data-stu-id="30632-138">Project and code navigation</span></span>

<span data-ttu-id="30632-139">讓我們示範 Visual Studio Code 所提供之巡覽功能的一些範例，以便我們自己熟悉程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="30632-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="30632-140">按 **&lt;Ctrl>P**。</span><span class="sxs-lookup"><span data-stu-id="30632-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="30632-141">輸入 `.js`，以顯示專案中的所有 JavaScript/JSON 檔案，以及每個檔案的上層目錄</span><span class="sxs-lookup"><span data-stu-id="30632-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![顯示所有 .js\* 檔案](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="30632-143">選取 `server.js`，這是應用程式的啟動指令碼。</span><span class="sxs-lookup"><span data-stu-id="30632-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="30632-144">將滑鼠停留在 **database** 變數上 (已匯入於第 6 行)，以查看其類型。</span><span class="sxs-lookup"><span data-stu-id="30632-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="30632-145">在您專案的開發期間，快速檢查檔案中變數/模組/類型的這項功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="30632-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![探索類型](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="30632-147">在變數 (例如 **database**) 的範圍內按一下滑鼠，可讓您查看相同檔案中該變數的所有參考。</span><span class="sxs-lookup"><span data-stu-id="30632-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="30632-148">若要檢視專案內變數的所有參考，以滑鼠右鍵按一下變數，並從操作功能表中選取 [尋找所有參考]。</span><span class="sxs-lookup"><span data-stu-id="30632-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![尋找變數的參考](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="30632-150">除了將滑鼠停留在變數來探索其類型，您也可以檢查定義的變數 (即使它在另一個檔案中)。</span><span class="sxs-lookup"><span data-stu-id="30632-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="30632-151">若要查看實際作業情形，以滑鼠右鍵按一下 **database.localUrl** (第 12 行)，然後從操作功能表中選取 [預覽定義]。</span><span class="sxs-lookup"><span data-stu-id="30632-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![預覽變數的定義](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="30632-153">修改程式碼並使用自動完成功能</span><span class="sxs-lookup"><span data-stu-id="30632-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="30632-154">MongoDB 連接字串已硬式編碼在 **database.localUrl** 的宣告中。</span><span class="sxs-lookup"><span data-stu-id="30632-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="30632-155">在本節中，您將修改程式碼以從環境變數擷取連接字串，並了解 Visual Studio Code 的自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="30632-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="30632-156">開啟 `server.js` 檔案</span><span class="sxs-lookup"><span data-stu-id="30632-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="30632-157">將下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="30632-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="30632-158">取代為此程式碼：</span><span class="sxs-lookup"><span data-stu-id="30632-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="30632-159">請注意，如果您以手動方式輸入程式碼 (而不是複製並貼上)，則當您在 `process` 之後輸入句點後，Visual Studio Code 會顯示 Node.js **process** 全域 API 的可用成員。</span><span class="sxs-lookup"><span data-stu-id="30632-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![自動完成功能會自動顯示 API 的成員](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="30632-161">自動完成功能有作用，因為 Visual Studio Code 在幕後使用 TypeScript (即使針對 JavaScript) 來提供類型資訊，而該資訊可接著在您輸入資料時用於告知完成清單。</span><span class="sxs-lookup"><span data-stu-id="30632-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="30632-162">Visual Studio Code 能夠偵測這是 Node.js 專案，因此會從 [NPM](https://www.npmjs.com/package/@types/node) 自動下載 Node.js 的 TypeScript typings 檔案。</span><span class="sxs-lookup"><span data-stu-id="30632-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="30632-163">typings 檔案可讓您取得其他 Node.js globals (例如 **Buffer** 和 **setTimeout**) 的自動完成功能，以及所有內建的模組 (例如 **fs** 和 **http**)。</span><span class="sxs-lookup"><span data-stu-id="30632-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="30632-164">除了內建 Node.js API 以外，此自動取得的 typings 也適用於超過 2,000 個第 3 方模組，例如 React、Underscore 和 Express。</span><span class="sxs-lookup"><span data-stu-id="30632-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="30632-165">例如，當 Mongoose 無法連線到已設定的 MongoDB 資料庫執行個體時，若要讓它免於損毀範例應用程式，請在第 13 行插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="30632-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="30632-166">如同先前的程式碼，您會發現您不需執行任何動作，即可取得自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="30632-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![自動完成功能會自動顯示 API 的成員](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="30632-168">您可瀏覽 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 專案 (這是所有 TypeScript 類型定義的社群導向來源)，以查看哪些模組支援此自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="30632-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="30632-169">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="30632-169">Running the app</span></span>

<span data-ttu-id="30632-170">一旦瀏覽過程式碼，您就可以執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="30632-171">若要從 Visual Studio Code 執行應用程式，請按 **&lt;F5>**。</span><span class="sxs-lookup"><span data-stu-id="30632-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="30632-172">透過  **&lt;F5>** 執行程式碼 (偵錯模式) 時，Visual Studio Code 會啟動應用程式並顯示 [偵錯主控台] 視窗，進而顯示應用程式的 stdout。</span><span class="sxs-lookup"><span data-stu-id="30632-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![透過偵錯主控台監視應用程式的 stdout](./media/node-howto-e2e/console.png)

<span data-ttu-id="30632-174">此外，[偵錯主控台] 會附加至新執行的應用程式，以便您輸入 JavaScript 運算式 (將在應用程式中評估)，而且還包含自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="30632-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="30632-175">若要查看實際作業情形，請在主控台中輸入 `process.env`：</span><span class="sxs-lookup"><span data-stu-id="30632-175">To see this in action, type `process.env` in the console:</span></span>

![在偵錯主控台中輸入程式碼](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="30632-177">因為目前開啟的檔案是 JavaScript 檔案 (`server.js`)，所以您可按 **&lt;F5>** 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="30632-178">因此，Visual Studio Code 假設此專案是 Node.js 應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="30632-179">如果您關閉 Visual Studio Code 中所有的 JavaScript 檔案，然後按 **&lt;F5>**，Visual Studio Code 會查詢您的環境：</span><span class="sxs-lookup"><span data-stu-id="30632-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![指定執行階段環境](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="30632-181">開啟瀏覽器並瀏覽至 `http://localhost:8080`，以查看執行中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="30632-182">在文字方塊中輸入訊息並新增/移除一些待辦事項，感受一下應用程式的運作方式。</span><span class="sxs-lookup"><span data-stu-id="30632-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![執行中的待辦事項應用程式](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="30632-184">Debugging</span><span class="sxs-lookup"><span data-stu-id="30632-184">Debugging</span></span>

<span data-ttu-id="30632-185">除了能夠執行應用程式並透過整合式主控台與其互動，Visual Studio Code 還可供直接在程式碼內設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="30632-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="30632-186">例如，按 **&lt;Ctrl>P** 可顯示檔案選擇器。</span><span class="sxs-lookup"><span data-stu-id="30632-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="30632-187">檔案選擇器顯示後，輸入 `route`，然後選取 `route.js` 檔案。</span><span class="sxs-lookup"><span data-stu-id="30632-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="30632-188">在第 28 行上設定中斷點，其代表應用程式嘗試新增待辦項目時呼叫的 Express 路由。</span><span class="sxs-lookup"><span data-stu-id="30632-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="30632-189">若要設定中斷點，只要在編輯器中按一下行號左邊的區域，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="30632-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![在 Visual Studio Code 中設定中斷點](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="30632-191">除了標準中斷點以外，Visual Studio Code 還支援條件式中斷點，這可讓您自訂應用程式何時應該暫停執行。</span><span class="sxs-lookup"><span data-stu-id="30632-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="30632-192">若要設定條件式中斷點，請以滑鼠右鍵按一下要暫停執的行左邊的區域，選取 [新增條件式中斷點...]，並指定 JavaScript 運算式 (例如 `foo = "bar"`) 或執行計數，以定義您要暫停執行的條件。</span><span class="sxs-lookup"><span data-stu-id="30632-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="30632-193">一旦設定中斷點，請回到執行中的應用程式並新增待辦項目。</span><span class="sxs-lookup"><span data-stu-id="30632-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="30632-194">立即新增待辦項目會導致應用程式在您設定中斷點的第 28 行暫停執行：</span><span class="sxs-lookup"><span data-stu-id="30632-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code 在中斷點暫停執行](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="30632-196">應用程式一旦暫停，您即可將滑鼠停留在程式碼的運算式上，以檢視其目前的值、檢查區域變數/監看式並呼叫堆疊，以及使用偵錯工具列來逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="30632-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="30632-197">按 **&lt;F5>** 以繼續執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="30632-198">完整堆疊的偵錯</span><span class="sxs-lookup"><span data-stu-id="30632-198">Full-stack debugging</span></span>

<span data-ttu-id="30632-199">如本主題稍早所述，TODO 應用程式是 MEAN 應用程式 - 也就是說，同時使用 JavaScript 撰寫其前端和後端。</span><span class="sxs-lookup"><span data-stu-id="30632-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="30632-200">因此，當您正在進行後端 (Node/Express) 程式碼的偵錯時，有些時候，您可能需要進行前端 (Angular) 程式碼的偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="30632-201">基於這個目的，Visual Studio Code 有很大的擴充功能生態系統，包括整合式 Chrome 偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="30632-202">切換至 [擴充功能] 索引標籤，然後在搜尋方塊中輸入 `chrome`：</span><span class="sxs-lookup"><span data-stu-id="30632-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Visual Studio Code 的 Chrome 偵錯擴充功能](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="30632-204">選取名為 [Chrome 偵錯工具] 的擴充功能，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="30632-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="30632-205">安裝 Chrome 偵錯擴充功能之後，請選取 [重新載入] 以關閉並重新開啟 Visual Studio Code，進而啟用擴充功能。</span><span class="sxs-lookup"><span data-stu-id="30632-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![在安裝 Chrome 偵錯擴充功能之後重新載入 Visual Studio Code](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="30632-207">隨然您可以在任何 Visual Studio Code 專屬組態的情況下，執行 Node.js 程式碼並進行偵錯，但為了進行前端 Web 應用程式的偵錯，您必須產生 `launch.json` 檔案，以指示 Visual Studio Code 如何執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="30632-208">若要產生 `launch.json` 檔案，請切換至 [偵錯] 索引標籤，按一下齒輪圖示 (其頂端應該會有小紅點)，然後選取 **node.js** 環境。</span><span class="sxs-lookup"><span data-stu-id="30632-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![用來設定 launch.json 檔案的 Visual Studio Code 選項](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="30632-210">所建立的 `launch.json` 檔案會如下所示，並且告知 Visual Studio Code 如何啟動及/或附加至應用程式，才能進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

<span data-ttu-id="30632-211">請注意，Visual Studio Code 能夠偵測到應用程式的啟動指令碼為 `server.js`。</span><span class="sxs-lookup"><span data-stu-id="30632-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="30632-212">開啟 `launch.json` 檔案後，選取 [新增組態] \(右下方)，然後選取 [Chrome：使用 userDataDir 啟動]。</span><span class="sxs-lookup"><span data-stu-id="30632-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![將 Chrome 組態新增至 Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="30632-214">為 Chrome 新增的執行組態可讓您進行前端 JavaScript 程式碼的偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="30632-215">您可以將滑鼠停留在任何指定的設定上，以檢視設定功能說明的相關文件。</span><span class="sxs-lookup"><span data-stu-id="30632-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="30632-216">此外，請注意，Visual Studio Code 會自動偵測應用程式的 URL。</span><span class="sxs-lookup"><span data-stu-id="30632-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="30632-217">將 **webRoot** 屬性更新為 `${workspaceRoot}/public`，讓 Chrome 偵錯工具知道如何找到應用程式的前端資產：</span><span class="sxs-lookup"><span data-stu-id="30632-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

<span data-ttu-id="30632-218">若要同時啟動/偵錯前端與後端，您需要建立「複合」執行組態，以告知 Visual Studio Code 哪一組組態會平行執行。</span><span class="sxs-lookup"><span data-stu-id="30632-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="30632-219">新增下列程式碼片段作為 `launch.json` 檔案中的最上層屬性 (作為現有 **configurations** 屬性的同層級)。</span><span class="sxs-lookup"><span data-stu-id="30632-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="30632-220">在 **compounds.configurations** 陣列中指定的字串值是指 **configurations** 清單中個別項目的 **name**。</span><span class="sxs-lookup"><span data-stu-id="30632-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="30632-221">如果您已修改這些名稱，您必須在陣列中進行適當的變更。</span><span class="sxs-lookup"><span data-stu-id="30632-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="30632-222">若要查看實際作業情形，切換至 [偵錯] 索引標籤，將所選取的組態變更為 [完整堆疊] \(複合組態的名稱)，然後按 **&lt;F5>** 加以執行。</span><span class="sxs-lookup"><span data-stu-id="30632-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![在 Visual Studio Code 中執行組態](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="30632-224">執行組態可啟動 Node.js 應用程式 (如偵錯主控台輸出所示) 和 Chrome (已設定為瀏覽至位於 `http://localhost:8080` 的 Node.js 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="30632-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="30632-225">按 **&lt;Ctrl>P**，然後輸入 (或選取) `todos.js`，這是應用程式前端的主要 Angular 控制器。</span><span class="sxs-lookup"><span data-stu-id="30632-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="30632-226">在第 11 行上設定中斷點，這是所建立之新待辦項目的進入點。</span><span class="sxs-lookup"><span data-stu-id="30632-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="30632-227">返回執行中的應用程式、新增待辦項目，並請注意 Visual Studio Code 現在已在 Angular 程式碼內暫停執行。</span><span class="sxs-lookup"><span data-stu-id="30632-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![在 Visual Studio Code 中進行前端程式碼的偵測](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="30632-229">如同 Node.js 偵錯，您可以將滑鼠停留在運算式上、檢視區域變數/監看式、在主控台中評估運算式等等。</span><span class="sxs-lookup"><span data-stu-id="30632-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="30632-230">有兩個值得注意的重點：</span><span class="sxs-lookup"><span data-stu-id="30632-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="30632-231">[呼叫堆疊] 窗格會顯示兩個不同的堆疊：**Node** 和 **Chrome**，並指出哪個堆疊目前暫停。</span><span class="sxs-lookup"><span data-stu-id="30632-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="30632-232">您可以在前端與後端程式碼之間徘徊。</span><span class="sxs-lookup"><span data-stu-id="30632-232">You can step between front and back-end code.</span></span> <span data-ttu-id="30632-233">若要測試此功能，請按 **&lt;F5>**，以執行和叫用先前在 Express 路由中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="30632-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="30632-234">使用此設定，您現在可以直接在 Visual Studio Code 中有效地進行前端、後端或完整堆疊 JavaScript 程式碼的偵錯。</span><span class="sxs-lookup"><span data-stu-id="30632-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="30632-235">此外，複合偵錯工具概念不限於只有兩個目標程序，而且也不只限於 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="30632-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="30632-236">因此，如果適用於微服務應用程式 (可能是 polyglot)，您可以使用完全相同的工作流程 (安裝適當的語言/架構擴充功能後)。</span><span class="sxs-lookup"><span data-stu-id="30632-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="30632-237">將應用程式 Docker 化</span><span class="sxs-lookup"><span data-stu-id="30632-237">Dockerizing the app</span></span>

<span data-ttu-id="30632-238">本節著重於 Visual Studio Code 針對使用 [Docker](https://www.docker.com/) 進行開發所提供的經驗。</span><span class="sxs-lookup"><span data-stu-id="30632-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="30632-239">Node.js 開發人員會使用 Docker 提供適用於開發、CI (連續整合) 和生產環境的可攜式應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="30632-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="30632-240">當 Docker 呈現陡峭的學習曲線時，Visual Studio Code 會提供擴充功能，試著協助簡化在應用程式中使用 Docker。</span><span class="sxs-lookup"><span data-stu-id="30632-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="30632-241">切換回 [擴充功能] 索引標籤，搜尋 `docker`，然後選取 **Docker** 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="30632-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="30632-242">安裝 Docker 擴充功能，然後重新載入 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="30632-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![安裝適用於 Visual Studio Code 的 Docker 擴充功能](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="30632-244">適用於 Visual Studio Code 的 Docker 擴充功能包含針對現有專案產生 *Dockerfile* 和 `docker-compose.yml` 檔案的命令。</span><span class="sxs-lookup"><span data-stu-id="30632-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="30632-245">若要查看可用的 Docker 命令，請顯示命令選擇區 (透過 **&lt;F1>**) 並輸入 `docker`。</span><span class="sxs-lookup"><span data-stu-id="30632-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="30632-246">適用於 Visual studio 的 Docker 擴充功能所支援的命令</span><span class="sxs-lookup"><span data-stu-id="30632-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="30632-247">選取 [Docker：將 Docker 檔案新增到工作區]，選取 **Node.js** 作為應用程式平台，並指定應用程式公開連接埠 `8080`。</span><span class="sxs-lookup"><span data-stu-id="30632-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="30632-248">Docker 命令會產生您可立即開始使用的完整 `Dockerfile` 和 Docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="30632-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![所產生的 Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="30632-250">Docker 擴充功能也會為 `Dockerfiles` 和 `docker-compose.yml` 檔案提供自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="30632-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="30632-251">若要查看實際作業情形，請開啟 `Dockerfile` 並將第 2 行從：</span><span class="sxs-lookup"><span data-stu-id="30632-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="30632-252">變更為：</span><span class="sxs-lookup"><span data-stu-id="30632-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="30632-253">將游標放在 `mhart` 中的 `t` 之後，按 **&lt;Ctrl>&lt;Space>** 以檢視 `mhart` 在 DockerHub 上發佈的所有映像存放庫。</span><span class="sxs-lookup"><span data-stu-id="30632-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Docker 擴充功能自動完成](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="30632-255">選取 `mhart/alpine-node`，這會提供此應用程式需要的所有項目。</span><span class="sxs-lookup"><span data-stu-id="30632-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="30632-256">較小的映像通常比較適當，因為您希望應用程式的建置和部署愈快愈好，而讓散發和調整更加快速。</span><span class="sxs-lookup"><span data-stu-id="30632-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="30632-257">此時，您已產生 `Dockerfile`，您必須建立實際的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="30632-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="30632-258">同樣地，您可以使用 Docker 擴充功能安裝在 Visual Studio Code 中的命令。</span><span class="sxs-lookup"><span data-stu-id="30632-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="30632-259">按 **&lt;F1>**，在命令選擇區輸入 `dockerb`，然後選取 [Docker：建置映像] 命令。</span><span class="sxs-lookup"><span data-stu-id="30632-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="30632-260">選擇您剛產生及修改的 `/Dockerfile`。</span><span class="sxs-lookup"><span data-stu-id="30632-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="30632-261">指定包含您的 DockerHub 使用者名稱的標籤 (例如 `lostintangent/node`)。</span><span class="sxs-lookup"><span data-stu-id="30632-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="30632-262">按 **&lt;ENTER>** 以啟動整合式終端機視窗，以顯示正在建立的 Docker 映像輸出。</span><span class="sxs-lookup"><span data-stu-id="30632-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Docker 映像組建狀態](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="30632-264">請注意，此命令會為您自動執行 `docker build`，這是您可以選擇使用的另一個生產力加強程式範例，或者您可以直接使用 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="30632-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="30632-265">此時，若要讓此映像可輕鬆取得以供部署，您只需要將映像推送至 DockerHub。</span><span class="sxs-lookup"><span data-stu-id="30632-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="30632-266">若要這麼做，請確定您已藉由從 CLI 執行 `docker login` 並輸入您的帳戶認證，向 DockerHub 驗證。</span><span class="sxs-lookup"><span data-stu-id="30632-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="30632-267">然後，在 Visual Studio Code 中，您可以啟動命令選擇區，輸入 `dockerpush`，然後選取 `Docker: Push` 命令。</span><span class="sxs-lookup"><span data-stu-id="30632-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="30632-268">選取您剛才建立的映像標籤 (例如 `lostintangent/node`)，然後按 **&lt;Enter>**。</span><span class="sxs-lookup"><span data-stu-id="30632-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="30632-269">此命令會自動呼叫 `docker push` 並在整合式終端機中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="30632-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="30632-270">部署應用程式</span><span class="sxs-lookup"><span data-stu-id="30632-270">Deploying the app</span></span>

<span data-ttu-id="30632-271">既然您已將應用程式 Docker 化並推送至 DockerHub，您就必須將它部署到雲端，以便全世界可以看到它。</span><span class="sxs-lookup"><span data-stu-id="30632-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="30632-272">為此，您可以使用 Azure App Service (這是 Azure 的 PaaS 供應項目)。</span><span class="sxs-lookup"><span data-stu-id="30632-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="30632-273">App Service 有兩項與 Node.js 開發人員相關的功能：</span><span class="sxs-lookup"><span data-stu-id="30632-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="30632-274">支援以 Linux 為基礎的 VM，這可減少使用原生 Node 模組建置的應用程式，或其他可能不支援 Windows 和/或運作方式不同的工具發生不相容的情形。</span><span class="sxs-lookup"><span data-stu-id="30632-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="30632-275">支援以 Docker 為基礎的部署，這可讓您指定 Docker 映像的名稱，並允許 App Service 提取、部署及自動縮放影像。</span><span class="sxs-lookup"><span data-stu-id="30632-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="30632-276">若要開始使用，請開啟 Visual Studio 終端機。</span><span class="sxs-lookup"><span data-stu-id="30632-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="30632-277">您將使用新的 Azure CLI 2.0 來管理 Azure 帳戶及佈建執行待辦事項應用程式所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="30632-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="30632-278">使用 `az login` 命令從 CLI 登入您的帳戶 (如必要條件所述) 後，請執行下列步驟來佈建 App Service 執行個體及部署待辦事項應用程式容器：</span><span class="sxs-lookup"><span data-stu-id="30632-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="30632-279">建立資源群組，您可以將它視為有助於組織 Azure 資源的「命名空間」或「目錄」。</span><span class="sxs-lookup"><span data-stu-id="30632-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="30632-280">`-n` 選項用來指定您想要的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="30632-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="30632-281">`-l` 選項表示資源群組的位置。</span><span class="sxs-lookup"><span data-stu-id="30632-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="30632-282">在預覽期間，Linux 上的 App Service 支援僅適用於精選的區域。</span><span class="sxs-lookup"><span data-stu-id="30632-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="30632-283">因此，如果您不是位於美國西部，而且要查看有其他哪些區域可用，請從 CLI 執行 `az appservice list-locations --linux-workers-enabled` 以檢視您的資料中心選項。</span><span class="sxs-lookup"><span data-stu-id="30632-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="30632-284">將新建立的資源群組設定為預設資源群組，您便可以繼續使用 CLI，而不需要在每個呼叫中明確指定資源群組：</span><span class="sxs-lookup"><span data-stu-id="30632-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="30632-285">建立 App Service *方案*，其可管理應用程式部署所在基礎虛擬機器的建立和調整。</span><span class="sxs-lookup"><span data-stu-id="30632-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="30632-286">同樣地，指定您想要的任何 `n` 選項值。</span><span class="sxs-lookup"><span data-stu-id="30632-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="30632-287">--is-linux 選項表示您想要以 Linux 為基礎的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="30632-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="30632-288">若是沒有，CLI 會預設為佈建以 Windows 為基礎的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="30632-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="30632-289">建立 App Service Web 應用程式，代表將在剛建立的方案和資源群組內執行的實際待辦事項應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="30632-290">您可以將 Web 應用程式視為程序或容器的同義詞，而將方案視為 Web 應用程式執行所在的虛擬機器/容器主機。</span><span class="sxs-lookup"><span data-stu-id="30632-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="30632-291">此外，建立 Web 應用程式時，您需要將它設定為使用您發佈至 DockerHub 的 Docker 映像：</span><span class="sxs-lookup"><span data-stu-id="30632-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="30632-292">若不使用自訂容器，您寧可使用 Git 部署，請參閱[在 Azure 中建立 Node.js Web 應用程式](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs)一文。</span><span class="sxs-lookup"><span data-stu-id="30632-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="30632-293">將 Web 應用程式設定為預設 Web 執行個體：</span><span class="sxs-lookup"><span data-stu-id="30632-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="30632-294">啟動應用程式，以檢視已部署的容器 (將會在 `*.azurewebsites.net` URL 提供)：</span><span class="sxs-lookup"><span data-stu-id="30632-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![在瀏覽器中執行的待辦事項應用程式](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="30632-296">第一次可能需要幾分鐘才能載入應用程式，因為 App Service 必須從 DockerHub 提取 Docker 映像，然後加以啟動。</span><span class="sxs-lookup"><span data-stu-id="30632-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="30632-297">此時，您才剛部署並執行待辦事項應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="30632-298">您現在已部署待辦事項應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-298">You have now deployed the todo app.</span></span> <span data-ttu-id="30632-299">不過，轉圈圖示表示應用程式無法連線到資料庫。</span><span class="sxs-lookup"><span data-stu-id="30632-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="30632-300">這是因為您在開發期間使用了 MongoDB 的本機執行個體，這顯然無法從 Azure 資料中心觸達。</span><span class="sxs-lookup"><span data-stu-id="30632-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="30632-301">因為您將應用程式修改為透過環境變數接受連接字串，所以您只需要啟動 MongoDB 伺服器並重新設定 App Service 執行個體來參考環境變數。</span><span class="sxs-lookup"><span data-stu-id="30632-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="30632-302">下一節會提供相關說明。</span><span class="sxs-lookup"><span data-stu-id="30632-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="30632-303">佈建 MongoDB 伺服器</span><span class="sxs-lookup"><span data-stu-id="30632-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="30632-304">雖然您可以設定 MongoDB 伺服器或複本集，並自行管理基礎結構，但 Azure 會提供一個名為 [Cosmos DB](https://azure.microsoft.com/services/documentdb/) 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="30632-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="30632-305">Cosmos DB 是完全受管理、可異地複寫、高效能並可提供 MongoDB 相容性層級的 NoSQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="30632-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="30632-306">這表示您可以指向其上的現有 MEAN 應用程式 (或任何 MongoDB 用戶端/工具，例如 [Studio 3T](https://studio3t.com/))，而不需變更連接字串以外的任何項目。</span><span class="sxs-lookup"><span data-stu-id="30632-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="30632-307">下列步驟說明如何達成：</span><span class="sxs-lookup"><span data-stu-id="30632-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="30632-308">從 Visual Studio Code 終端機，執行下列命令以建立與 MongoDB 相容的 Cosmos DB 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="30632-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="30632-309">以全域唯一的值取代 **<NAME>** 預留位置 (Cosmos DB 會使用此名稱來產生資料庫的伺服器 URL)：</span><span class="sxs-lookup"><span data-stu-id="30632-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="30632-310">擷取此執行個體的 MongoDB 連接字串：</span><span class="sxs-lookup"><span data-stu-id="30632-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="30632-311">更新 Web 應用程式的 **MONGODB_URL** 環境變數，讓它連線到新佈建的 Cosmos DB 執行個體，而不是嘗試連線到在本機執行的 MongoDB 伺服器 (這不存在！)：</span><span class="sxs-lookup"><span data-stu-id="30632-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="30632-312">返回您的瀏覽器並予以重新整理。</span><span class="sxs-lookup"><span data-stu-id="30632-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="30632-313">嘗試新增和移除待辦項目，證明應用程式現在運作正常，而不需要變更任何項目！</span><span class="sxs-lookup"><span data-stu-id="30632-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="30632-314">將環境變數設定為已建立的 Cosmos DB 執行個體，這完全模擬 MongoDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="30632-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![連線到資料庫之後的示範應用程式](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="30632-316">如有需要，您可以切換回 Cosmos DB 執行個體並相應增加 (或減少) MongoDB 執行個體所需的保留輸送量，並受惠於新增的流量，而不需要手動管理任何基礎結構。</span><span class="sxs-lookup"><span data-stu-id="30632-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="30632-317">此外，Cosmos DB 會自動為您編製每份文件和每個屬性的索引。</span><span class="sxs-lookup"><span data-stu-id="30632-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="30632-318">如此一來，您就不需要剖析較慢的查詢，或手動微調您的索引。</span><span class="sxs-lookup"><span data-stu-id="30632-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="30632-319">只要視需要進行佈建和調整，讓 Cosmos DB 處理其他事宜。</span><span class="sxs-lookup"><span data-stu-id="30632-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="30632-320">裝載私人 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="30632-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="30632-321">DockerHub 針對散佈容器映像提供令人讚嘆的經驗，但有些情況下您寧可裝載自己的私人 Docker 登錄 - 例如為了安全性/控管或效能優勢。</span><span class="sxs-lookup"><span data-stu-id="30632-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="30632-322">基於此目的，Azure 提供可讓您加速自有 Docker 登錄的 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR)，其支援儲存體位於與您的 Web 應用程式相同的資料中心 (讓提取更加快速)。</span><span class="sxs-lookup"><span data-stu-id="30632-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="30632-323">ACR 也為您提供完整的內容和存取控制權 - 例如誰可以推送或提取映像。</span><span class="sxs-lookup"><span data-stu-id="30632-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="30632-324">執行下列命令即可完成自訂登錄的佈建。</span><span class="sxs-lookup"><span data-stu-id="30632-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="30632-325">(以全域唯一的值取代 **<NAME>** 預留位置，因為 ACE 會使用指定的值來產生登錄的登入伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="30632-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="30632-326">為了簡單起見，雖然本主題的範例使用**系統管理員帳戶**，但不建議用於生產登錄。</span><span class="sxs-lookup"><span data-stu-id="30632-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="30632-327">`az acr create` 命令會顯示登入伺服器 URL (透過 `LOGIN SERVER` 資料行)，您用來登入使用 Docker CLI (例如`ninademo.azurecr.io`)。</span><span class="sxs-lookup"><span data-stu-id="30632-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="30632-328">此外，此命令會產生您可用於進行驗證的系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="30632-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="30632-329">若要擷取這些認證，請執行下列命令並記下所顯示的使用者名稱和密碼：</span><span class="sxs-lookup"><span data-stu-id="30632-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="30632-330">使用上一個步驟中的認證，以及您的個別登入伺服器，即可使用標準 Docker CLI 工作流程登入登錄。</span><span class="sxs-lookup"><span data-stu-id="30632-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="30632-331">您現在可以使用下列命令 (以您為容器映像提供的名稱取代 `lostintangent/node`) 來標記您的 Docker 容器，指出它與您的私人登錄相關聯。</span><span class="sxs-lookup"><span data-stu-id="30632-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="30632-332">最後，將已標記的映像推送到您私人的 Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="30632-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="30632-333">您的容器現在儲存在您自己的私人登錄中，而 Docker CLI 很樂於讓您繼續以使用 DockerHub 時的相同方式操作。</span><span class="sxs-lookup"><span data-stu-id="30632-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="30632-334">若要指示 App Service Web 應用程式從私人登錄提取，您只需要執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="30632-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="30632-335">務必將 `https://` 前置詞新增至 `-r` 選項的開頭。</span><span class="sxs-lookup"><span data-stu-id="30632-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="30632-336">不過，請勿將前置詞新增至容器映像名稱。</span><span class="sxs-lookup"><span data-stu-id="30632-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="30632-337">如果您在瀏覽器中重新整理此應用程式，一切的外觀和運作方式應該相同。</span><span class="sxs-lookup"><span data-stu-id="30632-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="30632-338">不過，它現在透過您的私人 Docker 登錄執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="30632-339">更新您的應用程式後，如上所述標記和推送變更，並在 App Service 容器組態中更新此標籤。</span><span class="sxs-lookup"><span data-stu-id="30632-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="30632-340">設定自訂網域名稱</span><span class="sxs-lookup"><span data-stu-id="30632-340">Configuring a custom domain name</span></span>

<span data-ttu-id="30632-341">雖然 `*.azurewebsites.net` URL 很適合用於測試，但有些時候，建議您將自訂網域名稱新增至您的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="30632-342">一旦擁有註冊機構提供的網域名稱，您只需要將 `A` 記錄新增給它，以指向您的 Web 應用程式的外部 IP (這實際上是負載平衡器)。</span><span class="sxs-lookup"><span data-stu-id="30632-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="30632-343">您可以執行下列命令來擷取此 IP：</span><span class="sxs-lookup"><span data-stu-id="30632-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="30632-344">除了新增 `A` 記錄，您也需要將 `TXT` 記錄新增到您的網域，以指向您到目前為止使用的 `*.azurewebsites.net` 網域。</span><span class="sxs-lookup"><span data-stu-id="30632-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="30632-345">`A` 和 `TXT` 記錄的組合可讓 Azure 確認您擁有該網域。</span><span class="sxs-lookup"><span data-stu-id="30632-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="30632-346">建立這些記錄 (並傳播 DNS 變更) 後，請向 Azure 登錄自訂網域，它就知道要正確地預期連入流量。</span><span class="sxs-lookup"><span data-stu-id="30632-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="30632-347">直到傳播 DNS 變更後，此命令才能運作。</span><span class="sxs-lookup"><span data-stu-id="30632-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="30632-348">開啟瀏覽器並瀏覽至您的自訂網域，查看它現在會解析成您在 Azure 上部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30632-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="30632-349">相應增加和放大</span><span class="sxs-lookup"><span data-stu-id="30632-349">Scaling up and out</span></span>

<span data-ttu-id="30632-350">在某些時候，Web 應用程式會變得極為熱門，以致其配置的資源 (CPU 和 RAM) 不足以處理增加的流量和操作需求。</span><span class="sxs-lookup"><span data-stu-id="30632-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="30632-351">您稍早建立的 App Service 方案 (**B1**) 隨附 1 個 CPU 核心和 1.75 GB 的 RAM，其可能相當快速達到使用極限。</span><span class="sxs-lookup"><span data-stu-id="30632-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="30632-352">**B2** 方案則隨附兩倍的 RAM 和 CPU，因此若注意到您的應用程式即將用完任何一項，您即可執行下列命令來相應增加基礎虛擬機器：</span><span class="sxs-lookup"><span data-stu-id="30632-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="30632-353">如須 Azure App Service 方案價格詳細資料和規格，請參閱 [App Service 價格](https://azure.microsoft.com/pricing/details/app-service/)一文。</span><span class="sxs-lookup"><span data-stu-id="30632-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="30632-354">稍候片刻，Web 應用程式將會移轉至要求的硬體，即可開始利用相關的資源。</span><span class="sxs-lookup"><span data-stu-id="30632-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="30632-355">除了相應增加以外，您也可執行上述相同的命令，並指定可以較低價格提供較少資源的 `--sku` 選項，相應減少資源。</span><span class="sxs-lookup"><span data-stu-id="30632-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="30632-356">除了相應增加虛擬機器規格，只要 Web 應用程式屬於無狀態，您也可藉由新增更多基礎虛擬機器執行個體來選擇「相應放大」。</span><span class="sxs-lookup"><span data-stu-id="30632-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="30632-357">您稍早建立的 App Service 方案僅包含單一虛擬機器 (背景工作角色)，因此，所有連入流量最終受制於該執行個體的可用資源限制。</span><span class="sxs-lookup"><span data-stu-id="30632-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="30632-358">如果您想要新增第二個虛擬機器執行個體，您可執行稍早執行的相同命令，但不是相應增加 SKU，而是相應放大背景工作角色虛擬機器的數目。</span><span class="sxs-lookup"><span data-stu-id="30632-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="30632-359">當您相應放大 Web 應用程式時，連入流量將以透明方式在所有的執行個體之間達到負載平衡，這可讓您立即增加您的容量，而不需變更任何程式碼或擔心所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="30632-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="30632-360">無狀態的 Web 應用程式可視為最佳做法，這可讓相應調整的能力 (增加、減少、放大) 具有完全的決定性，因為沒有任何虛擬機器或應用程式執行個體包含運作必備的狀態。</span><span class="sxs-lookup"><span data-stu-id="30632-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="30632-361">雖然本主題的教學課程說明如何在 App Service 方案中執行單一 Web 應用程式，但您可建立多個 Web 應用程式並部署到相同的方案中，讓您佈建和支付單一方案。</span><span class="sxs-lookup"><span data-stu-id="30632-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="30632-362">清除</span><span class="sxs-lookup"><span data-stu-id="30632-362">Clean-up</span></span>

<span data-ttu-id="30632-363">若要確保您不需支付任何未使用之 Azure 資源的費用，從 Visual Studio Code 終端機執行下列命令，即可刪除在本教學課程期間佈建的所有資源。</span><span class="sxs-lookup"><span data-stu-id="30632-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="30632-364">清除程序可能需要數分鐘的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="30632-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="30632-365">完成後，`az group delete` 命令可讓 Azure 帳戶保留在您開始本教學課程之前的相同狀態。</span><span class="sxs-lookup"><span data-stu-id="30632-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="30632-366">以一個單位的方式組織、部署和刪除 Azure 資源的功能，是資源群組的主要優勢之一。</span><span class="sxs-lookup"><span data-stu-id="30632-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="30632-367">因此，建議的作法是，您應該將預期有相同生命週期的資源群組在一起。</span><span class="sxs-lookup"><span data-stu-id="30632-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>