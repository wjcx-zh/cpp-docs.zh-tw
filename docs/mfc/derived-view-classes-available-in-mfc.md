---
title: MFC 中的可用衍生檢視類別
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 9972586bd0cc4059e81d81be954a8cf0cada1f0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594489"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC 中的可用衍生檢視類別

下表顯示 MFC 檢視類別和其之間的關聯性。 您的檢視類別的功能取決於從它衍生的 MFC 檢視類別。

### <a name="view-classes"></a>檢視類別

|類別|描述|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|所有檢視的基底類別。|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|基底類別`CTreeView`， `CListView`， `CEditView`，和`CRichEditView`。 這些類別可讓您使用與指定的 Windows 通用控制項的文件/檢視架構。|
|[CEditView](../mfc/reference/ceditview-class.md)|Windows 為基礎的簡單檢視編輯方塊控制項。 允許輸入和編輯文字，並可以用於做為基礎的簡單文字編輯器應用程式。 請參閱 `CRichEditView`。|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|檢視包含[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)物件。 這個類別是類似`CEditView`，但不同於`CEditView`，`CRichEditView`控點格式化的文字。|
|[CListView](../mfc/reference/clistview-class.md)|檢視包含[CListCtrl](../mfc/reference/clistctrl-class.md)物件。|
|[Ctreeview 比較](../mfc/reference/ctreeview-class.md)|檢視包含[CTreeCtrl](../mfc/reference/ctreectrl-class.md)物件，類似於在 Visual c + + 中的 [方案總管] 視窗的檢視。|
|[CScrollView](../mfc/reference/cscrollview-class.md)|基底類別`CFormView`， `CRecordView`，和`CDaoRecordView`。 實作捲動檢視的內容。|
|[CFormView](../mfc/reference/cformview-class.md)|表單檢視中，包含控制項的檢視。 表單架構應用程式提供一或多個這類表單介面。|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|與應用程式的使用者可以瀏覽網站上全球資訊網上，以及資料夾中的本機檔案系統與網路上的網頁瀏覽器檢視。 Web 瀏覽器檢視也可為使用中的文件容器。|
|[CRecordView](../mfc/reference/crecordview-class.md)|表單檢視顯示在控制項中的 ODBC 資料庫記錄。 如果您選取您的專案中的 ODBC 支援，該檢視的基底類別是`CRecordView`。 檢視已連線到`CRowset`物件。|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|表單檢視顯示在控制項中的 DAO 資料庫記錄。 如果您選取 DAO 支援在您的專案時，該檢視的基底類別是`CDaoRecordView`。 檢視已連線到`CDaoRecordset`物件。|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|控制項中顯示 OLE DB 資料錄 [表單] 檢視中。 如果您選取 OLE DB 支援在您的專案時，該檢視的基底類別是`COleDBRecordView`。 檢視已連線到`CRowset`物件。|

> [!NOTE]
>  根據 MFC 4.0 版，`CEditView`衍生自`CCtrlView`。

若要在您的應用程式中使用這些類別，請從它們衍生的應用程式檢視類別。 如需相關資訊，請參閱[捲動和縮放檢視](../mfc/scrolling-and-scaling-views.md)。 如需有關資料庫類別的詳細資訊，請參閱 <<c0> [ 概觀： 資料庫程式設計](../data/data-access-programming-mfc-atl.md)。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)

