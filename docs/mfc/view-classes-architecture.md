---
title: 檢視類別 (架構)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: fda4e968a4761fcf1e2245964bd5dca3f41a82ad
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302977"
---
# <a name="view-classes-architecture"></a>檢視類別 (架構)

`CView` 及其衍生類別都是子視窗，代表框架視窗的工作區。 Views 顯示資料並接受檔的輸入。

View 類別是與檔類別和框架視窗類別相關聯，並使用檔範本物件。

[CView](../mfc/reference/cview-class.md)<br/>
檔資料之應用程式特定視圖的基類。 Views 會顯示資料並接受使用者輸入，以編輯或選取資料。 從 `CView`衍生您的 view 類別。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
具有滾動功能之視圖的基類。 從 `CScrollView` 衍生您的 view 類別，以進行自動滾動。

## <a name="form-and-record-views"></a>表單和記錄視圖

表單檢視也是捲軸視圖。 它們是以對話方塊範本為基礎。

記錄視圖是從表單檢視衍生而來。 除了對話方塊範本，它們也有資料庫的連接。

[CFormView](../mfc/reference/cformview-class.md)<br/>
一個捲軸，其版面配置定義于對話方塊範本中。 從 `CFormView` 衍生類別，以根據對話方塊範本來執行使用者介面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供直接連接到資料存取物件（DAO）記錄集物件的表單檢視。 就像所有表單檢視一樣，`CDaoRecordView` 是以對話方塊範本為基礎。 DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
支援在應用程式內進行網頁流覽的控制項。 控制項支援 MFC 中的動態 HTML。

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
提供表單檢視的 MFC OLE DB 支援。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供直接連接到開放式資料庫連接（ODBC）記錄集物件的表單檢視。 就像所有表單檢視一樣，`CRecordView` 是以對話方塊範本為基礎。

## <a name="control-views"></a>控制項視圖

控制項視圖會將控制項顯示為其視圖。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
所有與 Windows 控制項相關聯之視圖的基類。 以控制項為基礎的視圖如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows standard 編輯控制項的視圖（請參閱[CEdit](../mfc/reference/cedit-class.md)）。 編輯控制項支援文字編輯、搜尋、取代和滾動功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控制項的視圖（請參閱[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)）。 除了編輯控制項的功能之外，rich edit 控制項也支援字型、色彩、段落格式和內嵌的 OLE 物件。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 清單控制項的視圖（請參閱[CListCtrl](../mfc/reference/clistctrl-class.md)）。 清單控制項會以類似于 [檔案瀏覽器] 右窗格的方式來顯示圖示和字串。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 樹狀目錄控制項的視圖（請參閱[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）。 樹狀目錄控制項會以類似于 [檔案瀏覽器] 左窗格的方式，顯示在階層中排列的圖示和字串。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
