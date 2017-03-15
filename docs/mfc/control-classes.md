---
title: "控制項類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按鈕, MFC 控制項類別"
  - "控制項類別"
  - "控制項類別, MFC"
  - "控制項 [C++], MFC 控制項類別"
  - "控制項 [MFC]"
  - "清單方塊, MFC 控制項類別"
  - "靜態顯示控制項"
  - "文字, 輸入的控制項"
  - "使用者輸入, MFC 控制項類別"
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 控制項類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制類別封裝範圍從靜態文字控制項的各種標準 Windows 控制項加入至樹狀目錄控制項。  此外， MFC 提供一些新的控制項，包括按鈕以點陣圖控制列。  
  
 類別名稱會以「**Ctrl**」結尾的控制項功能、Windows 95 和 Windows NT 3.51 版。  
  
## 靜態顯示控制項。  
 [CStatic](../mfc/reference/cstatic-class.md)  
 靜態顯示視窗。  靜態控制項是用來標記，把或分隔在對話方塊或視窗中的其他控制項容器。  他們也可能會顯示圖形影像而非文字或方塊。  
  
## 文字控制項  
 [CEdit](../mfc/reference/cedit-class.md)  
 可編輯的文字控制項的視窗。  編輯控制項用來接受使用者輸入的文字。  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 支援操作的網際網路通訊協定 \(IP\) 位址 \(IP\) 一個編輯方塊。  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 使用者可以輸入和編輯文字的控制項。  不同於 `CEdit`封裝的控制項， Rich Edit 控制項支援字元和段落格式和 OLE 物件。  
  
## 表示數字的控制項  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 包含滑桿控制項，使用者將選取值或值集合。  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 一對箭號按鈕使用者可以按一下加入或減去的值。  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 顯示由左至右逐漸填滿表示作業進度的矩形。  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 捲動列控制項的視窗。  類別提供捲軸的功能，以做為對話方塊或視窗中的控制項，使用者可以指定範圍內的位置。  
  
## 按鈕  
 [CButton](../mfc/reference/cbutton-class.md)  
 按鈕控制項視窗。  類別為按鈕、核取方塊或選項按鈕提供程式設計介面在對話方塊或視窗。  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 取得點陣圖的按鈕而非文字標題。  
  
## 清單  
 [CListBox](../mfc/reference/clistbox-class.md)  
 清單方塊控制項的視窗。  清單方塊會顯示使用者可以檢視和選取項目的清單。  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 提供視窗清單方塊的功能;允許使用者捲動清單方塊項目，例如檔案名稱和字串常值，清單方塊內。  清單方塊以這項功能對於項目清單是有用的順序除了按字母順序之外，例如 Include 路徑名稱或專案中的檔案。  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 下拉式方塊控制項的視窗。  下拉式方塊包含編輯控制項加上清單方塊。  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 藉由提供影像清單的支援，擴充下拉式方塊控制項。  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 在每個項目旁顯示核取方塊的項目清單，使用者可以選取或清除。  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 顯示項目集合，包括圖示和標籤的每個，方式與檔案總管的右窗格中。  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 顯示的階層式清單圖示與標籤排列的方式類似於檔案總管左窗格中。  
  
## 工具列和狀態列  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具列通用控制項的功能。  大部分的 MFC 程式使用 [CToolBar](../mfc/reference/ctoolbar-class.md) 而不是這個類別。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平視窗，通常分為窗格，應用程式可能顯示狀態資訊。  大部分的 MFC 程式使用 [CStatusBar](../mfc/reference/cstatusbar-class.md) 而不是這個類別。  
  
## 其他控制項  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 顯示簡單的目錄剪輯。  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 顯示說明工具的目的單行文字在應用程式的小型快顯視窗。  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 支援的擴充編輯控制項或簡單的日曆介面控制項，讓使用者選取特定日期或時間值。  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 顯示標題或標籤資料列的。  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 支援可讓使用者選取日期的行事曆控制項介面。  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 與使用者可以按一下索引標籤的控制項，類似於筆記本的分割線。  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 可讓使用者建立快速鍵組合，使用者可以按快速執行動作。  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 renders 明顯的文字和啟動適當的應用程式，當使用者按一下內嵌連結。  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。  
  
## 相關類別  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 提供 Windows 影像清單的功能。  影像清單使用與清單控制項和樹狀目錄控制項。  也可以用來儲存和保存一組相同的點陣圖。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 所有檢視的基底類別與視窗控制項。  根據控制項的檢視說明如下。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準編輯控制項的檢視。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 包含 Windows Rich Edit 控制項的檢視。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含視窗樹狀目錄控制項的檢視。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)