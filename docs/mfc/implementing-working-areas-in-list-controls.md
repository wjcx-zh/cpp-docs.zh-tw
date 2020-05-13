---
title: 在清單控制項中實作工作區域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377217"
---
# <a name="implementing-working-areas-in-list-controls"></a>在清單控制項中實作工作區域

預設情況下,清單控制項以標準網格方式排列所有專案。 但是,支援另一種方法,工作區,將列表項排列到矩形組中。 有關實現工作區的清單控制件的圖像,請參閱在 Windows SDK 中使用清單視圖控制件。

> [!NOTE]
> 僅當清單控制者處於圖示或小圖示模式時,工作區才可見。 但是,如果檢視切換到報表或清單模式,則維護任何當前工作區。

工作區可用於顯示空邊框(在項目的左側、頂部和/或右側),或在通常不存在水準滾動條時導致顯示水準滾動條。 另一個常見用法是創建多個工作區,以便可以移動或刪除專案。 使用此方法,您可以在單個檢視中創建具有不同含義的區域。 然後,使用者可以通過將專案放置在其他區域來對專案進行分類。 例如,檔案系統的檢視具有讀取/寫入檔的區域和另一個唯讀檔案區域。 如果將檔項移動到唯讀區域,它將自動變為唯讀。 將檔從唯讀區域移到讀/寫區域將使檔案被讀/寫。

`CListCtrl`提供了多個成員函數,用於在清單控制項中創建和管理工作區。 [GetWork區域](../mfc/reference/clistctrl-class.md#getworkareas)和[SetWork區域](../mfc/reference/clistctrl-class.md#setworkareas)檢`CRect`索和設置 物件`RECT`(或結構) 陣列,這些物件(或結構)儲存當前實現的工作區域,以便進行清單控制。 此外[,GetNumberOfWork區域](../mfc/reference/clistctrl-class.md#getnumberofworkareas)會檢索清單控制項的當前工作區數(預設情況下為零)。

## <a name="items-and-working-areas"></a>專案與工作區域

創建工作區時,位於工作區內的項將成為工作區的成員。 同樣,如果項目移動到工作區,它將成為移動到工作區的成員。 如果專案不位於任何工作區中,它將自動成為第一個 (索引 0) 工作區的成員。 如果要建立項並將其放置在特定工作區中,則需要建立該項,然後將其移至所需的工作區中,並呼叫[SetItemMove](../mfc/reference/clistctrl-class.md#setitemposition)。 下面的第二個示例演示了此技術。

下面的示例在每個工作區周圍實現四個`rcWorkAreas`大小相等的工作區域 (),每個工作區周圍都有 10 像素寬的邊框,`m_WorkAreaListCtrl`在清單控件 () 中。

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

調用[近似檢視Rect](../mfc/reference/clistctrl-class.md#approximateviewrect)是為了獲得顯示一個區域中所有專案所需的總面積的估計值。 然後,此估計值分為四個區域,並填充了5像素寬的邊框。

下一個範例將現有清單項分配給每個組`rcWorkAreas`( ), 並刷新控制`m_WorkAreaListCtrl`項檢視 ( ) 以完成效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
