---
title: "清單方塊樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LBS_STANDARD
- LBS_NODATA
- LBS_OWNERDRAWVARIABLE
- LBS_EXTENDEDSEL
- LBS_USETABSTOPS
- LBS_WANTKEYBOARDINPUT
- LBS_NOTIFY
- LBS_DISABLENOSCROLL
- LBS_HASSTRINGS
- LBS_NOREDRAW
- LBS_NOSEL
- LBS_NOINTEGRALHEIGHT
- LBS_MULTICOLUMN
- LBS_SORT
- LBS_MULTIPLESEL
- LBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- LBS_NOSEL constant [MFC]
- LBS_NOREDRAW constant [MFC]
- LBS_HASSTRINGS constant [MFC]
- LBS_OWNERDRAWFIXED constant [MFC]
- LBS_WANTKEYBOARDINPUT constant [MFC]
- LBS_STANDARD constant [MFC]
- LBS_MULTIPLESEL constant [MFC]
- LBS_OWNERDRAWVARIABLE constant [MFC]
- LBS_DISABLENOSCROLL constant [MFC]
- LBS_NODATA constant [MFC]
- list boxes [MFC], styles
- LBS_EXTENDEDSEL constant [MFC]
- LBS_MULTICOLUMN constant [MFC]
- LBS_NOTIFY constant [MFC]
- LBS_USETABSTOPS constant [MFC]
- LBS_NOINTEGRALHEIGHT constant [MFC]
- LBS_SORT constant
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f52734e26d1965811aded67bc1e1dde6a2c28bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="list-box-styles"></a>清單方塊樣式
-   **LBS_DISABLENOSCROLL**清單方塊會顯示已停用的垂直捲軸當清單方塊中未包含足夠的項目捲動。 若沒有這個樣式，在清單方塊中未包含足夠的項目時，捲軸會隱藏。  
  
-   **LBS_EXTENDEDSEL**使用者可以選取多個項目，使用 SHIFT 鍵和滑鼠或特殊按鍵組合。  
  
-   **LBS_HASSTRINGS**指定主控描繪清單方塊，其中包含由字串組成的項目。 清單方塊會維護記憶體和字串的指標，讓應用程式可以使用 `GetText` 成員函式來擷取特定項目的文字。  
  
-   **LBS_MULTICOLUMN**指定水平捲動的資料行清單方塊。 `SetColumnWidth` 成員函式可設定資料行的寬度。  
  
-   **LBS_MULTIPLESEL**每次使用者按一下或按兩下字串切換字串選取範圍。 您可以選取任何數目的字串。  
  
-   **LBS_NODATA**指定無資料清單方塊。 當清單方塊的項目計數會超過一千時，請指定此樣式。 無資料清單方塊也必須具有**LBS_OWNERDRAWFIXED**樣式，但是不能有**LBS_SORT**或**LBS_HASSTRINGS**樣式。  
  
     無資料清單方塊類似於主控描繪清單方塊，但它的項目不包含字串或點陣圖資料。 加入、插入或刪除項目的命令永遠會忽略任何指定的項目資料；在清單方塊尋找字串的要求永遠會失敗。 需要繪製項目時，系統會傳送 `WM_DRAWITEM` 訊息至主控視窗。 `DRAWITEMSTRUCT` 結構的 itemID 成員 (使用 `WM_DRAWITEM` 訊息傳遞) 指定要繪製項目的行號。 無資料清單方塊不會傳送 `WM_DELETEITEM` 資訊。  
  
-   **LBS_NOINTEGRALHEIGHT**清單方塊的大小是建立清單方塊時，應用程式所指定的大小相同。 通常，Windows 會調整清單方塊的大小，使清單方塊不會只顯示一部分的項目。  
  
-   **LBS_NOREDRAW**清單方塊顯示不會更新變更時。 可以隨時變更此樣式，藉由傳送**WM_SETREDRAW**訊息。  
  
-   **LBS_NOSEL**指定清單方塊包含您可以檢視但未選取的項目。  
  
-   **LBS_NOTIFY**每當使用者按一下或按兩下字串時，父視窗會收到輸入的訊息。  
  
-   **LBS_OWNERDRAWFIXED**清單方塊的擁有者會負責繪製其內容; 清單方塊中的項目都有相同的高度。  
  
-   **LBS_OWNERDRAWVARIABLE**清單方塊的擁有者會負責繪製其內容; 清單方塊中的項目高度是可變的。  
  
-   **LBS_SORT**清單方塊中的字串會依字母順序排序。  
  
-   **LBS_STANDARD**英文字母順序排序清單方塊中的字串，每當使用者按一下或按兩下字串時，父視窗會收到輸入的訊息。 清單方塊的每一邊都包含邊界。  
  
-   **LBS_USETABSTOPS**允許清單方塊辨識和展開定位點字元繪製字串時。 預設的定位點位置是 32 個對話方塊單位 (對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 **GetDialogBaseUnits** Windows 函式會傳回目前對話方塊基本單位像素為單位。)這個樣式不應與**LBS_OWNERDRAWFIXED**。  
  
-   **LBS_WANTKEYBOARDINPUT**清單方塊的擁有者會收到`WM_VKEYTOITEM`或`WM_CHARTOITEM`訊息清單方塊具有輸入焦點時使用者按下按鍵時。 這樣可以讓應用程式在鍵盤輸入時執行特殊的處理。  
  
## <a name="see-also"></a>請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../../mfc/reference/clistbox-class.md#create)   
 [清單方塊樣式](http://msdn.microsoft.com/library/windows/desktop/bb775149)

