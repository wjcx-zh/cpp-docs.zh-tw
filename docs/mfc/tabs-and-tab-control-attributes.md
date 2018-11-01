---
title: 索引標籤和索引標籤控制項屬性
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: ba63fdca32af28d0763dd4cf2da3465a99ddeb1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571986"
---
# <a name="tabs-and-tab-control-attributes"></a>索引標籤和索引標籤控制項屬性

您有相當大的控制權的外觀和行為的索引標籤組成的索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。 每個索引標籤可以有標籤、 圖示、 項目狀態和與其相關聯的應用程式定義的 32 位元值。 針對每個索引標籤中，您可以顯示圖示、 標籤，或兩者。

此外，每個索引標籤項目可以有三種可能狀態： 已按下，未按下或反白顯示。 此狀態只可以設定藉由修改現有的索引標籤項目。 若要修改現有的索引標籤項目，擷取它藉由呼叫[GetItem](../mfc/reference/ctabctrl-class.md#getitem)，修改`TCITEM`結構 (特別*dwState*並*dwStateMask*資料成員)，然後傳回已修改`TCITEM`結構，藉由呼叫[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 如果您要清除項目狀態中的所有索引標籤項目的`CTabCtrl`物件，呼叫[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)。 此函式會重設 索引標籤上的所有項目或所有的項目，除了目前所選取的狀態。

下列程式碼會清除所有的索引標籤項目的狀態，然後再修改 第三個項目的狀態：

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

如需 索引標籤上屬性的詳細資訊，請參閱[索引標籤和索引標籤屬性](/windows/desktop/Controls/tab-controls)Windows SDK 中。 如需將索引標籤加入至索引標籤控制項的詳細資訊，請參閱[新增至索引標籤控制項的索引標籤](../mfc/adding-tabs-to-a-tab-control.md)本主題稍後的。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

