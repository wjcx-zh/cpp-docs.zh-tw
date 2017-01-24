---
title: "清單方塊樣式 | Microsoft Docs"
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
  - "LBS_STANDARD"
  - "LBS_NODATA"
  - "LBS_OWNERDRAWVARIABLE"
  - "LBS_EXTENDEDSEL"
  - "LBS_USETABSTOPS"
  - "LBS_WANTKEYBOARDINPUT"
  - "LBS_NOTIFY"
  - "LBS_DISABLENOSCROLL"
  - "LBS_HASSTRINGS"
  - "LBS_NOREDRAW"
  - "LBS_NOSEL"
  - "LBS_NOINTEGRALHEIGHT"
  - "LBS_MULTICOLUMN"
  - "LBS_SORT"
  - "LBS_MULTIPLESEL"
  - "LBS_OWNERDRAWFIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LBS_DISABLENOSCROLL 常數"
  - "LBS_EXTENDEDSEL 常數"
  - "LBS_HASSTRINGS 常數"
  - "LBS_MULTICOLUMN 常數"
  - "LBS_MULTIPLESEL 常數"
  - "LBS_NODATA 常數"
  - "LBS_NOINTEGRALHEIGHT 常數"
  - "LBS_NOREDRAW 常數"
  - "LBS_NOSEL 常數"
  - "LBS_NOTIFY 常數"
  - "LBS_OWNERDRAWFIXED 常數"
  - "LBS_OWNERDRAWVARIABLE 常數"
  - "LBS_SORT 常數"
  - "LBS_STANDARD 常數"
  - "LBS_USETABSTOPS 常數"
  - "LBS_WANTKEYBOARDINPUT 常數"
  - "清單方塊, 樣式"
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 清單方塊樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **LBS\_DISABLENOSCROLL** 在清單方塊中未包含足夠的項目可以捲動時，清單方塊會顯示已停用的垂直捲軸。  若沒有這個樣式，在清單方塊中未包含足夠的項目時，捲軸會隱藏。  
  
-   **LBS\_EXTENDEDSEL** 使用 SHIFT 鍵和滑鼠或特殊按鍵組合，使用者可以選取多個項目。  
  
-   **LBS\_HASSTRINGS** 指定包含以字串組成的項目之主控描繪清單方塊。  清單方塊維護記憶體和字串的指標，讓應用程式可以使用 `GetText` 成員函式來擷取文字的特定項目。  
  
-   **LBS\_MULTICOLUMN** 指定水平捲動的多個資料行清單方塊。  `SetColumnWidth` 成員函式設定資料行的寬度。  
  
-   **LBS\_MULTIPLESEL** 每次使用者按一下或按兩下字串，字串選取範圍切換。  可以選取任何數目的字串。  
  
-   **LBS\_NODATA** 指定無資料清單方塊。  當清單方塊的項目計數會超過一千時，請指定此樣式。  無資料清單方塊也必須有 **LBS\_OWNERDRAWFIXED** 樣式，不過不能有 **LBS\_SORT** 和 **LBS\_HASSTRINGS** 樣式。  
  
     無資料清單方塊類似主控描繪清單方塊，除了它的項目不包含字串或點陣圖資料。  加入、插入或刪除項目的命令永遠會忽略任何指定的項目資料；在清單方塊尋找字串的要求永遠會失敗。  當需要繪製項目時，系統會傳送 `WM_DRAWITEM` 訊息至主控視窗項目。  `DRAWITEMSTRUCT` 結構的 itemID 成員 \(與 `WM_DRAWITEM` 訊息傳送\) 指示要繪製項目的行號。  無資料清單方塊不傳送 `WM_DELETEITEM` 資訊。  
  
-   **LBS\_NOINTEGRALHEIGHT** 在建立清單方塊時，清單方塊的大小就是應用程式所指定的大小。  通常，視窗會調整清單方塊的大小，使清單方塊不會只顯示項目的部份。  
  
-   **LBS\_NOREDRAW** 當有變更時，清單方塊顯示不會更新。  這個樣式可以藉由傳送 **WM\_SETREDRAW** 訊息來隨時變更。  
  
-   **LBS\_NOSEL** 指定清單方塊包含可檢視但不會被選取的項目。  
  
-   **LBS\_NOTIFY** 每當使用者按一下或按兩下字串時，父視窗會收到輸入訊息。  
  
-   **LBS\_OWNERDRAWFIXED** 清單方塊的擁有人負責繪製它的內容；清單方塊內的項目有相同的高度。  
  
-   **LBS\_OWNERDRAWVARIABLE** 清單方塊的擁有人負責繪製它的內容；清單方塊內的項目的高度是可變的。  
  
-   **LBS\_SORT** 清單方塊中的字串依字母順序排序。  
  
-   **LBS\_STANDARD** 清單方塊中的字串依字母順序排序，並且每當使用者按一下或按兩下字串時，父視窗收到輸入訊息。  清單方塊的各個邊都包含邊界。  
  
-   **LBS\_USETABSTOPS** 在繪製自己的字串時，允許清單方塊辨識和展開定位字元。  預設的定位點位置是 32 個對話方塊單位。\(對話方塊單位是水平或垂直距離。  一個水平對話方塊單位等於目前對話基底寬度單位的四分之一。  對話方塊基本單位根據目前系統字型的高度和寬度計算。  **GetDialogBaseUnits** Windows 函式會傳回目前對話基本單位，以像素為單位。\)這個樣式不應該與 **LBS\_OWNERDRAWFIXED** 一起使用。  
  
-   **LBS\_WANTKEYBOARDINPUT** 當清單方塊有輸入焦點時，當使用者按下按鍵，則清單方塊的擁有者收到 `WM_VKEYTOITEM` 或 `WM_CHARTOITEM` 訊息。  這樣讓應用程式可以執行特殊輸入的處理。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../Topic/CListBox::Create.md)   
 [List Box Styles](http://msdn.microsoft.com/library/windows/desktop/bb775149)