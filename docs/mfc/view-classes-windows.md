---
title: 檢視類別 (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: ad58fd6fa2548c2cf320baf75b8fc33a835ddd55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267091"
---
# <a name="view-classes-windows"></a>檢視類別 (Windows)

`CView` 和其衍生的類別所代表的框架視窗工作區的子視窗。 檢視會顯示資料，並接受文件的輸入。

檢視類別是與文件類別和使用文件範本物件的框架視窗類別相關聯。

[CView](../mfc/reference/cview-class.md)<br/>
應用程式專屬資料的檢視文件的基底類別。 檢視會顯示資料，並接受使用者輸入以編輯，或選取的資料。 衍生您的檢視類別或類別從`CView`。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
檢視具有捲動功能的基底類別。 衍生檢視類別從`CScrollView`自動捲動。

## <a name="form-and-record-views"></a>表單和資料錄檢視

表單檢視也捲動檢視。 它們根據對話方塊範本。

資料錄檢視被衍生自表單檢視中。 除了對話方塊範本，他們也擁有資料庫的連接。

[CFormView](../mfc/reference/cformview-class.md)<br/>
捲軸檢視，在對話方塊範本中定義的配置。 自`CFormView`實作根據對話方塊範本的使用者介面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供表單直接連接到資料存取物件 (DAO) 資料錄集物件的檢視。 像所有的表單檢視中，`CDaoRecordView`根據對話方塊範本。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供表單直接連接到開放式資料庫連接 (ODBC) 資料錄集物件的檢視。 像所有的表單檢視中，`CRecordView`根據對話方塊範本。

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
提供 HTML WebBrowser 編輯平台的功能 [表單] 檢視中。

## <a name="control-views"></a>控制項檢視

控制項檢視中顯示為其檢視控制項。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows 控制項相關聯的所有檢視的基底類別。 根據控制項的檢視如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 標準的檢視編輯控制項 (請參閱[CEdit](../mfc/reference/cedit-class.md))。 編輯控制項支援文字編輯、 搜尋、 取代和捲動功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
檢視，其中包含 Windows rich edit 控制項 (請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 編輯控制項的功能，除了豐富編輯控制項支援字型、 色彩、 段落格式，和內嵌的 OLE 物件。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 清單控制項的檢視 (請參閱[CListCtrl](../mfc/reference/clistctrl-class.md))。 清單控制項中顯示項目的集合，每個組成的圖示和標籤，以類似方式右窗格的 [檔案總管] 中。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的檢視 (請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 樹狀目錄控制項顯示圖示和標籤排列在類似的左窗格的 [檔案總管] 中的階層式清單。

## <a name="related-classes"></a>相關的類別

`CSplitterWnd` 可讓您有多個檢視單一框架視窗內。 `CPrintDialog` 和`CPrintInfo`支援的檢視表的列印和預覽列印功能。 `CRichEditDoc` 並`CRichEditCntrItem`搭配使用`CRichEditView`來實作 OLE 容器功能。

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
使用者可以將分割成多個窗格視窗。 這些窗格可以由使用者或固定的大小的可調整大小。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供標準對話方塊，來列印檔案。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
結構，包含列印或預覽列印工作的相關資訊。 使用`CView`架構中的列印。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
維護中的 OLE 用戶端項目清單`CRichEditView`。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
提供 OLE 項目儲存在用戶端存取`CRichEditView`。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
