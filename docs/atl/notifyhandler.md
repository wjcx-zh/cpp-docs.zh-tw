---
title: "NotifyHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NotifyHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NotifyHandler function"
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# NotifyHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`NOTIFY_HANDLER` 巨集的第三個參數識別的函式名稱加入至訊息對應的。  
  
## 語法  
  
```  
  
      LRESULT   
      NotifyHandler  
      (  
   int idCtrl,  
   LPNMHDR pnmh,  
   BOOL& bHandled   
);  
```  
  
#### 參數  
 `idCtrl`  
 傳送訊息的控制項的識別項。  
  
 *pnmh*  
 包含通知程式碼和其他資訊 [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) 結構的位址。  對於某些通知訊息，則會 **NMHDR** 結構做為它的第一個成員的較大架構的這個參數。  
  
 `bHandled`  
 在呼叫之前， *NotifyHandler* 訊息對應設定 `bHandled` 至 **是** 。  如果 *NotifyHandler* 不完全處理訊息，應該將 `bHandled` 至 **否** 表示訊息需要進一步處理。  
  
## 傳回值  
 訊息處理的結果。  如果成功，則為 0。  
  
## 備註  
 如需使用這個訊息處理常式在訊息對應，請參閱 [NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md)。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)