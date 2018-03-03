---
title: "對話方塊控制項和變數類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 744b9da2db456a72ed386806d8a4aa34c5942f69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-box-controls-and-variable-types"></a>對話方塊控制項和變數類型
您可以使用[加入成員變數精靈](../ide/add-member-variable-wizard.md)將成員變數新增至使用 MFC 所建立的對話方塊控制項。 加入成員變數的控制項類型決定出現在對話方塊中的選項。  
  
 下表描述在 MFC 中支援所有的對話方塊方塊控制項類型和[對話方塊編輯器](../windows/dialog-editor.md)，和其可用的類型和值。  
  
|控制項|控制項類型|控制變數的型別|值的變數類型|最小/最大值 （值類型）|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|動畫控制項|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|無。只有控制項|N/A|  
|按鈕|按鈕|[CButton](../mfc/reference/cbutton-class.md)|無。只有控制項|N/A|  
|核取方塊|核取|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值/最大值|  
|下拉式方塊|下拉式方塊|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字元數|  
|日期時間選擇器控制項|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|  
|編輯方塊|編輯|[CEdit](../mfc/reference/cedit-class.md)|`CString`、 int、 UINT、 long、 DWORD，float、 double、 BYTE、 short、 BOOL、 `COleDateTime`，或**COleCurrency**|最小值/最大值。部分支援的最大字元|  
|熱鍵控制項|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|無。只有控制項|N/A|  
|清單方塊|清單方塊|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字元數|  
|清單控制項|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|無。只有控制項|N/A|  
|月曆控制項|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|  
|進度控制項|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|無。只有控制項|N/A|  
|豐富的編輯 2 控制項|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字元數|  
|Rich Edit 控制項|RICHEDIT|`CRichEditCtrl`|`CString`|最大字元數|  
|（垂直或水平捲軸|捲軸|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值/最大值|  
|Slider 控制項|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值/最大值|  
|微調控制項|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|無。只有控制項|N/A|  
|索引標籤控制項|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|無。只有控制項|N/A|  
|樹狀控制項|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|無。只有控制項|N/A|  
  
## <a name="see-also"></a>請參閱  
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)