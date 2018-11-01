---
title: 適用於 Node.js 的 Azure 媒體服務模組
description: 適用於 Node.js 的 Azure 媒體服務模組參考
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50269741"
---
# <a name="azure-media-services-modules-for-nodejs"></a>適用於 Node.js 的 Azure 媒體服務模組

Azure 媒體服務是一個可延伸的雲端型平台，供開發人員建置可擴充的媒體管理和傳遞應用程式。 媒體服務是以 REST API 為基礎，可讓您安全地上傳、儲存、編碼和封裝視訊或音訊內容，以用於隨選和即時資料流傳遞給各種用戶端 (例如電視、電腦和行動裝置)。

使用 Azure 媒體服務，您可以：
- 建置完全採用媒體服務的端對端工作流程。 
- 在工作流程的某些部分使用第三方元件。 例如，使用第三方編碼器來進行編碼； 然後使用媒體服務上傳、保護、封裝、傳遞。
- 即時串流您的內容或傳遞隨選內容。 本主題也會連結到其他相關主題。

## <a name="management-package"></a>管理套件

### <a name="install-the-npm-module"></a>安裝 npm 模組

安裝 Azure 媒體服務 npm 模組

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>範例

此範例會列出資源群組的所有媒體服務。

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>範例

深入探索可在應用程式中使用的 [Node.js 程式碼範例](https://azure.microsoft.com/resources/samples/?platform=nodejs)。
