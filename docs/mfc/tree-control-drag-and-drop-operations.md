---
title: 樹狀目錄控制項拖放作業
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5dc498008c6b019635cd361a950c6d2926e26541
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519362"
---
# <a name="tree-control-drag-and-drop-operations"></a>樹狀目錄控制項拖放作業

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送通知，當使用者開始拖曳項目。 控制項會傳送[TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag)當使用者開始拖曳滑鼠左鍵的項目時，會產生通知訊息。 並[TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag)使用者開始拖曳時，會產生通知訊息。右邊的按鈕。 您可以防止樹狀目錄控制項提供 TVS_DISABLEDRAGDROP 樣式的樹狀控制項傳送這些通知。

取得要顯示在拖曳作業期間，藉由呼叫影像[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成員函式。 樹狀控制項會根據被拖曳的項目之標籤產生拖曳點陣圖。 然後樹狀結構控制項中建立影像清單、 加入點陣圖至它，並將指標傳回至[CImageList](../mfc/reference/cimagelist-class.md)物件。

您必須提供實際拖曳項目的程式碼。 這通常牽涉到使用影像清單函式的拖曳功能和處理[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)並[WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (或[WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup))在拖曳作業開始後所傳送的訊息。 如需有關影像清單函式的詳細資訊，請參閱[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考 》* 並[影像清單](https://msdn.microsoft.com/library/windows/desktop/bb761389)Windows SDK 中。 如需拖曳樹狀目錄控制項目的詳細資訊，請參閱 <<c0> [ 拖曳樹狀檢視項目](/windows/desktop/Controls/tree-view-controls)，也在 Windows SDK 中。

如果在樹狀控制項中的項目是拖放作業的目標，您需要知道滑鼠游標何時位於目標項目上。 您可以藉由呼叫了[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成員函式。 您指定的點和整數或位址[TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo)結構，其中包含滑鼠游標目前座標。 當函式傳回時，整數或結構會包含一個旗標，表示相對於樹狀控制項的滑鼠游標位置。 如果游標位於樹狀控制項中的項目上，結構也會包含該項目的控制代碼。

您可以指定項目是拖放作業的目標，藉由呼叫[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成員函式來將狀態設定為`TVIS_DROPHILITED`值。 具有這個狀態的項目會繪製為用來表示拖放目標的樣式。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

