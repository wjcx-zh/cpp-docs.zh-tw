---
title: "檢視類別 (架構) | Microsoft Docs"
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
  - "vc.classes.view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項檢視"
  - "表單和資料錄檢視"
  - "檢視類別"
  - "檢視類別, 架構"
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檢視類別 (架構)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CView` 及其衍生類別是表示框架視窗的工作區的子視窗。  檢視顯示資料並接受資料的項目。  
  
 使用文件樣板物件，檢視類別與文件類別和框架視窗類別。  
  
 [CView](../mfc/reference/cview-class.md)  
 文件資料的應用程式特定的檢視的基底類別。  檢視顯示資料並接受編輯或選取資料的使用者輸入。  從 `CView`衍生您自己的檢視類別。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 檢視的基底類別以捲動功能。  從自動捲動的 `CScrollView` 衍生您自己的檢視類別。  
  
## 表單和資料錄檢視  
 表單檢視也捲動檢視。  它們會根據對話方塊範本。  
  
 資料錄檢視從表單檢視衍生。  除了對話方塊範本以外，也有與資料庫的連接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 設定對話方塊範本中定義的捲動檢視。  衍生自 `CFormView` 類別實作以對話方塊範本的使用者介面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供一個表單檢視直接連接到資料存取物件 \(DAO\) 資料錄集物件。  就像所有表單檢視 `CDaoRecordView` ，根據對話方塊範本。  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 支援瀏覽在應用程式中的控制項。  控制項支援的 MFC 動態 HTML。  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 為表單檢視提供 MFC OLE DB 支援。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供一個表單檢視直接連接至開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料錄集物件。  就像所有表單檢視 `CRecordView` ，根據對話方塊範本。  
  
## 控制項檢視  
 控制項檢視中顯示控制項做為其檢視。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 所有檢視的基底類別與視窗控制項。  根據控制項的檢視說明如下。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準編輯控制項的檢視 \(請參閱 [CEdit](../mfc/reference/cedit-class.md)\)。  編輯控制項支援文字編輯，搜尋，取代和捲動功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 包含 Windows Rich Edit 控制項的檢視 \(請參閱 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)。  除了編輯控制項的功能， Rich Edit 控制項支援字型、色彩、段落格式和內嵌 OLE 物件。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視 \(請參閱 [CListCtrl](../mfc/reference/clistctrl-class.md)\)。  清單控制項中顯示圖示和字串方式與檔案總管的右窗格中。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含視窗樹狀檢視控制項 \(請參閱 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)。  樹狀目錄控制項階層架構和字串排列顯示圖示方式與檔案總管左窗格中。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)