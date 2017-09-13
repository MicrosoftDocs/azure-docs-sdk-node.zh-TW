---
title: "適用於 Node.js 的 Azure Machine Learning 模組"
description: "適用於 Node.js 的 Azure Machine Learning 模組參考"
keywords: Azure,SDK,API,Machine Learning, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="d4b16-104">適用於 Node.js 的 Azure Machine Learning 模組</span><span class="sxs-lookup"><span data-stu-id="d4b16-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d4b16-105">概觀</span><span class="sxs-lookup"><span data-stu-id="d4b16-105">Overview</span></span>

<span data-ttu-id="d4b16-106">機器學習服務是一項資料科學技術，協助電腦從現有的資料學習，以便預測未來的行為、結果和趨勢。</span><span class="sxs-lookup"><span data-stu-id="d4b16-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="d4b16-107">機器學習服務的這些預測可讓應用程式和裝置更聰明。</span><span class="sxs-lookup"><span data-stu-id="d4b16-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="d4b16-108">當您線上購物時，機器學習服務可根據您已經購買的產品，協助推薦其他產品。</span><span class="sxs-lookup"><span data-stu-id="d4b16-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="d4b16-109">當您的信用卡被刷過時，機器學習服務可將該筆交易與交易資料庫進行比對，協助偵測詐騙。</span><span class="sxs-lookup"><span data-stu-id="d4b16-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="d4b16-110">當您的真空吸塵器機器人清潔房間時，機器學習服務可協助它判斷作業是否完成。</span><span class="sxs-lookup"><span data-stu-id="d4b16-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="d4b16-111">管理套件</span><span class="sxs-lookup"><span data-stu-id="d4b16-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="d4b16-112">安裝 npm 模組</span><span class="sxs-lookup"><span data-stu-id="d4b16-112">Install the npm module</span></span>

<span data-ttu-id="d4b16-113">安裝 Azure Machine Learning npm 模組</span><span class="sxs-lookup"><span data-stu-id="d4b16-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="d4b16-114">範例</span><span class="sxs-lookup"><span data-stu-id="d4b16-114">Example</span></span>

<span data-ttu-id="d4b16-115">此範例會列出所有的機器學習認可方案。</span><span class="sxs-lookup"><span data-stu-id="d4b16-115">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="d4b16-116">範例</span><span class="sxs-lookup"><span data-stu-id="d4b16-116">Samples</span></span>

<span data-ttu-id="d4b16-117">深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。</span><span class="sxs-lookup"><span data-stu-id="d4b16-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
