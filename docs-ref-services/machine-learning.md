---
title: 適用於 Node.js 的 Azure Machine Learning 模組
description: 適用於 Node.js 的 Azure Machine Learning 模組參考
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439102"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>適用於 Node.js 的 Azure Machine Learning 模組

機器學習服務是一項資料科學技術，協助電腦從現有的資料學習，以便預測未來的行為、結果和趨勢。 機器學習服務的這些預測可讓應用程式和裝置更聰明。 當您線上購物時，機器學習服務可根據您已經購買的產品，協助推薦其他產品。 當您的信用卡被刷過時，機器學習服務可將該筆交易與交易資料庫進行比對，協助偵測詐騙。 當您的真空吸塵器機器人清潔房間時，機器學習服務可協助它判斷作業是否完成。

## <a name="management-package"></a>管理套件


### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Machine Learning npm 模組

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>範例

此範例會列出所有的機器學習認可方案。

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

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
