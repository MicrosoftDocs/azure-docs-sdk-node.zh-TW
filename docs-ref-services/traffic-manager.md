---
title: "適用於 Node.js 的 Azure 流量管理員模組"
description: "適用於 Node.js 的 Azure 流量管理員模組參考"
keywords: "Azure,SDK,API,流量管理員, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>適用於 Node.js 的 Azure 流量管理員模組

## <a name="overview"></a>概觀

Microsoft Azure 流量管理員可讓您控制使用者流量，將流量分散到不同資料中心的服務端點。 流量管理員支援的服務端點包括 Azure VM、Web Apps 和雲端服務。 您也可以將流量管理員使用於外部、非 Azure 端點。

深入了解 [Azure 流量管理員](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 流量管理員 npm 模組

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>範例

此範例會列出指定之資源群組的所有流量管理員。

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
