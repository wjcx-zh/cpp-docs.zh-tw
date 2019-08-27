---
title: 樹狀目錄控制項目狀態概觀
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bbeabf69f174fcf172808ff71f07ed05f1dc9675
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511047"
---
# <a name="tree-control-item-states-overview"></a>樹狀目錄控制項目狀態概觀

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的每個專案都有目前的狀態。 例如，項目可選取、停用、展開等等。 在大部分的情況下，樹狀目錄控制項會自動設定項目的狀態以反映使用者動作，例如選擇項目。 不過, 您也可以使用[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成員函式來設定專案的狀態, 並使用[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成員函式來取出專案的目前狀態。 如需專案狀態的完整清單, 請參閱 Windows SDK 中的[樹狀檢視控制項常數](/windows/win32/Controls/tree-view-control-item-states)。

專案的目前狀態是由*nState*參數所指定。 樹狀目錄控制項可能會變更項目的狀態來反映自訂動作，例如選取項目或為項目設定焦點。 此外，應用程式可變更項目的狀態以停用或隱藏項目，或指定重疊影像或狀態影像。

當您指定或變更專案的狀態時, *nStateMask*參數會指定要設定的狀態位, 而*nState*參數會包含這些位的新值。 例如, 下列範例會將`CTreeCtrl`物件 (`m_treeCtrl`) 中父項 (由 hParentItem 指定) 的目前狀態變更為: `TVIS_EXPANDPARTIAL`

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

變更狀態的另一個範例是設定項目的重疊影像。 若要完成這項操作, nStateMask `TVIS_OVERLAYMASK`必須包含值, 而*nState*必須包含使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏向左移動八個位的重迭影像以一為基的索引。 索引可為 0，表示不指定重疊影像。 對[CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)函式的先前呼叫, 必須已將重迭影像加入至樹狀目錄控制項的覆迭影像清單。 函式會指定要加入之映射的以一為基的索引;這是與 INDEXTOOVERLAYMASK 宏搭配使用的索引。 樹狀目錄控制項有四個重疊影像。

若要設定專案的狀態影像, *nStateMask*必須包含`TVIS_STATEIMAGEMASK`值, 而*nState*必須包含狀態影像的以一為起始的索引, 而後者使用[INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask)宏向左移動了12位。 索引可為 0，表示不指定狀態影像。 如需重迭和狀態影像的詳細資訊, 請參閱[樹狀目錄控制項影像清單](../mfc/tree-control-image-lists.md)。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
