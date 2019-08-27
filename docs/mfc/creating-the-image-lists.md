---
title: 建立影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508790"
---
# <a name="creating-the-image-lists"></a>建立影像清單

無論您使用[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md), 建立影像清單都是相同的。

> [!NOTE]
>  如果您的`LVS_ICON`清單控制項包含樣式, 您只需要影像清單。

使用 [ `CImageList`類別] 來建立一或多個影像清單 (適用于完整大小的圖示、小圖示和狀態)。 請參閱[CImageList](../mfc/reference/cimagelist-class.md), 並查看 Windows SDK 中的[清單視圖影像清單](/windows/win32/Controls/using-list-view-controls)。

針對每個影像清單呼叫[CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) ;將指標傳遞至適當`CImageList`的物件。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
