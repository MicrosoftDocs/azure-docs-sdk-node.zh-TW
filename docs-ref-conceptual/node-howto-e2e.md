---
title: "使用 Visual Studio Code 和 Azure 進行 Node.js 開發"
description: "完整的端對端教學課程說明如何建立 Node.js 應用程式、將其 Docker 化及部署到 Azure"
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
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>使用 Visual Studio Code 和 Azure 進行 Node.js 開發

本教學課程說明如何採用現有的 Node.js 應用程式，將它「容器化」 (使用 Docker)，然後使用 Visual Studio Code 將應用程式部署至 Azure。

本教學課程會使用 [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) 所建立及發佈的簡單待辦事項應用程式。 它是單一頁面的 MEAN 應用程式，因此會使用 MongoDB 作為其資料庫，Node/Express 作為其 REST API/Web 伺服器，以及 Angular.js 1.x 作為前端 UI。 

## <a name="prerequisites"></a>必要條件

若要依照示範操作，您必須安裝下列軟體：

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [DockerHub 帳戶](https://hub.docker.com/)
- [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Azure 帳戶](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/) - 用於對示範應用程式的前端進行偵錯。
- MongoDB - 由於示範應用程式會使用 MongoDB，所以您必須有在本機執行並接聽標準 `27017` 連接埠的 MongoDB 執行個體。 安裝 Docker 之後，執行下列兩個命令是達成此目的的最簡單方式：依序執行 `docker pull mongo` 和 `docker run -it -p 27017:27017 mongo`。

## <a name="project-setup"></a>專案設定

若要開始進行，請使用下列步驟下載範例專案：

1. 開啟 Visual Studio Code。

1. 按 **&lt;F1>** 以顯示命令選擇區。

1. 在命令選擇區提示字元，輸入 `gitcl`，選取 **Git: Clone** 命令，然後按 **&lt;Enter>**。

    ![Visual Studio Code 命令選擇區提示字元中的 gitcl 命令](./media/node-howto-e2e/git-clone.png)

1. 當系統提示您輸入 [存放庫 URL] 時，輸入 `https://github.com/scotch-io/node-todo`，然後按 **&lt;Enter>**。

1. 選取 (或建立) 要將專案複製到其中的本機目錄。

    ![Visual Studio Code 總管](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>整合式終端機

由於這是一個 Node.js 專案，所以您需要做的第一件事就是確定已從 npm 安裝專案的所有相依性。  

1. 按 **&lt;Ctrl>`** 以顯示 Visual Studio Code 整合式終端機。 

1. 輸入 `yarn`，然後按 **&lt;Enter>**。  

    ![在 Visual Studio Code 中執行 yarn 命令](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>整合式 Git 版本控制

透過 Yarn 安裝應用程式的相依性之後，就會建立 `yarn.lock` 檔案來提供可預測的方式，以在未來重新取得完全相同的相依性，而 CI (連續整合) 組建、生產部署或其他開發人員電腦都在意料之中。

下列步驟說明如何將 `yarn.lock` 檔案簽入原始檔控制中：

1. 在 Visual Studio Code 中，切換至整合式 Git 索引標籤 (包含 Git 標誌的索引標籤)。

1. 在 [訊息] 方塊中，輸入認可訊息，並且按 **&lt;Ctrl>&lt;Enter>**。 

    ![將 yarn.lock 檔案新增至 Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>專案和程式碼瀏覽

讓我們示範 Visual Studio Code 所提供之巡覽功能的一些範例，以便我們自己熟悉程式碼基底。

1. 按 **&lt;Ctrl>P**。

1. 輸入 `.js`，以顯示專案中的所有 JavaScript/JSON 檔案，以及每個檔案的上層目錄 

    ![顯示所有 .js* 檔案](./media/node-howto-e2e/git-output.png)

1. 選取 `server.js`，這是應用程式的啟動指令碼。 

1. 將滑鼠停留在 **database** 變數上 (已匯入於第 6 行)，以查看其類型。 在您專案的開發期間，快速檢查檔案中變數/模組/類型的這項功能非常有用。 

    ![探索類型](./media/node-howto-e2e/hover-help.png)

1. 在變數 (例如 **database**) 的範圍內按一下滑鼠，可讓您查看相同檔案中該變數的所有參考。 若要檢視專案內變數的所有參考，以滑鼠右鍵按一下變數，並從操作功能表中選取 [尋找所有參考]。

    ![尋找變數的參考](./media/node-howto-e2e/word-hilight.png)

1. 除了將滑鼠停留在變數來探索其類型，您也可以檢查定義的變數 (即使它在另一個檔案中)。 若要查看實際作業情形，以滑鼠右鍵按一下 **database.localUrl** (第 12 行)，然後從操作功能表中選取 [預覽定義]。 

    ![預覽變數的定義](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>修改程式碼並使用自動完成功能

MongoDB 連接字串已硬式編碼在 **database.localUrl** 的宣告中。 在本節中，您將修改程式碼以從環境變數擷取連接字串，並了解 Visual Studio Code 的自動完成功能。  

1. 開啟 `server.js` 檔案

1. 將下列程式碼： 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    取代為此程式碼：

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

請注意，如果您以手動方式輸入程式碼 (而不是複製並貼上)，則當您在 `process` 之後輸入句點後，Visual Studio Code 會顯示 Node.js **process** 全域 API 的可用成員。

![自動完成功能會自動顯示 API 的成員](./media/node-howto-e2e/process-env.png)

自動完成功能有作用，因為 Visual Studio Code 在幕後使用 TypeScript (即使針對 JavaScript) 來提供類型資訊，而該資訊可接著在您輸入資料時用於告知完成清單。 Visual Studio Code 能夠偵測這是 Node.js 專案，因此會從 [NPM](https://www.npmjs.com/package/@types/node) 自動下載 Node.js 的 TypeScript typings 檔案。 typings 檔案可讓您取得其他 Node.js globals (例如 **Buffer** 和 **setTimeout**) 的自動完成功能，以及所有內建的模組 (例如 **fs** 和 **http**)。

除了內建 Node.js API 以外，此自動取得的 typings 也適用於超過 2,000 個第 3 方模組，例如 React、Underscore 和 Express.。 例如，當 Mongoose 無法連線到已設定的 MongoDB 資料庫執行個體時，若要讓它免於損毀範例應用程式，請在第 13 行插入下列程式碼：

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

如同先前的程式碼，您會發現您不需執行任何動作，即可取得自動完成功能。

![自動完成功能會自動顯示 API 的成員](./media/node-howto-e2e/mongoose.png)

您可瀏覽 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 專案 (這是所有 TypeScript 類型定義的社群導向來源)，以查看哪些模組支援此自動完成功能。

## <a name="running-the-app"></a>執行應用程式

一旦瀏覽過程式碼，您就可以執行應用程式。 若要從 Visual Studio Code 執行應用程式，請按 **&lt;F5>**。 透過  **&lt;F5>** 執行程式碼 (偵錯模式) 時，Visual Studio Code 會啟動應用程式並顯示 [偵錯主控台] 視窗，進而顯示應用程式的 stdout。

![透過偵錯主控台監視應用程式的 stdout](./media/node-howto-e2e/console.png)

此外，[偵錯主控台] 會附加至新執行的應用程式，以便您輸入 JavaScript 運算式 (將在應用程式中評估)，而且還包含自動完成功能。 若要查看實際作業情形，請在主控台中輸入 `process.env`：

![在偵錯主控台中輸入程式碼](./media/node-howto-e2e/console-code.png)

因為目前開啟的檔案是 JavaScript 檔案 (`server.js`)，所以您可按 **&lt;F5>** 來執行應用程式。 因此，Visual Studio Code 假設此專案是 Node.js 應用程式。 如果您關閉 Visual Studio Code 中所有的 JavaScript 檔案，然後按 **&lt;F5>**，Visual Studio Code 會查詢您的環境：

![指定執行階段環境](./media/node-howto-e2e/select-env.png)

開啟瀏覽器並瀏覽至 `http://localhost:8080`，以查看執行中的應用程式。 在文字方塊中輸入訊息並新增/移除一些待辦事項，感受一下應用程式的運作方式。

![執行中的待辦事項應用程式](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Debugging

除了能夠執行應用程式並透過整合式主控台與其互動，Visual Studio Code 還可供直接在程式碼內設定中斷點。 例如，按 **&lt;Ctrl>P** 可顯示檔案選擇器。 檔案選擇器顯示後，輸入 `route`，然後選取 `route.js` 檔案。

在第 28 行上設定中斷點，其代表應用程式嘗試新增待辦項目時呼叫的 Express 路由。 若要設定中斷點，只要在編輯器中按一下行號左邊的區域，如下圖所示。

![在 Visual Studio Code 中設定中斷點](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> 除了標準中斷點以外，Visual Studio Code 還支援條件式中斷點，這可讓您自訂應用程式何時應該暫停執行。 若要設定條件式中斷點，請以滑鼠右鍵按一下要暫停執的行左邊的區域，選取 [新增條件式中斷點...]，並指定 JavaScript 運算式 (例如 `foo = "bar"`) 或執行計數，以定義您要暫停執行的條件。
> 
> 

一旦設定中斷點，請回到執行中的應用程式並新增待辦項目。 立即新增待辦項目會導致應用程式在您設定中斷點的第 28 行暫停執行：

![Visual Studio Code 在中斷點暫停執行](./media/node-howto-e2e/debugger.png)

應用程式一旦暫停，您即可將滑鼠停留在程式碼的運算式上，以檢視其目前的值、檢查區域變數/監看式並呼叫堆疊，以及使用偵錯工具列來逐步執行程式碼。 按 **&lt;F5>** 以繼續執行應用程式。

## <a name="full-stack-debugging"></a>完整堆疊的偵錯

如本主題稍早所述，TODO 應用程式是 MEAN 應用程式 - 也就是說，同時使用 JavaScript 撰寫其前端和後端。 因此，當您正在進行後端 (Node/Express) 程式碼的偵錯時，有些時候，您可能需要進行前端 (Angular) 程式碼的偵錯。 基於這個目的，Visual Studio Code 有很大的擴充功能生態系統，包括整合式 Chrome 偵錯。

切換至 [擴充功能] 索引標籤，然後在搜尋方塊中輸入 `chrome`：

![Visual Studio Code 的 Chrome 偵錯擴充功能](./media/node-howto-e2e/chrome.png)

選取名為 [Chrome 偵錯工具] 的擴充功能，然後選取 [安裝]。 安裝 Chrome 偵錯擴充功能之後，請選取 [重新載入] 以關閉並重新開啟 Visual Studio Code，進而啟用擴充功能。 

![在安裝 Chrome 偵錯擴充功能之後重新載入 Visual Studio Code](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

隨然您可以在任何 Visual Studio Code 專屬組態的情況下，執行 Node.js 程式碼並進行偵錯，但為了進行前端 Web 應用程式的偵錯，您必須產生 `launch.json` 檔案，以指示 Visual Studio Code 如何執行應用程式。 

若要產生 `launch.json` 檔案，請切換至 [偵錯] 索引標籤，按一下齒輪圖示 (其頂端應該會有小紅點)，然後選取 **node.js** 環境。

![用來設定 launch.json 檔案的 Visual Studio Code 選項](./media/node-howto-e2e/debug-gear.png)

所建立的 `launch.json` 檔案會如下所示，並且告知 Visual Studio Code 如何啟動及/或附加至應用程式，才能進行偵錯。 

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

請注意，Visual Studio Code 能夠偵測到應用程式的啟動指令碼為 `server.js`。 

開啟 `launch.json` 檔案後，選取 [新增組態] (右下方)，然後選取 [Chrome：使用 userDataDir 啟動]。

![將 Chrome 組態新增至 Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

為 Chrome 新增的執行組態可讓您進行前端 JavaScript 程式碼的偵錯。 

您可以將滑鼠停留在任何指定的設定上，以檢視設定功能說明的相關文件。 此外，請注意，Visual Studio Code 會自動偵測應用程式的 URL。 將 **webRoot** 屬性更新為 `${workspaceRoot}/public`，讓 Chrome 偵錯工具知道如何找到應用程式的前端資產：

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

若要同時啟動/偵錯前端與後端，您需要建立「複合」執行組態，以告知 Visual Studio Code 哪一組組態會平行執行。 

新增下列程式碼片段作為 `launch.json` 檔案中的最上層屬性 (作為現有 **configurations** 屬性的同層級)。

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

在 **compounds.configurations** 陣列中指定的字串值是指 **configurations** 清單中個別項目的 **name**。 如果您已修改這些名稱，您必須在陣列中進行適當的變更。 若要查看實際作業情形，切換至 [偵錯] 索引標籤，將所選取的組態變更為 [完整堆疊] (複合組態的名稱)，然後按 **&lt;F5>** 加以執行。

![在 Visual Studio Code 中執行組態](./media/node-howto-e2e/full-stack-profile.png)

執行組態可啟動 Node.js 應用程式 (如偵錯主控台輸出所示) 和 Chrome (已設定為瀏覽至位於 `http://localhost:8080` 的 Node.js 應用程式)。

按 **&lt;Ctrl>P**，然後輸入 (或選取) `todos.js`，這是應用程式前端的主要 Angular 控制器。 

在第 11 行上設定中斷點，這是所建立之新待辦項目的進入點。

返回執行中的應用程式、新增待辦項目，並請注意 Visual Studio Code 現在已在 Angular 程式碼內暫停執行。

![在 Visual Studio Code 中進行前端程式碼的偵測](./media/node-howto-e2e/chrome-pause.png)

如同 Node.js 偵錯，您可以將滑鼠停留在運算式上、檢視區域變數/監看式、在主控台中評估運算式等等。 

有兩個值得注意的重點：

1. [呼叫堆疊] 窗格會顯示兩個不同的堆疊：**Node** 和 **Chrome**，並指出哪個堆疊目前暫停。

1. 您可以在前端與後端程式碼之間徘徊。 若要測試此功能，請按 **&lt;F5>**，以執行和叫用先前在 Express 路由中設定的中斷點。

使用此設定，您現在可以直接在 Visual Studio Code 中有效地進行前端、後端或完整堆疊 JavaScript 程式碼的偵錯。 

此外，複合偵錯工具概念不限於只有兩個目標程序，而且也不只限於 JavaScript。 因此，如果適用於微服務應用程式 (可能是 polyglot)，您可以使用完全相同的工作流程 (安裝適當的語言/架構擴充功能後)。

## <a name="dockerizing-the-app"></a>將應用程式 Docker 化

本節著重於 Visual Studio Code 針對使用 [Docker](https://www.docker.com/) 進行開發所提供的經驗。 Node.js 開發人員會使用 Docker 提供適用於開發、CI (連續整合) 和生產環境的可攜式應用程式部署。 當 Docker 呈現陡峭的學習曲線時，Visual Studio Code 會提供擴充功能，試著協助簡化在應用程式中使用 Docker。

切換回 [擴充功能] 索引標籤，搜尋 `docker`，然後選取 **Docker** 擴充功能。 

安裝 Docker 擴充功能，然後重新載入 Visual Studio Code。

![安裝適用於 Visual Studio Code 的 Docker 擴充功能](./media/node-howto-e2e/docker-search.png)

適用於 Visual Studio Code 的 Docker 擴充功能包含針對現有專案產生 *Dockerfile* 和 `docker-compose.yml` 檔案的命令。 

若要查看可用的 Docker 命令，請顯示命令選擇區 (透過 **&lt;F1>**) 並輸入 `docker`。

![適用於 Visual studio 的 Docker 擴充功能所支援的命令 ](./media/node-howto-e2e/docker-commands.png)

選取 [Docker：將 Docker 檔案新增到工作區]，選取 **Node.js** 作為應用程式平台，並指定應用程式公開連接埠 `8080`。 

Docker 命令會產生您可立即開始使用的完整 `Dockerfile` 和 Docker-compose 檔案。

![所產生的 Dockerfile](./media/node-howto-e2e/docker-file.png)

Docker 擴充功能也會為 `Dockerfiles` 和 `docker-compose.yml` 檔案提供自動完成功能。 

若要查看實際作業情形，請開啟 `Dockerfile` 並將第 2 行從：

```docker
FROM node:latest
```

變更為：

```docker
FROM mhart
```

將游標放在 `mhart` 中的 `t` 之後，按 **&lt;Ctrl>&lt;Space>** 以檢視 `mhart` 在 DockerHub 上發佈的所有映像存放庫。

![Docker 擴充功能自動完成](./media/node-howto-e2e/docker-completion.png)

選取 `mhart/alpine-node`，這會提供此應用程式需要的所有項目。 

較小的映像通常比較適當，因為您希望應用程式的建置和部署愈快愈好，而讓散發和調整更加快速。

此時，您已產生 `Dockerfile`，您必須建立實際的 Docker 映像。 同樣地，您可以使用 Docker 擴充功能安裝在 Visual Studio Code 中的命令。 按 **&lt;F1>**，在命令選擇區輸入 `dockerb`，然後選取 [Docker：建置映像] 命令。 選擇您剛產生及修改的 `/Dockerfile`。 指定包含您的 DockerHub 使用者名稱的標籤 (例如 `lostintangent/node`)。 按 **&lt;ENTER>** 以啟動整合式終端機視窗，以顯示正在建立的 Docker 映像輸出。

![Docker 映像組建狀態](./media/node-howto-e2e/docker-build.png)

請注意，此命令會為您自動執行 `docker build`，這是您可以選擇使用的另一個生產力加強程式範例，或者您可以直接使用 Docker CLI。 

此時，若要讓此映像可輕鬆取得以供部署，您只需要將映像推送至 DockerHub。 若要這麼做，請確定您已藉由從 CLI 執行 `docker login` 並輸入您的帳戶認證，向 DockerHub 驗證。 然後，在 Visual Studio Code 中，您可以啟動命令選擇區，輸入 `dockerpush`，然後選取 `Docker: Push` 命令。 選取您剛才建立的映像標籤 (例如 `lostintangent/node`)，然後按 **&lt;Enter>**。 此命令會自動呼叫 `docker push` 並在整合式終端機中顯示輸出。

## <a name="deploying-the-app"></a>部署應用程式

既然您已將應用程式 Docker 化並推送至 DockerHub，您就必須將它部署到雲端，以便全世界可以看到它。 為此，您可以使用 Azure App Service (這是 Azure 的 PaaS 供應項目)。 App Service 有兩項與 Node.js 開發人員相關的功能：

- 支援以 Linux 為基礎的 VM，這可減少使用原生 Node 模組建置的應用程式，或其他可能不支援 Windows 和/或運作方式不同的工具發生不相容的情形。
- 支援以 Docker 為基礎的部署，這可讓您指定 Docker 映像的名稱，並允許 App Service 提取、部署及自動縮放影像。

若要開始使用，請開啟 Visual Studio 終端機。 您將使用新的 Azure CLI 2.0 來管理 Azure 帳戶及佈建執行待辦事項應用程式所需的基礎結構。 使用 `az login` 命令從 CLI 登入您的帳戶 (如必要條件所述) 後，請執行下列步驟來佈建 App Service 執行個體及部署待辦事項應用程式容器：

1. 建立資源群組，您可以將它視為有助於組織 Azure 資源的「命名空間」或「目錄」。 `-n` 選項用來指定您想要的群組名稱。

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > `-l` 選項表示資源群組的位置。 在預覽期間，Linux 上的 App Service 支援僅適用於精選的區域。 因此，如果您不是位於美國西部，而且要查看有其他哪些區域可用，請從 CLI 執行 `az appservice list-locations --linux-workers-enabled` 以檢視您的資料中心選項。

2. 將新建立的資源群組設定為預設資源群組，您便可以繼續使用 CLI，而不需要在每個呼叫中明確指定資源群組：

   ```shell
   az configure -d group=nina-demo
   ```
   
3. 建立 App Service *方案*，其可管理應用程式部署所在基礎虛擬機器的建立和調整。 同樣地，指定您想要的任何 `n` 選項值。

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > --is-linux 選項表示您想要以 Linux 為基礎的虛擬機器。 若是沒有，CLI 會預設為佈建以 Windows 為基礎的虛擬機器。

4. 建立 App Service Web 應用程式，代表將在剛建立的方案和資源群組內執行的實際待辦事項應用程式。 您可以將 Web 應用程式視為程序或容器的同義詞，而將方案視為 Web 應用程式執行所在的虛擬機器/容器主機。 此外，建立 Web 應用程式時，您需要將它設定為使用您發佈至 DockerHub 的 Docker 映像：

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > 若不使用自訂容器，您寧可使用 Git 部署，請參閱[在 Azure 中建立 Node.js Web 應用程式](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs)一文。

5. 將 Web 應用程式設定為預設 Web 執行個體：

    ```shell
    az configure -d web=nina-demo-app
    ```

6. 啟動應用程式，以檢視已部署的容器 (將會在 `*.azurewebsites.net` URL 提供)：

    ```shell
    az webapp browse
    ```

    ![在瀏覽器中執行的待辦事項應用程式](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > 第一次可能需要幾分鐘才能載入應用程式，因為 App Service 必須從 DockerHub 提取 Docker 映像，然後加以啟動。

此時，您才剛部署並執行待辦事項應用程式。 

您現在已部署待辦事項應用程式。 不過，轉圈圖示表示應用程式無法連線到資料庫。 這是因為您在開發期間使用了 MongoDB 的本機執行個體，這顯然無法從 Azure 資料中心觸達。 因為您將應用程式修改為透過環境變數接受連接字串，所以您只需要啟動 MongoDB 伺服器並重新設定 App Service 執行個體來參考環境變數。 下一節會提供相關說明。

## <a name="provisioning-a-mongodb-server"></a>佈建 MongoDB 伺服器

雖然您可以設定 MongoDB 伺服器或複本集，並自行管理基礎結構，但 Azure 會提供一個名為 [Cosmos DB](https://azure.microsoft.com/services/documentdb/) 的解決方案。 Cosmos DB 是完全受管理、可異地複寫、高效能並可提供 MongoDB 相容性層級的 NoSQL 資料庫。 這表示您可以指向其上的現有 MEAN 應用程式 (或任何 MongoDB 用戶端/工具，例如 [Studio 3T](https://studio3t.com/))，而不需變更連接字串以外的任何項目。 下列步驟說明如何達成：

1. 從 Visual Studio Code 終端機，執行下列命令以建立與 MongoDB 相容的 Cosmos DB 服務執行個體。 以全域唯一的值取代 **<NAME>** 預留位置 (Cosmos DB 會使用此名稱來產生資料庫的伺服器 URL)：

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. 擷取此執行個體的 MongoDB 連接字串：

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. 更新 Web 應用程式的 **MONGODB_URL** 環境變數，讓它連線到新佈建的 Cosmos DB 執行個體，而不是嘗試連線到在本機執行的 MongoDB 伺服器 (這不存在！)：

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. 返回您的瀏覽器並予以重新整理。 嘗試新增和移除待辦項目，證明應用程式現在運作正常，而不需要變更任何項目！ 將環境變數設定為已建立的 Cosmos DB 執行個體，這完全模擬 MongoDB 資料庫。

    ![連線到資料庫之後的示範應用程式](./media/node-howto-e2e/finished-demo.png)

如有需要，您可以切換回 Cosmos DB 執行個體並相應增加 (或減少) MongoDB 執行個體所需的保留輸送量，並受惠於新增的流量，而不需要手動管理任何基礎結構。

此外，Cosmos DB 會自動為您編製每份文件和每個屬性的索引。 如此一來，您就不需要剖析較慢的查詢，或手動微調您的索引。 只要視需要進行佈建和調整，讓 Cosmos DB 處理其他事宜。

## <a name="hosting-a-private-docker-registry"></a>裝載私人 Docker 登錄

DockerHub 針對散佈容器映像提供令人讚嘆的經驗，但有些情況下您寧可裝載自己的私人 Docker 登錄 - 例如為了安全性/控管或效能優勢。 基於此目的，Azure 提供可讓您加速自有 Docker 登錄的 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR)，其支援儲存體位於與您的 Web 應用程式相同的資料中心 (讓提取更加快速)。 ACR 也為您提供完整的內容和存取控制權 - 例如誰可以推送或提取映像。 

執行下列命令即可完成自訂登錄的佈建。 (以全域唯一的值取代 **<NAME>** 預留位置，因為 ACE 會使用指定的值來產生登錄的登入伺服器 URL。

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> 為了簡單起見，雖然本主題的範例使用**系統管理員帳戶**，但不建議用於生產登錄。 

`az acr create` 命令會顯示登入伺服器 URL (透過 `LOGIN SERVER` 資料行)，您用來登入使用 Docker CLI (例如`ninademo.azurecr.io`)。 此外，此命令會產生您可用於進行驗證的系統管理員認證。 若要擷取這些認證，請執行下列命令並記下所顯示的使用者名稱和密碼：

```shell
az acr credential show -n $ACR_NAME
```

使用上一個步驟中的認證，以及您的個別登入伺服器，即可使用標準 Docker CLI 工作流程登入登錄。

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

您現在可以使用下列命令 (以您為容器映像提供的名稱取代 `lostintangent/node`) 來標記您的 Docker 容器，指出它與您的私人登錄相關聯。

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

最後，將已標記的映像推送到您私人的 Docker 登錄。

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

您的容器現在儲存在您自己的私人登錄中，而 Docker CLI 很樂於讓您繼續以使用 DockerHub 時的相同方式操作。 若要指示 App Service Web 應用程式從私人登錄提取，您只需要執行下列命令：

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> 務必將 `https://` 前置詞新增至 `-r` 選項的開頭。 不過，請勿將前置詞新增至容器映像名稱。

如果您在瀏覽器中重新整理此應用程式，一切的外觀和運作方式應該相同。 不過，它現在透過您的私人 Docker 登錄執行您的應用程式。 更新您的應用程式後，如上所述標記和推送變更，並在 App Service 容器組態中更新此標籤。

## <a name="configuring-a-custom-domain-name"></a>設定自訂網域名稱

雖然 `*.azurewebsites.net` URL 很適合用於測試，但有些時候，建議您將自訂網域名稱新增至您的 Web 應用程式。 一旦擁有註冊機構提供的網域名稱，您只需要將 `A` 記錄新增給它，以指向您的 Web 應用程式的外部 IP (這實際上是負載平衡器)。 您可以執行下列命令來擷取此 IP：

```shell
az webapp config hostname get-external-ip
```

除了新增 `A` 記錄，您也需要將 `TXT` 記錄新增到您的網域，以指向您到目前為止使用的 `*.azurewebsites.net` 網域。 `A` 和 `TXT` 記錄的組合可讓 Azure 確認您擁有該網域。

建立這些記錄 (並傳播 DNS 變更) 後，請向 Azure 登錄自訂網域，它就知道要正確地預期連入流量。 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> 直到傳播 DNS 變更後，此命令才能運作。

開啟瀏覽器並瀏覽至您的自訂網域，查看它現在會解析成您在 Azure 上部署的應用程式。

## <a name="scaling-up-and-out"></a>相應增加和放大

在某些時候，Web 應用程式會變得極為熱門，以致其配置的資源 (CPU 和 RAM) 不足以處理增加的流量和操作需求。 您稍早建立的 App Service 方案 (**B1**) 隨附 1 個 CPU 核心和 1.75 GB 的 RAM，其可能相當快速達到使用極限。 **B2** 方案則隨附兩倍的 RAM 和 CPU，因此若注意到您的應用程式即將用完任何一項，您即可執行下列命令來相應增加基礎虛擬機器：

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> 如須 Azure App Service 方案價格詳細資料和規格，請參閱 [App Service 價格](https://azure.microsoft.com/pricing/details/app-service/)一文。

稍候片刻，Web 應用程式將會移轉至要求的硬體，即可開始利用相關的資源。 除了相應增加以外，您也可執行上述相同的命令，並指定可以較低價格提供較少資源的 `--sku` 選項，相應減少資源。 

除了相應增加虛擬機器規格，只要 Web 應用程式屬於無狀態，您也可藉由新增更多基礎虛擬機器執行個體來選擇「相應放大」。 您稍早建立的 App Service 方案僅包含單一虛擬機器 (背景工作角色)，因此，所有連入流量最終受制於該執行個體的可用資源限制。 如果您想要新增第二個虛擬機器執行個體，您可執行稍早執行的相同命令，但不是相應增加 SKU，而是相應放大背景工作角色虛擬機器的數目。

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

當您相應放大 Web 應用程式時，連入流量將以透明方式在所有的執行個體之間達到負載平衡，這可讓您立即增加您的容量，而不需變更任何程式碼或擔心所需的基礎結構。 

無狀態的 Web 應用程式可視為最佳做法，這可讓相應調整的能力 (增加、減少、放大) 具有完全的決定性，因為沒有任何虛擬機器或應用程式執行個體包含運作必備的狀態。 

> [!NOTE]
> 雖然本主題的教學課程說明如何在 App Service 方案中執行單一 Web 應用程式，但您可建立多個 Web 應用程式並部署到相同的方案中，讓您佈建和支付單一方案。 

## <a name="clean-up"></a>清除

若要確保您不需支付任何未使用之 Azure 資源的費用，從 Visual Studio Code 終端機執行下列命令，即可刪除在本教學課程期間佈建的所有資源。

```shell
az group delete
```

> [!NOTE]
> 清除程序可能需要數分鐘的時間才能完成。 

完成後，`az group delete` 命令可讓 Azure 帳戶保留在您開始本教學課程之前的相同狀態。 以一個單位的方式組織、部署和刪除 Azure 資源的功能，是資源群組的主要優勢之一。 因此，建議的作法是，您應該將預期有相同生命週期的資源群組在一起。