---
title: 檢視類別 (架構)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 15b120f0354c483480351b8d3abf995334779411
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299409"
---
# <a name="view-classes-architecture"></a>檢視類別 (架構)

`CView` 和其衍生的類別所代表的框架視窗工作區的子視窗。 檢視會顯示資料，並接受文件的輸入。

檢視類別是與文件類別和使用文件範本物件的框架視窗類別相關聯。

[CView](../mfc/reference/cview-class.md)<br/>
應用程式專屬資料的檢視文件的基底類別。 檢視會顯示資料，並接受使用者輸入以編輯，或選取的資料。 衍生您的檢視類別從`CView`。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
檢視具有捲動功能的基底類別。 衍生檢視類別從`CScrollView`自動捲動。

## <a name="form-and-record-views"></a>表單和資料錄檢視

表單檢視也捲動檢視。 它們根據對話方塊範本。

資料錄檢視被衍生自表單檢視中。 除了對話方塊範本，他們也擁有資料庫的連接。

[CFormView](../mfc/reference/cformview-class.md)<br/>
捲軸檢視，在對話方塊範本中定義的配置。 自`CFormView`實作根據對話方塊範本的使用者介面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供表單直接連接到資料存取物件 (DAO) 資料錄集物件的檢視。 像所有的表單檢視中，`CDaoRecordView`根據對話方塊範本。

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
支援的網頁瀏覽應用程式內的控制項。 此控制項在 MFC 中支援動態 HTML。

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
提供 MFC OLE DB 支援表單檢視。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供表單直接連接到開放式資料庫連接 (ODBC) 資料錄集物件的檢視。 像所有的表單檢視中，`CRecordView`根據對話方塊範本。

## <a name="control-views"></a>控制項檢視

控制項檢視中顯示為其檢視控制項。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows 控制項相關聯的所有檢視的基底類別。 根據控制項的檢視如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 標準的檢視編輯控制項 (請參閱[CEdit](../mfc/reference/cedit-class.md))。 編輯控制項支援文字編輯、 搜尋、 取代和捲動功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
檢視，其中包含 Windows rich edit 控制項 (請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 編輯控制項的功能，除了豐富編輯控制項支援字型、 色彩、 段落格式，和內嵌的 OLE 物件。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 清單控制項的檢視 (請參閱[CListCtrl](../mfc/reference/clistctrl-class.md))。 清單控制項的方式類似於右窗格的 [檔案總管] 中顯示圖示和字串。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的檢視 (請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 樹狀目錄控制項顯示圖示和類似的左窗格的 [檔案總管] 中的階層排列的字串。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
