---
title: "CAtlServiceModuleT::Handler Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule::Handler"
  - "CServiceModule.Handler"
  - "Handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Handler method"
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::Handler Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CAtlServiceModuleT::Handler` 是服務控制管理員 \(SCM\) 呼叫來擷取服務狀態並將各種指令的常式 \(例如停止或暫停\)。  SCM 透過作業程式碼至 `Handler` 指出服務應採取的動作。  預設 ATL 產生只服務處理停止命令。  如果 SCM 傳遞停止命令，服務呼叫 SCM 程式就會停止。  服務會呼叫 `PostThreadMessage` 播報已中止的訊息傳送至其本身。  結束這個訊息迴圈，並顯示服務最後將會關閉。  
  
 若要處理多個指令，您需要變更 `CAtlServiceModuleT` 建構函式初始化的 `m_status` 資料成員。  這個資料成員呼叫啟用 SCM 服務時的顯示在服務控制台應用程式選取 。  
  
## 請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../Topic/CAtlServiceModuleT::Handler.md)