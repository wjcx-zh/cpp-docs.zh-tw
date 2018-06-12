---
title: 對話方塊控制項和變數類型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2fbae37072f50898181334a9059a7dc9c6a83a9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33335061"
---
# <a name="dialog-box-controls-and-variable-types"></a>對話方塊控制項和變數類型
您可以使用 [[新增成員變數精靈]](../ide/add-member-variable-wizard.md)，將成員變數新增至使用 MFC 所建立的對話方塊控制項。 您新增成員變數的控制項類型會決定出現在對話方塊中的選項。  
  
 下表描述 MFC 支援的所有對話方塊方塊控制項類型，以及[對話方塊編輯器](../windows/dialog-editor.md)及其可用的類型和值。  
  
|控制項|控制項類型|控制變數類型|變數值類型|最小/最大值 (僅限實值型別)|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|動畫控制項|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|無；僅限控制項|N/A|  
|按鈕|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|無；僅限控制項|N/A|  
|核取方塊|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值/最大值|  
|下拉式方塊|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字元數|  
|日期時間選擇器控制項|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|  
|編輯方塊|編輯|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 **COleCurrency**|最小值/最大值；某些支援最大字元數|  
|熱鍵控制項|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|無；僅限控制項|N/A|  
|清單方塊|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字元數|  
|清單控制項|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|無；僅限控制項|N/A|  
|月曆控制項|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|  
|進度控制項|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|無；僅限控制項|N/A|  
|Rich Edit 2 控制項|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字元數|  
|Rich Edit 控制項|RICHEDIT|`CRichEditCtrl`|`CString`|最大字元數|  
|捲軸 (垂直或水平)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值/最大值|  
|Slider 控制項|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值/最大值|  
|微調控制項|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|無；僅限控制項|N/A|  
|索引標籤控制項|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|無；僅限控制項|N/A|  
|樹狀控制項|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|無；僅限控制項|N/A|  
  
## <a name="see-also"></a>請參閱  
 [新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)