---
title: 樹狀目錄控制項目狀態概觀
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: 57c6714073f4939ffb791a78454e9eac6342309b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264595"
---
# <a name="tree-control-item-states-overview"></a>樹狀目錄控制項目狀態概觀

樹狀結構控制項中的每個項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 的目前狀態。 例如，項目可選取、停用、展開等等。 在大部分的情況下，樹狀目錄控制項會自動設定項目的狀態以反映使用者動作，例如選擇項目。 您也可以使用設定項目的狀態的但是[SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate)成員函式並擷取項目所使用的目前狀態[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)成員函式。 項目狀態的完整清單，請參閱[樹狀檢閱控制項常數](/windows/desktop/Controls/tree-view-control-item-states)Windows SDK 中。

所指定項目的目前狀態*nState*參數。 樹狀目錄控制項可能會變更項目的狀態來反映自訂動作，例如選取項目或為項目設定焦點。 此外，應用程式可變更項目的狀態以停用或隱藏項目，或指定重疊影像或狀態影像。

當您指定或變更項目的狀態*nStateMask*參數可讓您指定哪些狀態位元設定，而*nState*參數會包含這些位元的新值。 例如，下列範例會變更目前的父項目狀態 (所指定*hParentItem*) 中`CTreeCtrl`物件 (`m_treeCtrl`) 以`TVIS_EXPANDPARTIAL`:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

變更狀態的另一個範例是設定項目的重疊影像。 若要這麼做， *nStateMask*必須包含`TVIS_OVERLAYMASK`的值，以及*nState*必須包含以一為基的覆疊影像索引移位使用向左八個位元[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)巨集。 索引可為 0，表示不指定重疊影像。 覆疊影像必須已新增至樹狀目錄控制項的清單，覆疊影像的先前呼叫所[cimagelist:: Setoverlayimage](../mfc/reference/cimagelist-class.md#setoverlayimage)函式。 函式會指定以一為基的索引表示要加入，映像這是 INDEXTOOVERLAYMASK 巨集所用的索引。 樹狀目錄控制項有四個重疊影像。

若要設定項目的狀態影像， *nStateMask*必須包含`TVIS_STATEIMAGEMASK`的值，以及*nState*必須包含一起始的索引的移位狀態影像使用剩餘的 12 位元[INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask)巨集。 索引可為 0，表示不指定狀態影像。 如需重疊和狀態影像的詳細資訊，請參閱[樹狀目錄控制項影像清單](../mfc/tree-control-image-lists.md)。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
