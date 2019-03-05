---
title: 將項目加入至控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 88e008f06fb669db1c13872b1a58555eeb357d86
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304596"
---
# <a name="adding-items-to-the-control"></a>將項目加入至控制項

若要將項目新增至清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md))，呼叫的數個版本的其中一個[InsertItem](../mfc/reference/clistctrl-class.md#insertitem)成員函式，根據您擁有的資訊。 一個版本會採用[LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema)您準備的結構。 因為 `LV_ITEM` 結構包含數個成員，所有您對於清單控制項項目的屬性擁有更大的控制權。


  `LV_ITEM` 結構的兩個重要成員 (若為報表檢視) 為 `iItem` 和 `iSubItem` 成員。 
  `iItem` 成員是結構所參考項目的以零為起始的索引，而 `iSubItem` 成員是子項目的以一為起始的索引，或者如果結構包含項目的相關資訊，則是以零為起始的索引。 對於您決定的這兩個成員，當清單控制項在報表檢視中時，會按照每個項目顯示子項目資訊的類型和值。 如需詳細資訊，請參閱 < [clistctrl:: Setitem](../mfc/reference/clistctrl-class.md#setitem)。

其他成員會指定項目的文字、圖示、狀態和項目資料。 「項目資料」是與清單檢視項目關聯的應用程式定義的值。 如需詳細資訊`LV_ITEM`結構，請參閱[clistctrl:: Getitem](../mfc/reference/clistctrl-class.md#getitem)。


  `InsertItem` 的其他版本採用一個或多個不同值，對應 `LV_ITEM` 結構中的成員，可讓您僅初始化您要支援的那些成員。 通常，清單控制項會管理清單項目的儲存體，但是您可以使用「回呼項目」改為在應用程式中儲存部分資訊。 如需詳細資訊，請參閱 <<c0> [ 回呼項目和回呼遮罩](../mfc/callback-items-and-the-callback-mask.md)本主題中並[回呼項目和回呼遮罩](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

如需詳細資訊，請參閱 <<c0> [ 加入清單檢視項目和子項目](/windows/desktop/Controls/using-list-view-controls)。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
