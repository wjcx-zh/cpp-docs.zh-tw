---
title: "TN014：自訂控制項 | Microsoft Docs"
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
  - "vc.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自訂控制項 [MFC]"
  - "TN014"
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
caps.latest.revision: 21
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN014：自訂控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註說明 MFC 支援自訂和自繪製控制項。  它也說明動態子類別化，並說明 [CWnd](../mfc/reference/cwnd-class.md) 物件與 `HWND`之間的關聯性。  
  
 MFC 應用程式範例 CTRLTEST 將說明如何使用許多自訂控制項。  為一般 MFC 範例 [CTRLTEST](../top/visual-cpp-samples.md) 和線上說明請參閱原始程式碼。  
  
## 主控描繪控制項\/功能表  
 使用 Windows 訊息，視窗為主控描繪控制項和功能表提供支援。  父視窗的任何控制項或功能表接收這些訊息並呼叫回應的函式。  您可以覆寫這些函式自訂您的主控描繪控制項或功能表視覺外觀和行為。  
  
 MFC 支援直接與下列函式的主控描繪:  
  
-   [CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)  
  
-   [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)  
  
-   [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)  
  
-   [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)  
  
 您可以在您的 `CWnd` 衍生類別的這些函式實作自訂的行為。  
  
 這個方法不會產生可重複使用的程式碼。  如果您有兩個類似的控制項在兩個不同的 `CWnd` 類別，您必須實作在兩個位置的自訂控制項行為。  MFC 支援的自繪控制結構來解決這個問題。  
  
## 自繪製控制項和功能表  
 MFC 提供標準主控描繪訊息提供預設實作 \( `CWnd` 和 [CMenu](../mfc/reference/cmenu-class.md) 類別\)。  這個預設實作會解碼主控描繪參數和委派擁有者繪製訊息至控制項或功能表。  這會呼叫自繪製，因為繪圖程式碼在控制項或功能表的類別中，而不是主控視窗。  
  
 使用自繪製控制項中建立使用主控描繪語意顯示控制項的可重複使用的控制項類別。  繪製控制項的程式碼會在控制項類別，而非其父代。  這是一種物件導向方法對自訂控制項的程序。  加入下列清單至自繪製類別:  
  
-   對於自繪製按鈕:  
  
    ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw this button  
    ```  
  
-   對於自繪製功能表:  
  
    ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this menu  
    ```  
  
-   對於自繪製清單方塊:  
  
    ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this list box  
  
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this list box  
    ```  
  
-   對於自繪製下拉式方塊:  
  
    ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this combo box  
  
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this combo box  
    ```  
  
 如需主控描繪結構 \([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md)、 [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md)、 [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md)和 [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)\) 的詳細資料為個別 `CWnd::OnDrawItem`、 `CWnd::OnMeasureItem`、 `CWnd::OnCompareItem`和 `CWnd::OnDeleteItem` 請參閱 MFC 文件。  
  
## 使用自繪製控制項和功能表  
 若是自繪製功能表，您必須覆寫 `OnMeasureItem` 和 `OnDrawItem` 方法。  
  
 若是自繪製清單方塊和下拉式方塊，您必須覆寫 `OnMeasureItem` 和 `OnDrawItem`。  您必須為清單方塊指定 `LBS_OWNERDRAWVARIABLE` 樣式或 `CBS_OWNERDRAWVARIABLE` 樣式為在對話方塊樣板的下拉式方塊。  `OWNERDRAWFIXED` 樣式不會與自繪製項目一起使用，因為內建的項目高度是在繪製自控制項附加至清單方塊之前判斷。\(您可以使用 [CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md) 方法和 [CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md) 克服這項限制\)。  
  
 轉換成 `OWNERDRAWVARIABLE` 樣式會強制系統套用 `NOINTEGRALHEIGHT` 樣式套用至控制項。  因為控制項無法計算可改變大小的項目之整數高度， `INTEGRALHEIGHT` 預設樣式會被忽略，而控制項永遠是 `NOINTEGRALHEIGHT`。  如果您的專案是固定高度，您可以防止部分項目指定控制項大小是項目大小的整數乘數。  
  
 對於自繪清單方塊和下拉式方塊有 `LBS_SORT` 或 `CBS_SORT` 模式的，您必須覆寫 `OnCompareItem` 方法。  
  
 對於自繪清單方塊和下拉式方塊 `OnDeleteItem` ，通常不會被覆寫。  如果您要執行任何特殊的處理，您可以覆寫 `OnDeleteItem` 。  這只適用的情況是額外的記憶體或其他資源儲存與每個清單方塊或下拉式方塊項目。  
  
## 自繪控制項和功能表的範例  
 一般 MFC 範例 [CTRLTEST](../top/visual-cpp-samples.md) 提供自繪製功能表和自繪製清單方塊的範例。  
  
 自繪製按鈕的最常見的範例是一個點陣圖按鈕。  一個點陣圖按鈕是顯示不同狀態的，兩個或三個點陣圖影像的按鈕。  這個範例是在 MFC 類別 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)提供。  
  
## 動態子類別化  
 有時候您會想要變更已存在物件的功能。  在建立之前，前一個範例會要求您自訂控制項。  動態子類別化可以讓您自訂已建立的控制項。  
  
 子類別化是取代視窗的 [WndProc](http://msdn.microsoft.com/zh-tw/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) 與自訂的 `WndProc` 和呼叫的舊 `WndProc` 視窗的預設功能。  
  
 不應該與 C\+\+ 類別衍生混淆。  如需說明， C\+\+ 關鍵字 *基底類別* 和 *衍生類別* 類似 *超級類別* 和 *子類別* 在視窗物件模型。  使用 MFC 的 C\+\+ 子類別化和衍生的視窗的功能相同，不過， C\+\+ 不支援動態子類別化。  
  
 `CWnd` 類別提供 C \+\+ 物件 \(衍生自 `CWnd`\) 和 Windows 視窗物件之間的連接 \(稱為 `HWND`\)。  
  
 這些彼此相關的方式有三種常見的方式:  
  
-   `CWnd` 建立 `HWND`。  您可以從 `CWnd`衍生的類別會在衍生類別中的行為修改。  當應用程式呼叫 [CWnd::Create](../Topic/CWnd::Create.md)時，建立 `HWND` 。  
  
-   應用程式將 `CWnd` 附加至現有的 `HWND`。  不會修改現有的視窗的行為。  這是一個大小寫委派和透過呼叫別名的 [CWnd::Attach](../Topic/CWnd::Attach.md) 可讓您對 `CWnd` 物件的現有 `HWND` 。  
  
-   `CWnd` 附加至現有的 `HWND` ，而您可以修改在衍生類別中的行為。  這稱為動態子類別化，因為我們變更行為，因此類別，在執行階段的視窗物件。  
  
 使用 [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md) 方法和[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md) `` ，您可以讓動態子類別化。  
  
 兩個常式附加至現有的 `HWND`的 `CWnd` 物件。  `SubclassWindow` 直接採用 `HWND` 。  `SubclassDlgItem` 是使用控制項 ID 和父視窗的 Helper 函式。  `SubclassDlgItem` 為附加至從對話方塊樣板建立的對話方塊控制項的 C\+\+ 物件設計的。  
  
 何時參閱 [CTRLTEST](../top/visual-cpp-samples.md) 範例為幾個範例中使用 `SubclassWindow` 和 `SubclassDlgItem`。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)