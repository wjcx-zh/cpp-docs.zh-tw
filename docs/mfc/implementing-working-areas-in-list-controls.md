---
title: 在清單控制項中實作工作區域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 01b166243c9032a113d46ff297b9f6e53429da21
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281599"
---
# <a name="implementing-working-areas-in-list-controls"></a>在清單控制項中實作工作區域

根據預設，清單控制項排列標準格線樣式中的所有項目。 不過，另一個支援方法，工作區，將清單項目排列成矩形的群組。 實作工作區域的清單控制項的映像，請參閱 Windows SDK 中使用清單檢視控制項。

> [!NOTE]
>  只有當清單控制項處於圖示或小圖示模式時，會顯示工作區域。 不過，如果檢視切換到 報表 或 清單模式，會保留任何目前的工作區域。

若要顯示空的框線 （位於左側、 上方和/或項目右邊），或導致時通常不會有一個要顯示水平捲軸可用工作區域。 另一個常見用法是建立多個工作區的項目可以移動或卸除。 使用此方法，您可以建立具有不同的意義的單一檢視中的區域。 然後，使用者無法分類的項目，將它們放在不同的區域。 這個範例是一個檔案系統，具有讀取/寫入檔案的區域和唯讀檔案的另一個區域的檢視。 如果檔案項目已移至 [唯讀] 區域中，它會自動變成唯讀狀態。 將檔案從唯讀區域移到讀取/寫入區域，會使檔案讀取/寫入。

`CListCtrl` 提供數個成員函式來建立及管理您的清單控制項中的工作區域。 [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas)並[SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas)擷取和設定的陣列`CRect`物件 (或`RECT`結構)，其中儲存您的清單控制項的目前實作的工作區域。 颾魤 ㄛ [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas)擷取您的清單控制項的工作區域的目前數目 （根據預設，零）。

## <a name="items-and-working-areas"></a>項目和工作區

建立工作區時，工作區域內的項目就會成為它的成員。 同樣地，如果項目移到工作區，它會成為它已移動的工作區的成員。 如果項目不在其內的任何工作區域，它會自動變成第一個 （索引 0） 工作區的成員。 如果您想要建立項目，並將它放在特定的工作區域內，您必須建立項目，然後將它移到所需的工作區域，藉由呼叫[SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)。 下列第二個範例會示範這項技巧。

下列範例會實作四個工作區 (`rcWorkAreas`)，具有 10 像素寬的框線，針對每個工作的領域，清單控制項中的相同大小的 (`m_WorkAreaListCtrl`)。

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

若要在呼叫[ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect)對整個區域顯示在一個區域中的所有項目所需的估計。 這項估計然後分成四個區域，並填滿 5 像素寬的框線。

下一個範例會將現有的清單項目指派給每個群組 (`rcWorkAreas`)，並重新整理的控制項檢視 (`m_WorkAreaListCtrl`) 完成的效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
