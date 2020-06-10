---
title: 控制項類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
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
ms.openlocfilehash: 277802bff3e4833396c4bf114ff8880fcd26343d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623006"
---
# <a name="control-classes"></a>控制項類別

控制項類別封裝了各種不同的標準 Windows 控制項，範圍從靜態文字控制項到樹狀目錄控制項。 此外，MFC 還提供一些新的控制項，包括具有點陣圖和控制列的按鈕。

其類別名稱結尾為 "**Ctrl**" 的控制項在 windows 95 和 windows NT 3.51 版中是新的。

## <a name="static-display-controls"></a>靜態顯示控制項

[CStatic](reference/cstatic-class.md)<br/>
靜態顯示視窗。 靜態控制項是用來標記、方塊或分隔對話方塊或視窗中的其他控制項。 它們也可以顯示圖形影像，而不是文字或方塊。

## <a name="text-controls"></a>文字控制項

[CEdit](reference/cedit-class.md)<br/>
可編輯的文字控制項視窗。 編輯控制項是用來接受使用者的文字輸入。

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
支援用於操作網際網路通訊協定（IP）位址的編輯方塊。

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
使用者可以在其中輸入和編輯文字的控制項。 不同于封裝在中的控制項 `CEdit` ，rich edit 控制項支援字元和段落格式設定和 OLE 物件。

## <a name="controls-that-represent-numbers"></a>代表數位的控制項

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
包含滑杆的控制項，使用者可以用來選取值或一組值。

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
一對箭號按鈕，使用者可以按一下以遞增或遞減值。

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
顯示從左至右逐漸填滿的矩形，以指示作業的進度。

[CScrollBar](reference/cscrollbar-class.md)<br/>
捲軸控制項視窗。 類別會提供捲軸的功能，以做為對話方塊或視窗中的控制項，供使用者在範圍內指定位置。

## <a name="buttons"></a>按鈕

[CButton](reference/cbutton-class.md)<br/>
按鈕控制項視窗。 類別會針對對話方塊或視窗中的 [推播] 按鈕、核取方塊或選項按鈕提供程式設計介面。

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
具有點陣圖而不是文字標題的按鈕。

## <a name="lists"></a>清單

[CListBox](reference/clistbox-class.md)<br/>
清單方塊控制項視窗。 清單方塊會顯示使用者可查看和選取的專案清單。

[CDragListBox](reference/cdraglistbox-class.md)<br/>
提供 Windows 清單方塊的功能;允許使用者在清單方塊中移動清單方塊專案，例如檔案名和字串常值。 具有此功能的清單方塊適用于依字母順序排列的專案清單，例如在專案中包含路徑路徑或檔案。

[CComboBox](reference/ccombobox-class.md)<br/>
下拉式方塊控制項視窗。 下拉式方塊是由編輯控制項加上清單方塊所組成。

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
藉由提供影像清單的支援，擴充下拉式方塊控制項。

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
顯示具有核取方塊的專案清單，使用者可以在每個專案旁邊進行檢查或清除。

[CListCtrl](reference/clistctrl-class.md)<br/>
顯示專案的集合，其中每一個都包含一個圖示和一個標籤，其方式類似于 [檔案瀏覽器] 的右窗格。

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
顯示圖示和標籤的階層式清單，其相片順序類似于 [檔案瀏覽器] 的左窗格。

## <a name="toolbars-and-status-bars"></a>工具列和狀態列

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具列通用控制項的功能。 大部分的 MFC 程式會使用[CToolBar](reference/ctoolbar-class.md) ，而不是這個類別。

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
水準視窗（通常分成窗格），應用程式可以在其中顯示狀態資訊。 大部分的 MFC 程式會使用[CStatusBar](reference/cstatusbar-class.md) ，而不是這個類別。

## <a name="miscellaneous-controls"></a>其他控制項

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
顯示簡單的影片剪輯。

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
一個小型快顯視窗，會在應用程式中顯示一個描述工具用途的單行文字。

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
支援可讓使用者選擇特定日期或時間值的擴充編輯控制項或簡單行事曆介面控制項。

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
顯示資料行的標題或標籤。

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
支援簡單行事曆介面控制項，可讓使用者選取日期。

[CTabCtrl](reference/ctabctrl-class.md)<br/>
控制項，其中包含使用者可以按一下的索引標籤，類似于筆記本中的分隔線。

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
可讓使用者建立快速鍵組合，使用者可以按下以快速執行動作。

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
呈現已標記的文字，並在使用者按一下內嵌連結時啟動適當的應用程式。

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。

## <a name="related-classes"></a>相關類別

[CImageList](reference/cimagelist-class.md)<br/>
提供 Windows 影像清單的功能。 影像清單是搭配清單控制項和樹狀目錄控制項使用。 也可以用來儲存和封存一組大小相同的點陣圖。

[CCtrlView](reference/cctrlview-class.md)<br/>
所有與 Windows 控制項相關聯之視圖的基類。 以控制項為基礎的視圖如下所述。

[CEditView](reference/ceditview-class.md)<br/>
包含 Windows standard 編輯控制項的視圖。

[CRichEditView](reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控制項的視圖。

[CListView](reference/clistview-class.md)<br/>
包含 Windows 清單控制項的視圖。

[CTreeView](reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的視圖。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
