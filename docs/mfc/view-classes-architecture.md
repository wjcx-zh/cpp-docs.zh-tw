---
title: "檢視類別 （架構） |Microsoft 文件"
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
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 184245411f44a9aa9a6747adda0aafa5a8f68010
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="view-classes-architecture"></a>檢視類別 (架構)
`CView`其衍生的類別是代表框架視窗的工作區的子視窗。 檢視可顯示資料，並接受輸入的文件。  
  
 檢視類別是與文件類別和使用文件範本物件的框架視窗類別相關聯。  
  
 [CView](../mfc/reference/cview-class.md)  
 應用程式特定資料檢視的文件的基底類別。 檢視會顯示資料，並可接受使用者輸入來編輯，或選取的資料。 衍生您的檢視類別從`CView`。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 檢視具有捲動功能的基底類別。 衍生檢視類別從`CScrollView`自動捲動。  
  
## <a name="form-and-record-views"></a>表單和資料錄檢視  
 表單檢視也會捲動檢視。 它們所根據的對話方塊範本。  
  
 資料錄檢視被衍生自表單檢視中。 除了對話方塊範本，他們也擁有資料庫的連接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 捲動檢視，在對話方塊範本中定義的配置。 自`CFormView`實作根據對話方塊範本的使用者介面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供表單直接連接到資料存取物件 (DAO) 資料錄集物件的檢視。 像所有的表單檢視`CDaoRecordView`根據對話方塊範本。  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 瀏覽 Web 應用程式中支援的控制項。 此控制項支援在 MFC 中的動態 HTML。  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 提供 MFC OLE DB 支援表單檢視。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供表單直接連接至開放式資料庫連接 (ODBC) 資料錄集物件的檢視。 像所有的表單檢視`CRecordView`根據對話方塊範本。  
  
## <a name="control-views"></a>控制項檢視  
 控制項檢視中顯示為其檢視控制項。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Windows 控制項相關聯的所有檢視的基底類別。 以下將詳述控制項為基礎的檢視。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含 Windows 標準的檢視編輯控制項 (請參閱[CEdit](../mfc/reference/cedit-class.md))。 編輯控制項支援文字編輯、 搜尋、 取代和捲動功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 檢視包含豐富的 Windows 編輯控制項 (請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 編輯控制項的功能，除了豐富編輯控制項支援字型、 色彩、 段落格式和內嵌的 OLE 物件。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 清單控制項的檢視 (請參閱[CListCtrl](../mfc/reference/clistctrl-class.md))。 清單控制項顯示圖示和字串的方式類似於右窗格的 [檔案總管] 中。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 包含 Windows 樹狀目錄控制項的檢視 (請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 樹狀目錄控制項顯示圖示和排列方式，類似於左窗格的 [檔案總管] 中的階層中的字串。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

