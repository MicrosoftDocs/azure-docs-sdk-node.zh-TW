---
title: 使用 Node.js 的 Azure 傳訊和 IoT 程式碼範例
description: 展示如何以 Node.js 來使用 Azure 傳訊和 IoT 的範例程式碼
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="0a768-103">使用 Azure 傳訊和 IoT 搭配 Node.js 的範例程式碼</span><span class="sxs-lookup"><span data-stu-id="0a768-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="0a768-104">下列範例程式碼說明如何使用 Azure 傳訊和 IoT 搭配 Node.js 的範例程式碼</span><span class="sxs-lookup"><span data-stu-id="0a768-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="0a768-105">如果您需要其他工作的程式碼，您可以瀏覽 [Azure Node.js 範例](https://azure.microsoft.com/resources/samples/?term=nodejs)的完整清單。</span><span class="sxs-lookup"><span data-stu-id="0a768-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="0a768-106">**Azure IoT 中心**</span><span class="sxs-lookup"><span data-stu-id="0a768-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="0a768-107">Azure IoT 中樞 ping</span><span class="sxs-lookup"><span data-stu-id="0a768-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="0a768-108">簡單的 ping 解決方案，有助於驗證對 Azure IoT 中樞的裝置連線。</span><span class="sxs-lookup"><span data-stu-id="0a768-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="0a768-109">Azure IoT 服務在來自執行 Node.js 之 Intel Edison 的資料上偵測到的資料推文震動異常</span><span class="sxs-lookup"><span data-stu-id="0a768-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="0a768-110">IoT 專案，該專案使用 Azure IoT 中樞並顯示裝置執行節點以傳送遙測資料，而且由 Azure IoT 服務分析。</span><span class="sxs-lookup"><span data-stu-id="0a768-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="0a768-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="0a768-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="0a768-112">開始使用 Intel Edison Azure IoT 入門套件</span><span class="sxs-lookup"><span data-stu-id="0a768-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="0a768-113">使用 Azure IoT 入門套件示範 Azure IoT - Intel Edison。</span><span class="sxs-lookup"><span data-stu-id="0a768-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="0a768-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="0a768-114">**MQTT**</span></span> ||
| [<span data-ttu-id="0a768-115">範例 MQTT 和 HTTP 閘道模組</span><span class="sxs-lookup"><span data-stu-id="0a768-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="0a768-116">提供兩個閘道模組，這兩個模組會公開 IoTHub 樣式 MQTT 和 HTTPS 端點，以供上傳遙測資料，而在 MQTT 模組的案例中也可用於 C2D 傳訊。</span><span class="sxs-lookup"><span data-stu-id="0a768-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="0a768-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="0a768-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="0a768-118">開始使用 Microsoft Azure IoT Raspberry Pi 入門套件</span><span class="sxs-lookup"><span data-stu-id="0a768-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="0a768-119">說明如何使用 Azure IoT Raspberry Pi 入門套件。</span><span class="sxs-lookup"><span data-stu-id="0a768-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="0a768-120">將 Microsoft Azure IoT Raspberry Pi 3 入門套件連線到遠端監視解決方案</span><span class="sxs-lookup"><span data-stu-id="0a768-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="0a768-121">了解如何將 Raspberry Pi 3 裝置連線到 Azure IoT 套件遠端監視解決方案。</span><span class="sxs-lookup"><span data-stu-id="0a768-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
