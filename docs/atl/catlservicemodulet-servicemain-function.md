---
title: "CAtlServiceModuleT::ServiceMain Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceMain"
  - "CServiceModule::ServiceMain"
  - "CServiceModule.ServiceMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ServiceMain method"
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::ServiceMain Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您開啟服務控制台應用程式，請選取服務，然後按一下 \[**啟動**\] 時，服務控制管理員 \(SCM\) 呼叫 `ServiceMain` 。  
  
 在 `ServiceMain`SCM 呼叫之後，服務必須提供 SCM 處理函式。  這個函式來讓 SCM 取得服務的狀態和傳遞特定指令 \(例如暫停或停止\)。  SCM 則沒有這個函式，當服務傳遞 **\_Handler** Win32 API 函式， [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054)。  \(**\_Handler** 是呼叫非靜態成員函式。 [處理常式](../atl/catlservicemodulet-handler-function.md)\) 的靜態成員函式  
  
 在啟動時，服務應告知 SCM 其目前狀態。  它會藉由將 **SERVICE\_START\_PENDING** 給 Win32 API 函式， [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)。  
  
 `ServiceMain` 然後呼叫 `CAtlExeModuleT::InitializeCom`，呼叫 Win32 API 函式 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)。  根據預設， `InitializeCom` 傳遞 **COINIT\_MULTITHREADED** 旗標才能運作。  這個旗標指示程式是無限制執行緒伺服器。  
  
 現在， `CAtlServiceModuleT::Run` 呼叫執行服務的主要工作。  **執行** 繼續執行，直到服務已停止。  
  
## 請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../Topic/CAtlServiceModuleT::ServiceMain.md)