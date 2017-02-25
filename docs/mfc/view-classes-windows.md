---
title: "檢視類別 (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "表單和資料錄檢視"
  - "分隔視窗類別"
  - "檢視類別, Windows"
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 檢視類別 (Windows)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CView` 及其衍生類別是表示框架視窗的工作區的子視窗。  檢視顯示資料並接受資料的項目。  
  
 使用文件樣板物件，檢視類別與文件類別和框架視窗類別。  
  
 [CView](../mfc/reference/cview-class.md)  
 文件資料的應用程式特定的檢視的基底類別。  檢視顯示資料並接受編輯或選取資料的使用者輸入。  從 `CView`衍生您自己的檢視類別或類別。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 檢視的基底類別以捲動功能。  從自動捲動的 `CScrollView` 衍生您自己的檢視類別。  
  
## 表單和資料錄檢視  
 表單檢視也捲動檢視。  它們會根據對話方塊範本。  
  
 資料錄檢視從表單檢視衍生。  除了對話方塊範本以外，也有與資料庫的連接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 設定對話方塊範本中定義的捲動檢視。  衍生自 `CFormView` 類別實作以對話方塊範本的使用者介面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供一個表單檢視直接連接到資料存取物件 \(DAO\) 資料錄集物件。  就像所有表單檢視 `CDaoRecordView` ，根據對話方塊範本。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供一個表單檢視直接連接至開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料錄集物件。  就像所有表單檢視 `CRecordView` ，根據對話方塊範本。  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 提供編輯平台的瀏覽器功能的 HTML 表單檢視。  
  
## 控制項檢視  
 控制項檢視中顯示控制項做為其檢視。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 所有檢視的基底類別與視窗控制項。  根據控制項的檢視說明如下。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準編輯控制項的檢視 \(請參閱 [CEdit](../mfc/reference/cedit-class.md)\)。  編輯控制項支援文字編輯，搜尋，取代和捲動功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 包含 Windows Rich Edit 控制項的檢視 \(請參閱 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)。  除了編輯控制項的功能，雜項編輯控制項支援字型、色彩、段落格式和內嵌 OLE 物件。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視 \(請參閱 [CListCtrl](../mfc/reference/clistctrl-class.md)\)。  清單控制項顯示項目的集合，每項包括圖示和標籤，如檔案總管的右窗格中的方式。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含視窗樹狀控制項的檢視 \(請參閱 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)。  樹狀目錄控制項顯示階層式清單圖示與標籤排列的方式，類似於檔案總管左窗格中。  
  
## 相關類別  
 `CSplitterWnd` 可讓您在單一框架視窗內有多個檢視。  `CPrintDialog` 和 `CPrintInfo` 支援檢視的列印和預覽列印功能。  `CRichEditDoc` 和 `CRichEditCntrItem` 以 `CRichEditView` 實作 OLE 容器功能。  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 使用者可以分割成多個窗格的視窗。  這些窗格可以由使用者調整大小或固定大小。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 提供列印檔案的標準對話方塊。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含列印或預覽列印工作的結構資訊。  用於列印結構的 `CView` 。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 維持 `CRichEditView` 中 OLE 客戶端項目清單。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供用戶端中 `CRichEditView`儲存的 OLE 項目。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)