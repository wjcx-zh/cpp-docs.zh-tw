---
title: "終結框架視窗 | Microsoft Docs"
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
  - "PostNcDestroy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Default 方法"
  - "終結框架視窗"
  - "DestroyWindow 方法"
  - "文件框架視窗, 終結"
  - "框架視窗 [C++], 終結"
  - "MFC [C++], 框架視窗"
  - "OnClose 方法"
  - "OnNcDestroy 方法, 和框架視窗"
  - "PostNcDestroy 方法"
  - "視窗 [C++], 終結"
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 終結框架視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 架構處理視窗終結以及撰寫這些視窗與框架文件和檢視。  如果您建立其他視窗，您要負責終結它們。  
  
 在 MFC 架構，當使用者關閉框架視窗時，視窗的預設 [OnClose](../Topic/CWnd::OnClose.md) 處理常式呼叫 [DestroyWindow](../Topic/CWnd::DestroyWindow.md)。  當 Windows 視窗終結時，呼叫的最後一個成員函式是 [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)，進行一些清除，呼叫 [預設](../Topic/CWnd::Default.md) 成員函式執行視窗清除和最後呼叫虛擬成員函式 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)。  `PostNcDestroy` 的 [CFrameWnd](../mfc/reference/cframewnd-class.md) 實作刪除 C\+\+ 視窗物件。  您不應該在框架視窗使用 C\+\+ **delete** 運算子。  請改用 `DestroyWindow`。  
  
 在主視窗關閉時，應用程式會關閉。  如果有修改的未儲存的文件，架構會顯示訊息方塊存取文件是否應儲存並確保適當的文件，必要時會保存。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)