---
title: "視窗解構序列 | Microsoft Docs"
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
  - "CWnd 物件, 解構序列"
  - "終結視窗"
  - "解構, 視窗"
  - "序列 [C++]"
  - "序列 [C++], 視窗解構"
  - "視窗 [C++], 終結"
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 視窗解構序列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 架構，，當使用者關閉框架視窗時，視窗的預設 [OnClose](../Topic/CWnd::OnClose.md) 處理常式呼叫 [DestroyWindow](../Topic/CWnd::DestroyWindow.md)。  呼叫的最後一個成員函式終結時，視窗的視窗是 [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)，進行一些清除，呼叫 [預設](../Topic/CWnd::Default.md) 成員函式執行視窗清除和最後呼叫虛擬成員函式 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)。  `PostNcDestroy` [CFrameWnd](../mfc/reference/cframewnd-class.md) 的實作刪除 C\+\+ 視窗物件。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [從 HWND 中斷連結 CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## 請參閱  
 [終結視窗物件](../mfc/destroying-window-objects.md)