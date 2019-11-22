---
title: 檢視類別 (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: a3e0f837bc13c022bec91bfff6e38c1513abaf16
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302970"
---
# <a name="view-classes-windows"></a>檢視類別 (Windows)

`CView` 及其衍生類別都是子視窗，代表框架視窗的工作區。 Views 顯示資料並接受檔的輸入。

View 類別是與檔類別和框架視窗類別相關聯，並使用檔範本物件。

[CView](../mfc/reference/cview-class.md)<br/>
檔資料之應用程式特定視圖的基類。 Views 會顯示資料並接受使用者輸入，以編輯或選取資料。 從 `CView`衍生您的 view 類別或類別。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
具有滾動功能之視圖的基類。 從 `CScrollView` 衍生您的 view 類別，以進行自動滾動。

## <a name="form-and-record-views"></a>表單和記錄視圖

表單檢視也是捲軸視圖。 它們是以對話方塊範本為基礎。

記錄視圖是從表單檢視衍生而來。 除了對話方塊範本，它們也有資料庫的連接。

[CFormView](../mfc/reference/cformview-class.md)<br/>
一個捲軸，其版面配置定義于對話方塊範本中。 從 `CFormView` 衍生類別，以根據對話方塊範本來執行使用者介面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供直接連接到資料存取物件（DAO）記錄集物件的表單檢視。 就像所有表單檢視一樣，`CDaoRecordView` 是以對話方塊範本為基礎。 DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供直接連接到開放式資料庫連接（ODBC）記錄集物件的表單檢視。 就像所有表單檢視一樣，`CRecordView` 是以對話方塊範本為基礎。

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
提供 WebBrowser HTML 編輯平臺功能的表單檢視。

## <a name="control-views"></a>控制項視圖

控制項視圖會將控制項顯示為其視圖。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
所有與 Windows 控制項相關聯之視圖的基類。 以控制項為基礎的視圖如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows standard 編輯控制項的視圖（請參閱[CEdit](../mfc/reference/cedit-class.md)）。 編輯控制項支援文字編輯、搜尋、取代和滾動功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控制項的視圖（請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)）。 除了編輯控制項的功能之外，rich edit 控制項也支援字型、色彩、段落格式和內嵌的 OLE 物件。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 清單控制項的視圖（請參閱[CListCtrl](../mfc/reference/clistctrl-class.md)）。 清單控制項會顯示專案的集合，其中每一個都包含一個圖示和一個標籤，其方式類似于 [檔案瀏覽器] 的右窗格。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的視圖（請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）。 樹狀目錄控制項會顯示以類似于 [檔案瀏覽器] 左窗格的方式排列的圖示和標籤的階層式清單。

## <a name="related-classes"></a>相關類別

`CSplitterWnd` 可讓您在單一框架視窗內擁有多個視圖。 `CPrintDialog` 和 `CPrintInfo` 支援 views 的 [列印] 和 [預覽列印] 功能。 `CRichEditDoc` 和 `CRichEditCntrItem` 會與 `CRichEditView` 搭配使用，以執行 OLE 容器功能。

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
使用者可以分割成多個窗格的視窗。 這些窗格可以根據使用者或固定大小來進行調整。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供用來列印檔案的標準對話方塊。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
結構，包含列印或預覽列印工作的相關資訊。 由 `CView`的列印架構所使用。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
維護 `CRichEditView`中的 OLE 用戶端專案清單。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
提供 `CRichEditView`中儲存之 OLE 專案的用戶端存取。

## <a name="see-also"></a>請參閱

[類別總覽](../mfc/class-library-overview.md)
