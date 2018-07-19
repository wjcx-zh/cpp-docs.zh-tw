---
title: 裝載 ActiveX 控制項使用 ATL AXHost |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e26fd9e80b96c2b0196e3fd0e11b9c97f0f3bff3
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027202"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 裝載 ActiveX 控制項
本主題中的範例示範如何建立 AXHost 以及如何裝載使用各種 ATL 函式的 ActiveX 控制項。 它也會示範如何存取 「 控制項 」 和 「 接收事件 (使用[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 所裝載之控制項中。 此範例裝載在主視窗或子視窗中的行事曆控制項。  
  
 請注意 USE_METHOD 符號的定義。 您可以變更此符號介於 1 到 8 之間的值。 符號的值會決定控制項建立的方式：  
  
-   偶數值 USE_METHOD，若要建立主應用程式子視窗呼叫並將它轉換成控制主機。 奇數的值，程式碼會建立做為主機的子視窗。  
  
-   USE_METHOD 值介於 1 到 4，存取控制項，並在呼叫中接收的事件來完成，也會建立主應用程式。 介於 5 到 8 之間的值查詢介面的主機，並攔截接收。  
  
摘要如下：  
  
|USE_METHOD|主機|控制存取和事件接收|示範的函式|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|子視窗|一個步驟|CreateControlLicEx|  
|2|主視窗|一個步驟|AtlAxCreateControlLicEx|  
|3|子視窗|一個步驟|CreateControlEx|  
|4|主視窗|一個步驟|AtlAxCreateControlEx|  
|5|子視窗|多個步驟|CreateControlLic|  
|6|主視窗|多個步驟|AtlAxCreateControlLic|  
|7|子視窗|多個步驟|CreateControl|  
|8|主視窗|多個步驟|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [CAxWindow2T 類別](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic 介面](../atl/reference/iaxwinhostwindowlic-interface.md)

