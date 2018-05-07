---
title: 控制類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffd7b3b7d2eb9db68fd61ac693c65d87b2ee62d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="control-classes"></a>控制項類別
控制項類別會封裝各種不同的範圍從靜態文字控制項到樹狀目錄控制項的標準 Windows 控制項。 此外，MFC 提供了一些新的控制項，包括具有點陣圖和控制列按鈕。  
  
 控制項類別名稱結尾 」**Ctrl**」 是 Windows 95 和 Windows NT 3.51 版的新功能。  
  
## <a name="static-display-controls"></a>靜態顯示控制項  
 [CStatic](../mfc/reference/cstatic-class.md)  
 靜態顯示在視窗中。 靜態控制項用來加上標籤，方塊中，或個別對話方塊或視窗中的其他控制項。 它們可能也會顯示圖形影像而不是文字或方塊。  
  
## <a name="text-controls"></a>文字控制項  
 [CEdit](../mfc/reference/cedit-class.md)  
 可編輯文字控制項視窗。 編輯控制項用來接受使用者輸入文字。  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 支援編輯方塊操作的網際網路通訊協定 (IP) 位址。  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 使用者可以輸入和編輯文字控制項。 不同於封裝中的控制項`CEdit`，rich edit 控制項支援的字元和段落格式以及 OLE 物件。  
  
## <a name="controls-that-represent-numbers"></a>表示數字的控制項  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 包含使用者移到選取的值或一組值的滑桿控制項。  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 一對箭號按鈕使用者可以按一下來增加或減少值。  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 顯示會逐漸填滿從左到右，表示作業的進度的矩形。  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 捲軸控制項視窗。 類別提供捲軸，作為對話方塊或視窗中，使用者可以透過此指定的範圍內的位置中的控制項的功能。  
  
## <a name="buttons"></a>按鈕  
 [CButton](../mfc/reference/cbutton-class.md)  
 按鈕控制項視窗。 類別會提供按鈕、 核取方塊，或在對話方塊或視窗中的選項按鈕的程式設計介面。  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 具有點陣圖，而不是文字標題的按鈕。  
  
## <a name="lists"></a>清單  
 [CListBox](../mfc/reference/clistbox-class.md)  
 清單方塊控制項視窗。 清單方塊會顯示使用者可以檢視和選取的項目清單。  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 提供 Windows 清單方塊的功能。可讓使用者在清單方塊內移動清單方塊項目，例如檔案名稱和字串常值。 使用這項功能的清單方塊適用於項目清單以外的字母順序，例如包含專案中的 路徑名稱或檔案。  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 下拉式方塊控制項視窗。 下拉式方塊包含編輯控制項和清單方塊。  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 藉由提供影像清單的支援，擴充下拉式方塊控制項。  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 顯示使用者可以檢查或清除，每個項目旁的核取方塊的項目清單。  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 顯示的項目，每個圖示和標籤，在檔案總管 的類似於右窗格的方式所組成的集合。  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 顯示圖示和標籤排列方式，類似於左窗格的 [檔案總管] 中的階層式清單。  
  
## <a name="toolbars-and-status-bars"></a>工具列和狀態列  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具列通用控制項的功能。 大部分的 MFC 程式使用[CToolBar](../mfc/reference/ctoolbar-class.md)而不是這個類別。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平視窗中，通常會分成的窗格，在其中應用程式可以顯示狀態資訊。 大部分的 MFC 程式使用[CStatusBar](../mfc/reference/cstatusbar-class.md)而不是這個類別。  
  
## <a name="miscellaneous-controls"></a>其他控制項  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 顯示簡單的視訊剪輯。  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 小型快顯視窗顯示單行說明應用程式中工具用途的文字。  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 支援擴充的編輯控制項或簡單的行事曆介面控制項，可讓使用者選擇的特定日期或時間值。  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 顯示標題或資料行的標籤。  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 支援簡單的行事曆介面控制，可讓使用者選取日期。  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 具有索引標籤的使用者可以按一下，類似於檔案櫃中的控制項。  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 可讓使用者建立的作用的按鍵組合，其中使用者可以按下以快速執行的動作。  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 會呈現標記文字，並啟動適當的應用程式，當使用者按一下內嵌的連結。  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。  
  
## <a name="related-classes"></a>相關的類別  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 提供 Windows 影像清單的功能。 影像清單是搭配清單控制項和樹狀目錄控制項使用。 也可以用來儲存和封存一組大小相同的點陣圖。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Windows 控制項相關聯的所有檢視的基底類別。 以下將詳述控制項為基礎的檢視。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準的檢視編輯控制項。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 檢視包含豐富的 Windows 編輯控制項。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含 Windows 樹狀目錄控制項的檢視。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

