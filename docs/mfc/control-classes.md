---
title: 控制類別 |Microsoft Docs
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
ms.openlocfilehash: a159677ffa12961e7f065b2cba2b1287c8ef7a58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432453"
---
# <a name="control-classes"></a>控制項類別

控制項類別會封裝各種不同的範圍從靜態文字控制項樹狀結構控制項的標準 Windows 控制項。 此外，MFC 提供了一些新的控制項，包括其中的點陣圖和控制列按鈕。

類別名稱結尾的控制項 」**Ctrl**」 是 Windows 95 和 Windows NT 3.51 版的新功能。

## <a name="static-display-controls"></a>靜態顯示控制項

[CStatic](../mfc/reference/cstatic-class.md)<br/>
靜態顯示視窗。 靜態控制項用來加上標籤、 方塊中，或不同的對話方塊或視窗中的其他控制項。 它們可能也會顯示圖形影像而不是文字或方塊。

## <a name="text-controls"></a>文字控制項

[CEdit](../mfc/reference/cedit-class.md)<br/>
可編輯文字控制項 視窗中。 編輯控制項用來接受使用者輸入文字。

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
支援的編輯方塊操作的網際網路通訊協定 (IP) 位址。

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
使用者可以輸入和編輯文字控制項。 不同於封裝在控制`CEdit`，rich edit 控制項支援的字元和段落格式以及 OLE 物件。

## <a name="controls-that-represent-numbers"></a>表示數字的控制項

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
包含使用者移到選取的值或一組值的滑桿控制項。

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
一對箭號按鈕的使用者可以按一下來遞增或遞減值。

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
會顯示矩形逐漸填滿從左到右來表示作業的進度。

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
捲軸控制項視窗。 類別提供的捲軸，作為對話方塊或視窗中，使用者可以用來指定範圍內的位置中的控制項的功能。

## <a name="buttons"></a>按鈕

[CButton](../mfc/reference/cbutton-class.md)<br/>
按鈕控制項視窗。 類別會提供程式設計介面，如按鈕、 核取方塊或在對話方塊或視窗中的選項按鈕。

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
具有點陣圖，而不是文字標題的按鈕。

## <a name="lists"></a>清單

[CListBox](../mfc/reference/clistbox-class.md)<br/>
清單方塊控制 視窗中。 清單方塊會顯示使用者可以檢視和選取的項目清單。

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
提供 Windows 清單方塊的功能;可讓使用者在清單方塊內移動清單方塊項目，例如檔案名稱和字串常值。 使用這項功能的清單方塊適用於項目清單而非依字母順序排列的順序，例如包含專案中的 路徑名稱或檔案。

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
下拉式方塊控制項視窗。 下拉式方塊包含編輯控制項，再加上一個清單方塊。

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
藉由提供影像清單的支援，擴充下拉式方塊控制項。

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
顯示使用者可以檢查或清除，每個項目旁的核取方塊的項目清單。

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
顯示項目的集合，每個圖示和標籤，以類似方式右窗格的 [檔案總管] 中所組成。

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
顯示圖示和標籤排列在類似的左窗格的 [檔案總管] 中的階層式清單。

## <a name="toolbars-and-status-bars"></a>工具列和狀態列

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具列通用控制項的功能。 大部分的 MFC 程式使用[CToolBar](../mfc/reference/ctoolbar-class.md)而不是此類別。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平的視窗中，通常會分成的窗格中，應用程式可以在其中顯示狀態資訊。 大部分的 MFC 程式使用[CStatusBar](../mfc/reference/cstatusbar-class.md)而不是此類別。

## <a name="miscellaneous-controls"></a>其他的控制項

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
顯示簡單的視訊剪輯。

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
小型快顯視窗會顯示一行文字，描述應用程式中工具用途。

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
支援擴充的編輯控制項或可讓使用者選擇特定日期或時間值的簡單的行事曆介面控制項。

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
顯示標題或資料行的標籤。

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
支援簡單的行事曆介面控制項，可讓使用者選取日期。

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
具有索引標籤的使用者可以按一下，類似於筆記本的插頁的控制項。

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
可讓使用者建立的作用的按鍵組合，其中使用者可以按下以快速執行的動作。

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
呈現標記文字，並啟動適當的應用程式，當使用者按一下內嵌的連結。

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。

## <a name="related-classes"></a>相關的類別

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
提供 Windows 影像清單的功能。 影像清單是搭配清單控制項和樹狀目錄控制項使用。 也可以用來儲存和封存一組大小相同的點陣圖。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows 控制項相關聯的所有檢視的基底類別。 根據控制項的檢視如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 標準的檢視編輯控制項。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
檢視包含豐富的 Windows 編輯控制項。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 清單控制項的檢視。

[Ctreeview 比較](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的檢視。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

