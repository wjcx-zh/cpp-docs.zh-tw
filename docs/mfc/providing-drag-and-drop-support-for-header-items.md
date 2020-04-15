---
title: 為標題項目提供拖放支援
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371155"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>為標題項目提供拖放支援

要為標頭項提供拖放支援,請指定HDS_DRAGDROP樣式。 為標題項目提供的拖放功能支援可讓使用者重新排列標題控制項的標題項目。 如果置放標題項目，預設行為會提供拖曳之標題項目的半透明拖曳影像，以及新位置的視覺指標。

如同一般拖放功能，您可以藉由處理 HDN_BEGINDRAG 和 HDN_ENDDRAG 通知來延伸預設拖放行為。 您還可以透過重寫[CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage)成員函數來自定義拖動影像的外觀。

> [!NOTE]
> 如果要在清單控制項中為嵌入標頭控制項提供拖放支援,請參閱[「更改清單控制件樣式」](../mfc/changing-list-control-styles.md)主題中的「擴展樣式」 部分。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
