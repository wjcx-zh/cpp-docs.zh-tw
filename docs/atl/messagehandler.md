---
title: "MessageHandler | Microsoft Docs"
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
  - "MessageHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MessageHandler function"
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MessageHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**MessageHandler** 是 `MESSAGE_HANDLER` 巨集的第二個參數所識別的函式名稱加入至訊息對應的。  
  
## 語法  
  
```  
  
      LRESULT   
      MessageHandler  
      (  
   UINT uMsg,  
   WPARAM wParam,  
   LPARAM lParam,  
   BOOL& bHandled  
);  
```  
  
#### 參數  
 `uMsg`  
 指定訊息。  
  
 `wParam`  
 其他特定訊息資訊。  
  
 `lParam`  
 其他特定訊息資訊。  
  
 `bHandled`  
 為 **是** 的訊息對應集合 `bHandled` 在 `MessageHandler` 之前呼叫。  如果 `MessageHandler` 不完全處理訊息，應該將 `bHandled` 至 **否** 表示訊息需要進一步處理。  
  
## 傳回值  
 訊息處理的結果。  如果成功，則為 0。  
  
## 備註  
 如需使用這個訊息處理常式在訊息對應，請參閱 [MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md)。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)