---
title: 拖放：實作置放來源
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: cceed8517c7b63588c7b1b90e3306d90f0921b78
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300742"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>拖放：實作置放來源

這篇文章說明如何取得您的應用程式提供資料給拖放作業。

基本實作置放來源也相當簡單。 第一個步驟是判斷哪些事件開始拖曳作業。 建議使用者介面指導方針定義為資料的選取範圍的拖曳作業開始時， **WM_LBUTTONDOWN**內選取的資料點上發生的事件。 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)並[HIERSVR](../visual-cpp-samples.md)遵循這些指導方針。

如果您的應用程式是一個容器，而且選取的資料連結或內嵌的物件的型別`COleClientItem`，呼叫其`DoDragDrop`成員函式。 否則，建構`COleDataSource`物件，將它初始化選取項目，然後呼叫資料來源物件的`DoDragDrop`成員函式。 如果您的應用程式伺服器，請使用`COleServerItem::DoDragDrop`。 如需自訂標準的拖放行為的資訊，請參閱文章[將拖放：自訂](../mfc/drag-and-drop-customizing.md)。

如果`DoDragDrop`會傳回**DROPEFFECT_MOVE**，立即刪除來源資料從來源文件。 從任何其他傳回值`DoDragDrop`置放來源上的任何作用。

如需詳細資訊，請參閱:

- [實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [自訂拖曳和置放](../mfc/drag-and-drop-customizing.md)

- [建立和終結 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [管理 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>另請參閱

[拖放 (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
