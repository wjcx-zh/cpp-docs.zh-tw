---
title: "CAtlServiceModuleT::Start Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule.Start"
  - "CServiceModule::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start 方法"
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::Start Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當服務執行時， **\_tWinMain CAtlServiceModuleT::WinMain**呼叫，接著呼叫 `CAtlServiceModuleT::Start`。  
  
 `CAtlServiceModuleT::Start` 設定陣列對應每個服務給它啟動函式的 **SERVICE\_TABLE\_ENTRY** 結構。  這個陣列傳遞至 Win32 API 函式， [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324)。  理論上，一個 EXE 可以處理多個服務，而且陣列可以有多 **SERVICE\_TABLE\_ENTRY** 結構。  目前，不過， ATL 所產生的服務僅支援每個 EXE 的服務。  因此，這個陣列包含服務名稱和 **\_ServiceMain** 做為啟始函式中的單一項目。  **\_ServiceMain** 是呼叫非靜態成員函式 `CAtlServiceModuleT` ， `ServiceMain`的靜態成員函式。  
  
> [!NOTE]
>  **StartServiceCtrlDispatcher** 不能連接至服務控制管理員 \(SCM\) 可能表示程式不是做為服務。  在這種情況下，程式直接呼叫 `CAtlServiceModuleT::Run` ，讓程式可以是以本機伺服器。  如需執行程式的詳細資訊做為本機伺服器，請參閱 [偵錯秘訣](../atl/debugging-tips.md)。  
  
## 請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../Topic/CAtlServiceModuleT::Start.md)