---
title: "對話方塊控制項和變數類型 | Microsoft Docs"
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
  - "對話方塊控制項, 成員變數"
  - "對話方塊控制項, 變數類型"
  - "變數, 對話方塊控制成員變數"
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 對話方塊控制項和變數類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用[加入成員變數精靈](../ide/add-member-variable-wizard.md)，在使用 MFC 建立的對話方塊控制項中加入成員變數。  您所加入成員變數的控制項型別決定了在對話方塊中出現的選項。  
  
 下表說明 MFC 和[對話方塊編輯器](../mfc/dialog-editor.md)中支援的所有對話方塊控制項，及其可用的型別和值。  
  
|控制項|控制項型別|控制項變數型別|數值變數型別|最小\/最大值 \(僅限實值型別\)|  
|---------|-----------|-------------|------------|------------------------|  
|動畫控制項|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|無；僅限控制項|N\/A|  
|Button|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|無；僅限控制項|N\/A|  
|Check box|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值\/最大值|  
|Combo box|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字元數|  
|日期時間選擇器控制項|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值\/最大值|  
|Edit box|EDIT|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 **COleCurrency**|最小值\/最大值；某些支援最大字元數|  
|熱鍵控制項|msctls\_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|無；僅限控制項|N\/A|  
|List box|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字元數|  
|List 控制項|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|無；僅限控制項|N\/A|  
|月曆控制項|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值\/最大值|  
|進度控制項|msctls\_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|無；僅限控制項|N\/A|  
|Rich Edit 2 控制項|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字元數|  
|Rich Edit 控制項|RICHEDIT|`CRichEditCtrl`|`CString`|最大字元數|  
|捲軸 \(垂直或水平\)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值\/最大值|  
|滑桿控制項 \(Slider Control\)|msctls\_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值\/最大值|  
|微調控制項|msctls\_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|無；僅限控制項|N\/A|  
|索引標籤控制項|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|無；僅限控制項|N\/A|  
|樹狀目錄控制項|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|無；僅限控制項|N\/A|  
  
## 請參閱  
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)