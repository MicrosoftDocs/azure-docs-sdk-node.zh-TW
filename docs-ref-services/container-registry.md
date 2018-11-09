---
title: 適用於 Node.js 的 Azure Container Registry 模組
description: 適用於 Node.js 的 Azure Container Registry 模組參考
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071597"
---
# <a name="azure-container-registry-modules-for-nodejs"></a>適用於 Node.js 的 Azure Container Registry 模組

Azure Container Registry 是受控 Docker 登錄服務，架構於開放原始碼的 Docker Registry 2.0。 建立及維護 Azure 容器登錄庫，以儲存和管理您的私人 Docker 容器映像。 使用 Azure 的容器登錄庫進行現有容器的開發與部署管線，並利用 Docker 社群的專業知識。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure Container Registry npm 模組

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>範例

此範例會取得可用容器的清單。

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
