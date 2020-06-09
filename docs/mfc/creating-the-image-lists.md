---
title: 建立影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: bbba01a6a8e08ea53e164656733aa06e03dd87a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625955"
---
# <a name="creating-the-image-lists"></a>建立影像清單

無論您使用[CListView](reference/clistview-class.md)或[CListCtrl](reference/clistctrl-class.md)，建立影像清單都是相同的。

> [!NOTE]
> 如果您的清單控制項包含樣式，您只需要影像清單 `LVS_ICON` 。

使用 [類別] `CImageList` 來建立一或多個影像清單（適用于完整大小的圖示、小圖示和狀態）。 請參閱[CImageList](reference/cimagelist-class.md)，並查看 Windows SDK 中的[清單視圖影像清單](/windows/win32/Controls/using-list-view-controls)。

針對每個影像清單呼叫[CListCtrl：： SetImageList](reference/clistctrl-class.md#setimagelist) ;將指標傳遞至適當的 `CImageList` 物件。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
