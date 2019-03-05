---
title: 為標題項目提供拖放支援
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: f30ad029742a01280abda85cbd1a81104d01d8cd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263714"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>為標題項目提供拖放支援

若要針對標題項目提供拖放支援，請指定 HDS_DRAGDROP 樣式。 為標題項目提供的拖放功能支援可讓使用者重新排列標題控制項的標題項目。 如果置放標題項目，預設行為會提供拖曳之標題項目的半透明拖曳影像，以及新位置的視覺指標。

做為一般的拖放功能，您可以藉由處理 HDN_BEGINDRAG 和 HDN_ENDDRAG 通知擴充預設的拖放行為。 您也可以藉由覆寫自訂拖曳影像的外觀[cheaderctrl:: Createdragimage](../mfc/reference/cheaderctrl-class.md#createdragimage)成員函式。

> [!NOTE]
>  如果您在清單控制項中的內嵌的標題控制項提供拖放支援，請參閱中的延伸樣式 」 一節[變更清單控制項樣式](../mfc/changing-list-control-styles.md)主題。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
