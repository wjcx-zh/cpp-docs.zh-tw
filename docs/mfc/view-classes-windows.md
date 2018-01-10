---
title: "檢視類別 (Windows) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.view
dev_langs: C++
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d737176df2676f543f47bb77a0d205fa7c908fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="view-classes-windows"></a>檢視類別 (Windows)
`CView`其衍生的類別是代表框架視窗的工作區的子視窗。 檢視可顯示資料，並接受輸入的文件。  
  
 檢視類別是與文件類別和使用文件範本物件的框架視窗類別相關聯。  
  
 [CView](../mfc/reference/cview-class.md)  
 應用程式特定資料檢視的文件的基底類別。 檢視會顯示資料，並可接受使用者輸入來編輯，或選取的資料。 衍生檢視類別或類別從`CView`。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 檢視具有捲動功能的基底類別。 衍生檢視類別從`CScrollView`自動捲動。  
  
## <a name="form-and-record-views"></a>表單和資料錄檢視  
 表單檢視也會捲動檢視。 它們所根據的對話方塊範本。  
  
 資料錄檢視被衍生自表單檢視中。 除了對話方塊範本，他們也擁有資料庫的連接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 捲動檢視，在對話方塊範本中定義的配置。 自`CFormView`實作根據對話方塊範本的使用者介面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供表單直接連接到資料存取物件 (DAO) 資料錄集物件的檢視。 像所有的表單檢視`CDaoRecordView`根據對話方塊範本。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供表單直接連接至開放式資料庫連接 (ODBC) 資料錄集物件的檢視。 像所有的表單檢視`CRecordView`根據對話方塊範本。  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 表單檢視，可提供 HTML WebBrowser 編輯平台的功能。  
  
## <a name="control-views"></a>控制項檢視  
 控制項檢視中顯示為其檢視控制項。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Windows 控制項相關聯的所有檢視的基底類別。 以下將詳述控制項為基礎的檢視。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準的檢視編輯控制項 (請參閱[CEdit](../mfc/reference/cedit-class.md))。 編輯控制項支援文字編輯、 搜尋、 取代和捲動功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 檢視包含豐富的 Windows 編輯控制項 (請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 編輯控制項的功能，除了豐富編輯控制項支援字型、 色彩、 段落格式和內嵌的 OLE 物件。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視 (請參閱[CListCtrl](../mfc/reference/clistctrl-class.md))。 清單控制項中顯示項目的集合，每個圖示和標籤，在檔案總管 的類似於右窗格的方式組成。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含 Windows 樹狀目錄控制項的檢視 (請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 樹狀目錄控制項顯示圖示和標籤排列方式，類似於左窗格的 [檔案總管] 中的階層式清單。  
  
## <a name="related-classes"></a>相關的類別  
 `CSplitterWnd`可讓您有多個檢視單一框架視窗內。 `CPrintDialog`和`CPrintInfo`支援列印和預覽列印功能的檢視。 `CRichEditDoc`和`CRichEditCntrItem`搭配`CRichEditView`實作 OLE 容器功能。  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 使用者可以分割成多個窗格視窗。 這些窗格可以由使用者或固定的大小可調整大小。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 列印檔案中提供的標準對話方塊。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含列印或預覽列印工作的相關資訊的結構。 使用`CView`列印架構。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 會維護中的 OLE 用戶端項目清單`CRichEditView`。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供 OLE 項目儲存在用戶端存取`CRichEditView`。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

