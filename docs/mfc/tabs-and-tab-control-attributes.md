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
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511237"
---
# <a name="tabs-and-tab-control-attributes"></a>索引標籤和索引標籤控制項屬性

您對組成索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 的索引標籤外觀和行為有相當大的控制權。 每個索引標籤都可以有一個與它相關聯的標籤、圖示、專案狀態和應用程式定義的32位值。 針對每個索引標籤, 您可以顯示圖示、標籤或兩者。

此外, 每個索引標籤專案可以有三種可能的狀態: 已按下、unpressed 或反白顯示。 此狀態只能透過修改現有的索引標籤專案來設定。 若要修改現有的索引標籤專案, 請使用[GetItem](../mfc/reference/ctabctrl-class.md#getitem)的呼叫來抓取`TCITEM`它、修改結構 (特別是*dwState*和*dwStateMask*資料成員), 然後使用`TCITEM`呼叫來傳回修改過的結構[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 如果您需要清除`CTabCtrl`物件中所有索引標籤專案的專案狀態, 請呼叫[DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)。 此函式會重設所有索引標籤專案或所有專案的狀態, 但目前選取的專案除外。

下列程式碼會清除所有索引標籤專案的狀態, 然後修改第三個專案的狀態:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

如需有關選項卡屬性的詳細資訊, 請參閱 Windows SDK 中的索引標籤和索引標籤[屬性](/windows/win32/Controls/tab-controls)。 如需將索引標籤加入至索引標籤控制項的詳細資訊, 請參閱本主題稍後的將索引標籤[加入至索引標籤控制項](../mfc/adding-tabs-to-a-tab-control.md)。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
