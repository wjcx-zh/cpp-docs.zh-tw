---
title: "TN014： 自訂控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.controls
dev_langs:
- C++
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4ffc4f26ed365673cdfb525c2bf3653827cc4ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn014-custom-controls"></a>TN014：自訂控制項
本附註將描述自訂和自繪控制項的 MFC 支援。 它也描述動態子類別化，並描述之間的關聯性[CWnd](../mfc/reference/cwnd-class.md)物件和`HWND`s。  
  
 MFC 範例應用程式 CTRLTEST 將說明如何使用多種自訂控制項。 請參閱 MFC 一般範例的原始程式碼[CTRLTEST](../visual-cpp-samples.md)和線上說明。  
  
## <a name="owner-draw-controlsmenus"></a>主控描繪控制項/功能表  
 Windows 使用 Windows 訊息為主控描繪控制項和功能表提供支援。 任何控制項或功能表的父視窗都會收到這些訊息，並呼叫函式予以回應。 您可以覆寫這些函式以自訂您的主控描繪控制項或功能表的視覺外觀和行為。  
  
 MFC 可直接支援包含下列函式的主控描繪：  
  
- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)  
  
- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)  
  
- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)  
  
- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)  
  
 您可以在 `CWnd` 衍生類別中覆寫這些函式，以實作自訂繪製行為。  
  
 這個方法不會產生可重複使用的程式碼。 如果兩個不同的 `CWnd` 類別中有兩個類似的控制項，您就必須在這兩個位置實作自訂控制項行為。 MFC 支援的自繪控制項架構可解決這個問題。  
  
## <a name="self-draw-controls-and-menus"></a>自繪控制項和功能表  
 MFC 提供的預設實作 (在`CWnd`和[CMenu](../mfc/reference/cmenu-class.md)類別) 標準的主控描繪訊息。 這個預設實作會將主控描繪參數解碼，並且將主控描繪訊息委派至控制項或功能表。 這個過程稱為自繪 (Self-draw)，因為繪圖程式碼位於控制項或功能表的類別中，而不是主控視窗中。  
  
 使用自繪控制項就能建置可重複使用的控制項類別，這些類別會使用主控描繪語意顯示控制項。 繪製控制項的程式碼位於控制項類別中，而非其父代中。 這是一種物件導向的自訂控制項程式設計方法。 將下列函式清單加入至自繪類別：  
  
-   自繪按鈕：  
  
 ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw this button  
 ```  
  
-   自繪功能表：  
  
 ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this menu  
 ```  
  
-   自繪清單方塊：  
  
 ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this list box  
 
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this list box  
 ```  
  
-   自繪下拉式方塊：  
  
 ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this combo box  
 
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this combo box  
 ```  
  
 如需詳細資訊，在主控描繪結構 ([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md)， [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md)， [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md)，和[DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)) 請參閱 MFC 文件`CWnd::OnDrawItem`， `CWnd::OnMeasureItem`， `CWnd::OnCompareItem`，和`CWnd::OnDeleteItem`分別。  
  
## <a name="using-self-draw-controls-and-menus"></a>使用自繪控制項和功能表  
 若是自繪功能表，您必須同時覆寫 `OnMeasureItem` 和 `OnDrawItem` 方法。  
  
 若是自繪清單方塊和下拉式方塊，您必須覆寫 `OnMeasureItem` 和 `OnDrawItem`。 您必須為清單方塊指定 `LBS_OWNERDRAWVARIABLE` 樣式，或是為對話方塊範本中的下拉式方塊指定 `CBS_OWNERDRAWVARIABLE` 樣式。 `OWNERDRAWFIXED` 樣式無法搭配自繪項目使用，因為在自繪控制項附加至清單方塊之前就已決定了固定的項目高度  (您可以使用方法[CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight)和[CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight)克服這項限制。)  
  
 轉換成 `OWNERDRAWVARIABLE` 樣式會強制系統將 `NOINTEGRALHEIGHT` 樣式套用至控制項。 因為控制項無法計算可改變大小的項目之整數高度，所以會忽略 `INTEGRALHEIGHT` 的預設樣式，而且控制項永遠是 `NOINTEGRALHEIGHT`。 如果您的項目高度固定，就可以藉由將控制項大小指定為項目大小的整數倍數防止繪製部分項目。  
  
 對於採用 `LBS_SORT` 或 `CBS_SORT` 模式的自繪清單方塊和下拉式方塊，您必須覆寫 `OnCompareItem` 方法。  
  
 對於自繪清單方塊和下拉式方塊，通常不會覆寫 `OnDeleteItem`。 如果您要執行任何特殊處理，可以覆寫 `OnDeleteItem`。 適用的情況是，每個清單方塊或下拉式方塊項目都儲存了額外的記憶體或其他資源。  
  
## <a name="examples-of-self-drawing-controls-and-menus"></a>自繪控制項和功能表的範例  
 MFC 一般範例[CTRLTEST](../visual-cpp-samples.md)提供了自繪功能表和自繪清單方塊的範例。  
  
 最常見的自繪按鈕範例是點陣圖按鈕。 點陣圖按鈕是指顯示一個、兩個或三個點陣圖影像代表不同狀態的按鈕。 MFC 類別中提供這個範例[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)。  
  
## <a name="dynamic-subclassing"></a>動態子類別化  
 有時候您會想要變更已存在物件的功能。 先前的範例會要求您在建立控制項之前進行自訂。 而動態子類別化可讓您自訂已建立的控制項。  
  
 子類別化是取代 Windows 詞彙[WndProc](http://msdn.microsoft.com/en-us/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26)與自訂視窗的`WndProc`，然後呼叫舊`WndProc`預設功能。  
  
 子類別化不應與 C++ 類別衍生混淆。 釐清，c + + 詞彙*基底類別*和*衍生的類別*類似於*超級類別*和*子類別*windows物件模型。 使用 MFC 的 C++ 衍生和 Windows 子類別化在功能上很類似，但 C++ 不支援動態子類別化。  
  
 `CWnd` 類別提供了 C++ 物件 (衍生自 `CWnd`) 與 Windows 視窗物件 (稱為 `HWND`) 之間的連接。  
  
 有三種在這些物件之間產生關聯的常見方式：  
  
- `CWnd` 會建立 `HWND`。 您可以建立衍生自 `CWnd` 的類別，藉此修改衍生類別中的行為。 `HWND`呼叫您的應用程式時，會建立[cwnd:: Create](../mfc/reference/cwnd-class.md#create)。  
  
-   應用程式會將 `CWnd` 附加至現有的 `HWND`。 現有視窗的行為則不會修改。 這是委派的情況下，即可進行呼叫[CWnd::Attach](../mfc/reference/cwnd-class.md#attach)別名的現有`HWND`至`CWnd`物件。  
  
- `CWnd` 會附加至現有的 `HWND`，而您可以修改衍生類別中的行為。 這稱為動態子類別化，因為我們會在執行階段變更 Windows 物件的行為，以因此變更了類別。  
  
 您可以使用的方法，以達到動態子類別化[CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow)和[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)。  
  
 這兩種常式都會將 `CWnd` 物件附加至現有的 `HWND`。 `SubclassWindow` 是直接採用 `HWND`。 `SubclassDlgItem` 是採用控制項 ID 和父視窗的 Helper 函式。 `SubclassDlgItem` 的設計是將 C++ 物件附加至從對話方塊範本建立的對話方塊控制項。  
  
 請參閱[CTRLTEST](../visual-cpp-samples.md)數個範例的使用時機的範例`SubclassWindow`和`SubclassDlgItem`。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

