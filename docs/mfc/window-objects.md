---
title: "視窗物件 | Microsoft Docs"
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
  - "框架視窗 [C++], C++ 視窗物件"
  - "HWND"
  - "HWND, 視窗物件"
  - "訊息 [C++], Windows"
  - "MFC [C++], 視窗"
  - "物件 [C++], 視窗"
  - "Visual C++, 視窗物件"
  - "視窗訊息 [C++]"
  - "視窗物件 [C++]"
  - "視窗 [C++], C++ 視窗物件"
  - "Windows 視窗 [C++]"
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 視窗物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供類別封裝視窗的 `HWND` 控制代碼的 [CWnd](../mfc/reference/cwnd-class.md) 。  `CWnd` 物件是 C \+\+. 表示 Windows 視窗，但包含它的視窗物件，區別 `HWND` 。  使用 `CWnd` 衍生您自己的子視窗類別或衍生自 `CWnd`的許多 MFC 類別之一。  `CWnd` 類別是所有視窗的基底類別，包括了框架視窗、對話方塊、子視窗、控制項和控制項的資料行，例如工具列。  以了解 [C \+\+. 視窗物件和 HWND 之間的關聯性。](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) 為與 MFC 的有效程式設計很重要。  
  
 MFC 提供視窗的一些預設功能和管理，不過，您可以從 `CWnd` 衍生您自己的類別和使用它的成員函式自訂所提供的功能。  您可以使用 `CWnd` 成員函式，建構 `CWnd` 物件並呼叫它的 [建立](../Topic/CWnd::Create.md) 成員函式建立子視窗，然後自訂子視窗。  您在框架視窗中嵌入衍生自 [CView](../mfc/reference/cview-class.md)的物件，例如表單檢視或樹狀檢視，。  然後您可以分割窗格支援您的文件多重檢視，提供由 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)類別。  
  
 每個物件從類別 `CWnd` 包含衍生自的訊息對應，您可以將 Windows 訊息或命令 ID 給您的處理常式。  
  
 以程式設計的一般文獻中視窗的是學習如何良好資源使用 `CWnd` 成員函式，封裝 `HWND` API。  
  
## 操作的函式在 CWnd  
 `CWnd` 及其 [衍生的視窗類別](../mfc/derived-window-classes.md) 提供建構函式、解構函式和成員函式來初始化物件，建立基本的 Windows 結構和存取封裝的 `HWND`。  `CWnd` 也提供封裝所傳送的訊息 Windows API，存取視窗的狀態，轉換座標，更新，移動，存取剪貼簿和許多其他工作的成員函式。  採用 `HWND` 引數的大部分 Windows 視窗管理 API 是封裝在 `CWnd`的成員函式。  函式及其參數的名稱在 `CWnd` 成員函式被保存。  如需 `CWnd`封裝的 Windows API 的詳細資訊，請參閱 [CWnd](../mfc/reference/cwnd-class.md)。  
  
## CWnd 和 Windows 訊息  
 其中一個 `CWnd` 的主要目的是處理 Windows 訊息的介面，例如 `WM_PAINT` 或 `WM_MOUSEMOVE`。  許多 `CWnd` 的成員函式標準訊息 \(這些處理常式會識別項 **afx\_msg** 和前置詞開頭「已開啟」，例如 `OnPaint` 和 **OnMouseMove**。  [訊息處理和對應](../mfc/message-handling-and-mapping.md) 詳細處理涵蓋的訊息和內部例外狀況的訊息。  其中的資訊是否套用與您自行建立特殊的框架視窗。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [C\+\+ 視窗物件和 HWND 之間的關聯性](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [衍生的視窗類別](../mfc/derived-window-classes.md)  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [終結視窗物件](../mfc/destroying-window-objects.md)  
  
-   [從 HWND 中斷連結 CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [使用視窗物件](../mfc/working-with-window-objects.md)  
  
-   [裝置內容。](../mfc/device-contexts.md):將動畫與裝置無關之視窗的物件  
  
-   [圖形物件](../mfc/graphic-objects.md):筆刷，字型，點陣圖，調色盤，區域  
  
## 請參閱  
 [Windows](../mfc/windows.md)