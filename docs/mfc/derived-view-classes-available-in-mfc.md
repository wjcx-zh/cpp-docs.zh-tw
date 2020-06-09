---
title: MFC 中的可用衍生檢視類別
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: dc0f0b10ea291db32c576a7d36b7fc19728fa6ce
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616975"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC 中的可用衍生檢視類別

下表顯示 MFC 的 view 類別及其關聯性。 View 類別的功能取決於它所衍生的目標 MFC view 類別。

### <a name="view-classes"></a>View 類別

|類別|描述|
|-----------|-----------------|
|[CView](reference/cview-class.md)|所有視圖的基類。|
|[CCtrlView](reference/cctrlview-class.md)|`CTreeView`、 `CListView` 、和的基類 `CEditView` `CRichEditView` 。 這些類別可讓您搭配指定的 Windows 通用控制項使用檔/視圖架構。|
|[CEditView](reference/ceditview-class.md)|以 Windows 編輯方塊控制項為基礎的簡單視圖。 允許輸入和編輯文字，而且可以當做簡單文字編輯器應用程式的基礎使用。 另請參閱 `CRichEditView`。|
|[CRichEditView](reference/cricheditview-class.md)|包含[CRichEditCtrl](reference/cricheditctrl-class.md)物件的視圖。 這個類別類似 `CEditView` ，但不同于，它會 `CEditView` `CRichEditView` 處理格式化的文字。|
|[CListView](reference/clistview-class.md)|包含[CListCtrl](reference/clistctrl-class.md)物件的視圖。|
|[CTreeView](reference/ctreeview-class.md)|包含[CTreeCtrl](reference/ctreectrl-class.md)物件的視圖，適用于 Visual C++ 中方案總管視窗的視圖。|
|[CScrollView](reference/cscrollview-class.md)|`CFormView`、和的基類 `CRecordView` `CDaoRecordView` 。 執行此視圖內容的滾動。|
|[CFormView](reference/cformview-class.md)|表單檢視，包含控制項的視圖。 以表單為基礎的應用程式會提供一或多個這類表單介面。|
|[CHtmlView](reference/chtmlview-class.md)|Web 瀏覽器視圖，應用程式的使用者可以在此流覽萬維網上的網站，以及本機檔案系統和網路上的資料夾。 Web 瀏覽器視圖也可以做為活動文檔容器。|
|[CRecordView](reference/crecordview-class.md)|表單檢視，會在控制項中顯示 ODBC 資料庫記錄。 如果您在專案中選取 [ODBC 支援]，則視圖的基類會是 `CRecordView` 。 此視圖會連接到 `CRowset` 物件。|
|[CDaoRecordView](reference/cdaorecordview-class.md)|表單檢視，會在控制項中顯示 DAO 資料庫記錄。 如果您在專案中選取 [DAO 支援]，則視圖的基類會是 `CDaoRecordView` 。 此視圖會連接到 `CDaoRecordset` 物件。|
|[COleDBRecordView](reference/coledbrecordview-class.md)|顯示控制項中 OLE DB 記錄的表單檢視。 如果您在專案中選取 OLE DB 支援，則此視圖的基類為 `COleDBRecordView` 。 此視圖會連接到 `CRowset` 物件。|

> [!NOTE]
> 從 MFC 版本4.0 開始， `CEditView` 衍生自 `CCtrlView` 。

若要在您的應用程式中使用這些類別，請從它們衍生應用程式的 view 類別。 如需相關資訊，請參閱[滾動和縮放視圖](scrolling-and-scaling-views.md)。 如需資料庫類別的詳細資訊，請參閱[總覽：資料庫程式設計](../data/data-access-programming-mfc-atl.md)。

## <a name="see-also"></a>另請參閱

[使用檢視](using-views.md)
