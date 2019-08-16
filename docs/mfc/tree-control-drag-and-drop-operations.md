---
title: 樹狀目錄控制項拖放作業
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510915"
---
# <a name="tree-control-drag-and-drop-operations"></a>樹狀目錄控制項拖放作業

當使用者開始拖曳專案時, 樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會傳送通知。 當使用者開始拖曳具有滑鼠左鍵的專案時, 控制項會傳送[TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag)通知訊息, 而當使用者使用右按鈕開始拖曳時, 就會傳送[TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag)通知訊息。 您可以為樹狀目錄控制項提供 TVS_DISABLEDRAGDROP 樣式, 以防止樹狀目錄控制項傳送這些通知。

您可以藉由呼叫[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成員函式, 取得要在拖曳作業期間顯示的影像。 樹狀控制項會根據被拖曳的項目之標籤產生拖曳點陣圖。 然後, 樹狀目錄控制項會建立影像清單、在其中加入點陣圖, 然後傳回[CImageList](../mfc/reference/cimagelist-class.md)物件的指標。

您必須提供實際拖曳項目的程式碼。 這通常牽涉到使用影像清單功能的拖曳功能, 以及處理在拖曳作業開始後傳送的[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)和[WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (或[WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) 訊息。 如需影像清單函式的詳細資訊, 請參閱 Windows SDK 中*MFC 參考*和[影像清單](/windows/win32/controls/image-lists)中的[CImageList](../mfc/reference/cimagelist-class.md) 。 如需拖曳樹狀控制項專案的詳細資訊, 請參閱[拖曳樹狀檢視專案](/windows/win32/Controls/tree-view-controls)(也在 Windows SDK 中)。

如果在樹狀控制項中的項目是拖放作業的目標，您需要知道滑鼠游標何時位於目標項目上。 您可以藉由呼叫[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成員函式來找出。 您可以指定點和整數, 或是包含滑鼠游標目前座標的[TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo)結構的位址。 當函式傳回時，整數或結構會包含一個旗標，表示相對於樹狀控制項的滑鼠游標位置。 如果游標位於樹狀控制項中的項目上，結構也會包含該項目的控制代碼。

您可以呼叫[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成員函式將狀態`TVIS_DROPHILITED`設定為值, 以指出某個專案是拖放作業的目標。 具有這個狀態的項目會繪製為用來表示拖放目標的樣式。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
