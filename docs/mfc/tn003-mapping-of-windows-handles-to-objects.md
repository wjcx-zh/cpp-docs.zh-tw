---
title: "TN003：將 Windows 控制代碼對應到物件 | Microsoft Docs"
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
  - "vc.mapping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制代碼對應"
  - "對應, Windows 控制代碼到物件"
  - "TN003"
  - "Windows 控制代碼到物件 [C++]"
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN003：將 Windows 控制代碼對應到物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註描述支援映像視窗物件控制代碼 C\+\+ 物件的 MFC 常式。  
  
## 問題  
 視窗物件由具有 C\+\+ 的 MFC 類別包裝視窗物件控制項物件的各種 [控制代碼](http://msdn.microsoft.com/library/windows/desktop/aa383751) 物件通常表示。  包裝 MFC 類別庫的函式的控制代碼可讓您尋找包裝視窗物件具有特殊控制代碼的 C\+\+ 物件。  不過，物件有時沒有 C \+\+. 包裝函式物件，而這些時間系統建立暫存物件以 C\+\+ 包裝函式。  
  
 視窗物件使用控制代碼對應如下:  
  
-   HWND \([CWnd](../mfc/reference/cwnd-class.md) 和 `CWnd`衍生類別\)  
  
-   HDC \([CDC](../mfc/reference/cdc-class.md) 和 `CDC`衍生類別\)  
  
-   項目 \([CMenu](../mfc/reference/cmenu-class.md)\)  
  
-   HPEN \([CGdiObject](../mfc/reference/cgdiobject-class.md)\)  
  
-   HBRUSH \(`CGdiObject`\)  
  
-   HFONT \(`CGdiObject`\)  
  
-   HBITMAP \(`CGdiObject`\)  
  
-   HPALETTE \(`CGdiObject`\)  
  
-   HRGN \(`CGdiObject`\)  
  
-   HIMAGELIST \([CImageList](../mfc/reference/cimagelist-class.md)\)  
  
-   通訊端 \([CSocket](../mfc/reference/csocket-class.md)\)  
  
 將控制項加入至任何一個物件，您可以藉由呼叫靜態方法包裝控制項 `FromHandle`的 MFC 物件。  例如將 HWND 呼叫 `hWnd`，下列程式碼會傳回包裝 `hWnd`之 `CWnd` 的指標:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 如果 `hWnd` 沒有特定的包裝函式物件，暫存 `CWnd` 建立包裝 `hWnd`。  這樣做可以衍生自所有控制代碼的有效的 C\+\+ 物件。  
  
 在您有包裝函式物件之後，您可以從包裝函式類別的公用成員變數擷取其控制代碼。  在 `CWnd`的情況下， `m_hWnd` 包含物件的 HWND。  
  
## 附加至 MFC 物件的控制代碼  
 將新建立的控制代碼的包裝函式物件和一個控制代碼視窗物件，您可以呼叫 `Attach` 函式使兩個如同下列範例所示:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);  
```  
  
 這會使 `myWnd` 和 `hWnd`的永久對應中的項目。  呼叫 `CWnd::FromHandle(hWnd)` 會傳回 `myWnd`的指標。  當 `myWnd` 刪除，解構函式會呼叫 Windows 函式 [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) 自動終結 `hWnd` 。  如果此不希望，必須從 `myWnd` 中斷連接 `hWnd` ，以在終結物件前 `myWnd` \(通常，讓 `myWnd` 所定義\) 的範圍。  `Detach` 方法。  
  
```  
myWnd.Detach();  
```  
  
## 進一步了解暫存物件  
 暫存物件建立，就將尚未包裝函式物件 `FromHandle` 的控制代碼。  這些暫存物件從其控制代碼中斷並由 `DeleteTempMap` 函式刪除。  預設 [CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md) 自動呼叫支援暫存控制代碼對應的每個類別的 `DeleteTempMap` 。  這表示您無法假設對暫存物件的指標是有效傳遞問題的從指標取得函式的匯出。  
  
## 包裝函式物件和多執行緒  
 暫時和永久目標維護個別執行緒為基礎。  也就是另一個執行緒的 C\+\+ 包裝函式物件的執行緒無法存取，不論它是否暫時或永久。  
  
 若要將執行緒的這些物件與另一個，務必將它們當做其原生 `HANDLE` 型別。  透過 C \+\+. 從一個執行緒的包裝函式物件與另一個通常會造成未預期的結果。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)