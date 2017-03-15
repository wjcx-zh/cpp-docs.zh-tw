---
title: "終結視窗物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架視窗, 終結"
  - "視窗物件, 刪除"
  - "視窗物件, 終結"
  - "視窗物件, 移除"
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 終結視窗物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在使用者完成以視窗時，必須謹慎地以您的子視窗終結 C\+\+ 視窗物件。  如果沒有終結這些物件，您的應用程式不會復原其記憶體。  所幸，架構處理視窗終結以及建立框架視窗、檢視和對話方塊。  如果您建立其他視窗，您要負責終結它們。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [從 HWND 中斷連結 CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [一般視窗建立順序](../mfc/general-window-creation-sequence.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)