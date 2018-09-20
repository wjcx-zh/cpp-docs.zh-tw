---
title: 建立映像清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7772b6b6a809e5a89e2cb6b0ef3edb68821805c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372311"
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

