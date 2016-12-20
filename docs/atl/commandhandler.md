---
title: "CommandHandler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CommandHandler function"
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CommandHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CommandHandler` 是 `COMMAND_HANDLER` 巨集的第三個參數識別的函式在您的訊息對應的。  
  
## 語法  
  
```  
  
      LRESULT   
      CommandHandler  
      (  
   WORD wNotifyCode,  
   WORD wID,  
   HWND hWndCtl,  
   BOOL& bHandled   
);  
```  
  
#### 參數  
 `wNotifyCode`  
 向程式碼。  
  
 *wID*  
 功能表項目、控制項或快速鍵的識別項。  
  
 *hWndCtl*  
 將 Windows 控制項的控制代碼。  
  
 `bHandled`  
 為 **是** 的訊息對應集合 `bHandled` 在 `CommandHandler` 之前呼叫。  如果 `CommandHandler` 不完全處理訊息，應該將 `bHandled` 至 **否** 表示訊息需要進一步處理。  
  
## 傳回值  
 訊息處理的結果。  如果成功，則為 0。  
  
## 備註  
 如需使用這個訊息處理常式在訊息對應，請參閱 [COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md)。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)