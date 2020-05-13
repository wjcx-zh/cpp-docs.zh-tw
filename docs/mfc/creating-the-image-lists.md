---
title: 建立影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371579"
---
# <a name="creating-the-image-lists"></a>建立影像清單

無論您使用[CListView](../mfc/reference/clistview-class.md)還是[CListCtrl,](../mfc/reference/clistctrl-class.md)創建圖像清單都是相同的。

> [!NOTE]
> 只使用清單控制檔包含樣式時,`LVS_ICON`才需要影像清單。

使用類`CImageList`創建一個或多個圖像列表(對於全尺寸圖示、小圖示和狀態)。 請參考[CImageList](../mfc/reference/cimagelist-class.md),並檢視 Windows SDK 中的[清單檢視映像清單](/windows/win32/Controls/using-list-view-controls)。

呼叫[CListCtrl:為每個影像清單設定影像清單](../mfc/reference/clistctrl-class.md#setimagelist);將指標傳遞給相應的`CImageList`物件。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
