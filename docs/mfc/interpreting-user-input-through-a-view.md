---
title: "透過檢視解譯使用者輸入 | Microsoft Docs"
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
  - "CView 類別, 解譯使用者輸入"
  - "輸入, 檢視類別"
  - "透過檢視解譯使用者輸入"
  - "使用者輸入, 透過檢視類別解譯"
  - "檢視, 使用者介面和輸入"
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 透過檢視解譯使用者輸入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個檢視的其他成員函式處理並說明所有使用者輸入。  您通常會定義訊息處理常式中的檢視類別的成員函式處理:  
  
-   視窗滑鼠和鍵盤動作產生的 [訊息](../mfc/messages.md) 。  
  
-   從功能表、工具列按鈕和快速鍵的[命令](../mfc/user-interface-objects-and-command-ids.md) 。  
  
 這些訊息處理常式成員函式說明下列動作在資料輸入，選取範圍或編輯，包括移動的資料加入至剪貼簿:  
  
-   滑鼠移動並按一下、按兩下和拖曳  
  
-   按鍵  
  
-   功能表命令  
  
 哪些 Windows 訊息您要處理視應用程式的需要。  
  
 [訊息處理和對應的主題](../mfc/message-handling-and-mapping.md) 說明如何指派功能表項目和其他使用者介面物件對命令以及如何將命令繫結至處理函式。  [訊息處理和對應的主題](../mfc/message-handling-and-mapping.md) 也說明 MFC 如何傳送命令並傳送標準 Windows 訊息至包含其處理常式的物件。  
  
 例如，您的應用程式可能需要實作在檢視中直接滑鼠繪圖。  Scribble 範例顯示如何分別處理 `WM_LBUTTONDOWN`、 `WM_MOUSEMOVE`和 `WM_LBUTTONUP` 訊息開始，繼續並結束線段的繪圖。  另一方面，您有時可能需要說明您要按一下滑鼠以選取範圍。  您的意圖的 `OnLButtonDown` 處理常式函式判斷使用者是否繪製或選取。  如果選取，處理常式會判斷點選作業是否發生在物件陣列中繫結至檢視的，因此，如果有，修改顯示物件中選取。  
  
 您的檢視也可以處理某些命令，例如從編輯\] 功能表剪下，複製，貼上，使用剪貼簿，或刪除選取的資料。  這種處理常式會呼叫某些類別 `CWnd` 的剪貼簿相關成員函式將選取的資料項目加入至剪貼簿。  
  
## 請參閱  
 [使用檢視](../mfc/using-views.md)