---
title: 建立影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 844bfe71f7b03f299f57b0fd4558b7e9eacf67c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242233"
---
# <a name="creating-the-image-lists"></a>建立影像清單

建立影像清單不論您使用的是相同[CListView](../mfc/reference/clistview-class.md)或是[CListCtrl](../mfc/reference/clistctrl-class.md)。

> [!NOTE]
>  您只需要映像清單如果清單控制項包含`LVS_ICON`樣式。

使用類別`CImageList`建立一或多個映像清單 （適用於完整大小的圖示、 小圖示和狀態）。 請參閱[CImageList](../mfc/reference/cimagelist-class.md)，並查看[清單檢視影像清單](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

呼叫[CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist)每個映像清單，將指標傳遞至適當`CImageList`物件。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
