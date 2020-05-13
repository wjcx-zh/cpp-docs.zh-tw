---
title: 在工具列控制項中使用影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366489"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具列控制項中使用影像清單

預設情況下,工具列控制項中按鈕使用的圖像將儲存為單個點陣圖。 但是,您還可以將按鈕圖像存儲在一組圖像清單中。 工具列控制件物件最多可以使用三個單獨的影像清單:

- 已啟用的影像清單 包含當前啟用的工具列按鈕的圖像。

- 關閉的影像清單 包含目前關閉的工具列按鈕的影像。

- 突顯的影像清單 包含目前突顯的工具列按鈕的影像。 僅當工具列使用TBSTYLE_FLAT樣式時,才會使用此圖像清單。

當您將它們與`CToolBarCtrl`物件關聯時,工具列控制項會使用這些圖像清單。 此關聯是通過調用[CToolBarCtrl::設置圖像清單](../mfc/reference/ctoolbarctrl-class.md#setimagelist)、[設置禁用圖像清單](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)和[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)來實現的。

默認情況下,MFC`CToolBar`使用 該類來實現 MFC 應用程式工具列。 但是,`GetToolBarCtrl`成員函數可用於檢索嵌`CToolBarCtrl`入的物件。 然後,可以使用返回的對象`CToolBarCtrl`對成員函數進行調用。

下面的範例透過將已啟用的`m_ToolBarImages`( ) 和關閉`m_ToolBarDisabledImages`( ) 映`CToolBarCtrl`像`m_ToolBarCtrl`清單分配給 物件 ( ) 展示此技術。

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> 工具列物件使用的圖像清單必須是永久物件。 因此,它們通常是 MFC 類的數據成員;在此示例中,主框架視窗類。

一旦圖像清單與`CToolBarCtrl`物件關聯,框架將自動顯示正確的按鈕圖像。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
