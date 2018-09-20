---
title: 提供標頭項目的拖放支援 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2eaa5040d34a442868a8fa6cb9f2aae08b0a6f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407695"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>為標題項目提供拖放支援

若要針對標題項目提供拖放支援，請指定 HDS_DRAGDROP 樣式。 為標題項目提供的拖放功能支援可讓使用者重新排列標題控制項的標題項目。 如果置放標題項目，預設行為會提供拖曳之標題項目的半透明拖曳影像，以及新位置的視覺指標。

做為一般的拖放功能，您可以藉由處理 HDN_BEGINDRAG 和 HDN_ENDDRAG 通知擴充預設的拖放行為。 您也可以藉由覆寫自訂拖曳影像的外觀[cheaderctrl:: Createdragimage](../mfc/reference/cheaderctrl-class.md#createdragimage)成員函式。

> [!NOTE]
>  如果您在清單控制項中的內嵌的標題控制項提供拖放支援，請參閱中的延伸樣式 」 一節[變更清單控制項樣式](../mfc/changing-list-control-styles.md)主題。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

