---
title: "框架視窗樣式 (C++) | Microsoft Docs"
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
  - "框架視窗 [C++], 樣式"
  - "MFC [C++], 框架視窗"
  - "PreCreateWindow 方法, 設定視窗樣式"
  - "樣式, 視窗"
  - "視窗樣式 [C++]"
  - "視窗 [C++], MFC"
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架視窗樣式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得與這個框架的框架視窗適用於大部分的程式，您可以使用進階的功能 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 和 MFC 全域函式 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md)，不過，您可以取得更多的彈性。  `PreCreateWindow` 是 `CWnd`的成員函式。  
  
 如果您套用至 **WS\_HSCROLL** 和 **WS\_VSCROLL** 樣式主框架視窗，就會套用到 **MDICLIENT** 視窗，讓使用者可以捲動 **MDICLIENT** 區域。  
  
 如果預設視窗的 **FWS\_ADDTOTITLE** 樣式位元設定為 \(為\)，檢視呼叫框架視窗哪些標題會顯示在視窗的標題列會根據檢視的文件名稱。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [處理的 MDI 子視窗 \(MDICLIENT\)](../mfc/managing-mdi-child-windows.md)，在包含 MDI 子視窗的 MDI 框架內的視窗  
  
-   [變更視窗的樣式由 MFC 建立](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [視窗樣式](../mfc/reference/window-styles.md)  
  
## 請參閱  
 [框架視窗](../mfc/frame-windows.md)