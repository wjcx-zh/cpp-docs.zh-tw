---
title: "Hosting ActiveX Controls Using ATL AXHost | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 裝載"
  - "AXHost method"
  - "Calendar control (ActiveX)"
  - "Calendar control (ActiveX), hosting with ATL AXHost"
  - "CAxWindow2T class"
  - "裝載 ActiveX 控制項"
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hosting ActiveX Controls Using ATL AXHost
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用各種 ATL 函式，本主題中的範例示範如何建立 AXHost 以及如何裝載 ActiveX 控制項。  它也會示範如何存取控制項和從所裝載控制項接收事件 \(使用 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)\)。  這個範例以裝載 Calendar 控制項已在主視窗或子視窗。  
  
 請注意 `USE_METHOD` 符號的定義。  您可以變更這個符號的值變更為 1 和 8 之間。.  符號值決定控制項要如何建立:  
  
-   對於建立裝載子類別的 `USE_METHOD`，呼叫的偶數值視窗並將它轉換為輸入控制項裝載。  對於奇數值，程式碼會建立為裝載的子視窗。  
  
-   如需 `USE_METHOD` 的值介於 1 和 4 之間，存取控制項和接收事件也會在主應用程式的呼叫中完成。  介於 5 和 8 之間的值會查詢介面的主機並攔截接收。  
  
 這個摘要:  
  
|USE\_METHOD|主應用程式|控制存取和接收事件。|這個範例所示範的函式|  
|-----------------|-----------|----------------|----------------|  
|1|子視窗|進一步|CreateControlLicEx|  
|2|主視窗|進一步|AtlAxCreateControlLicEx|  
|3|子視窗|進一步|CreateControlEx|  
|4|主視窗|進一步|AtlAxCreateControlEx|  
|5|子視窗|多個步驟。|CreateControlLic|  
|6|主視窗|多個步驟。|AtlAxCreateControlLic|  
|7|子視窗|多個步驟。|CreateControl|  
|8|主視窗|多個步驟。|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/CPP/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## 請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](../Topic/AtlAxCreateControl.md)   
 [AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)   
 [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)   
 [AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)   
 [CAxWindow2T Class](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic Interface](../atl/reference/iaxwinhostwindowlic-interface.md)