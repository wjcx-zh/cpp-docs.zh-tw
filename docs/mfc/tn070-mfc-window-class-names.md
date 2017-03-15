---
title: "TN070：MFC 視窗類別名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN070"
  - "視窗類別名稱"
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN070：MFC 視窗類別名稱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 MFC Windows 使用反映視窗功能的動態建立的類別名稱。  MFC 提供了框架視窗、檢視和應用程式所產生的快顯視窗動態產生的類別名稱。  MFC 應用程式和控制項所產生的對話方塊有 Windows 所提供的名稱所討論之視窗的類別。  
  
 您可以註冊視窗類別並用它取代動態提供的類別名稱在 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)覆寫。  它們由 MFC 提供的類別名稱符合了下列兩個形式:  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 取代 `%x` 字元的十六進位數字從 [名稱](http://msdn.microsoft.com/library/windows/desktop/ms633576) 結構的資料填入。  MFC 使用這項技術，以便要求相同 **WNDCLASS** 結構的多個 C\+\+ 類別可以共用相同的已登錄的視窗類別。  不同於大部分簡單的 Win32 應用程式， MFC 應用程式只有一個 **WNDPROC**，因此，您可以輕鬆地共用 **WNDCLASS** 結構節省時間和記憶體。  顯示的 `%x` 字元的可取代的值以上如下:  
  
-   **WNDCLASS.hInstance**  
  
-   **WNDCLASS.style**  
  
-   **WNDCLASS.hCursor**  
  
-   **WNDCLASS.hbrBackground**  
  
-   **WNDCLASS.hIcon**  
  
 使用第一個表單 \(`Afx:%x:%x`\)，當 **hCursor**和 **hbrBackground**和 **hIcon** 都 **NULL**時。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)   
 [TN020：ID 命名和編號慣例](../mfc/tn020-id-naming-and-numbering-conventions.md)