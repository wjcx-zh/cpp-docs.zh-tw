---
title: 在清單控制項中實作工作區域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: abbf9dd823e13fab252b7af8f32338b0d801079b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626378"
---
# <a name="implementing-working-areas-in-list-controls"></a>在清單控制項中實作工作區域

根據預設，清單控制項會以標準方格的方式來排列所有專案。 不過，另一個方法是支援的工作區域，可將清單專案排列成矩形群組。 如需可執行工作區域之清單控制項的影像，請參閱在 Windows SDK 中使用清單視圖控制項。

> [!NOTE]
> 只有當清單控制項為圖示或小型圖示模式時，工作區才會顯示。 不過，如果此視圖切換到報表或清單模式，則會保留任何目前的工作區。

工作區域可以用來顯示空的框線（在專案的左邊、上方和/或右方），或在一般情況下不會出現水準捲軸。 另一個常見的用法是建立多個工作區域，以移動或卸載專案。 使用此方法，您可以在具有不同意義的單一視圖中建立區域。 然後使用者可以將這些專案放在不同的區域，藉此將它們分類。 其中一個範例就是具有讀取/寫入檔案區域和唯讀檔案之另一個區域的檔案系統的觀點。 如果檔案專案已移至唯讀區域，它會自動變成隻讀。 將檔案從唯讀區域移至讀取/寫入區域，會使檔案變成讀取/寫入。

`CListCtrl`提供數個成員函式，用來建立和管理清單控制項中的工作區。 [GetWorkAreas](reference/clistctrl-class.md#getworkareas)和[SetWorkAreas](reference/clistctrl-class.md#setworkareas)會抓取和設定物件的陣列 `CRect` （或 `RECT` 結構），以儲存目前為您的清單控制項所實作用的工作區。 此外， [GetNumberOfWorkAreas](reference/clistctrl-class.md#getnumberofworkareas)會抓取清單控制項目前的工作區數（預設為零）。

## <a name="items-and-working-areas"></a>專案和工作區

建立工作區時，位於工作區域內的專案會成為其成員。 同樣地，如果某個專案移到工作區域中，它就會成為其所移動之工作區域的成員。 如果專案不在任何工作區域內，它會自動成為第一個（索引0）工作區域的成員。 如果您想要建立專案並將它放在特定的工作區域中，您必須建立專案，然後使用[SetItemPosition](reference/clistctrl-class.md#setitemposition)的呼叫，將它移至所需的工作區域。 下列第二個範例示範這項技術。

下列範例會 `rcWorkAreas` 在清單控制項（）中，執行大小相同且每個工作區域具有10圖元寬框線的四個工作區域（） `m_WorkAreaListCtrl` 。

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

已對[ApproximateViewRect](reference/clistctrl-class.md#approximateviewrect)進行呼叫，以取得在一個區域中顯示所有專案所需的總區域估計值。 然後，此預估會分成四個區域，並以5個圖元寬的框線填補。

下一個範例會將現有的清單專案指派給每個群組（ `rcWorkAreas` ），並重新整理控制項視圖（ `m_WorkAreaListCtrl` ）以完成效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
