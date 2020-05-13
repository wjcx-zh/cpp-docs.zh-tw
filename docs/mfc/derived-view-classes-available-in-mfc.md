---
title: MFC 中的可用衍生檢視類別
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373495"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC 中的可用衍生檢視類別

下表顯示了 MFC 的視圖類及其彼此之間的關係。 視圖類的功能取決於它派生自的 MFC 視圖類。

### <a name="view-classes"></a>檢視類

|類別|描述|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|所有視圖的基類。|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|的基類`CTreeView``CListView`,`CEditView``CRichEditView`與 。 這些類允許您使用文檔/檢視體系結構與指示的 Windows 公共控件。|
|[CEditView](../mfc/reference/ceditview-class.md)|基於 Windows 編輯框控制件的簡單檢視。 允許輸入和編輯文本,並可用作簡單文字編輯器應用程式的基礎。 另請參閱 `CRichEditView`。|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|包含[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)物件的檢視。 類類似於`CEditView`,但與`CEditView``CRichEditView`不同 , 處理格式化的文本。|
|[CListView](../mfc/reference/clistview-class.md)|包含[CListCtrl](../mfc/reference/clistctrl-class.md)物件的檢視。|
|[CTreeView](../mfc/reference/ctreeview-class.md)|包含[CTreeCtrl](../mfc/reference/ctreectrl-class.md)物件的檢視,用於類似於可視化 C++中的解決方案資源管理器視窗的檢視。|
|[CScrollView](../mfc/reference/cscrollview-class.md)|的基類`CFormView``CRecordView`,`CDaoRecordView`與 。 實現滾動視圖的內容。|
|[CFormView](../mfc/reference/cformview-class.md)|窗體視圖,包含控件的視圖。 基於表單的應用程式提供一個或多個此類表單介面。|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|應用程式用戶可以使用的 Web 瀏覽器檢視瀏覽萬維網上的網站以及本地檔案系統和網路上的資料夾。 Web 瀏覽器檢視也可以用作活動文檔容器。|
|[CRecordView](../mfc/reference/crecordview-class.md)|在控制項中顯示 ODBC 資料庫記錄的表單影像檢視。 如果在項目中選擇 ODBC 支援,則檢視的基數`CRecordView`為 。 檢視連線到物件`CRowset`。|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|在控制項中顯示 DAO 資料庫記錄的表單單。 如果在項目中選擇 DAO 支援,則檢視的基數`CDaoRecordView`為 。 檢視連線到物件`CDaoRecordset`。|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|在控制項中顯示 OLE DB 記錄的表單單表。 如果在項目中選擇 OLE DB 支援,則檢視的基`COleDBRecordView`數為 。 檢視連線到物件`CRowset`。|

> [!NOTE]
> 自 MFC 版本`CEditView`4.0 起`CCtrlView`,派生自 。

要在應用程式中使用這些類,請從這些類派生應用程式的視圖類。 有關詳細資訊,請參閱[捲動和縮放檢視](../mfc/scrolling-and-scaling-views.md)。 有關資料庫類的詳細資訊,請參閱[概述:資料庫程式設計](../data/data-access-programming-mfc-atl.md)。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
