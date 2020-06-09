---
title: 將項目加入至控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 5cc1c7a921cf6d6ba2c0f968012b48bfcaef0658
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623371"
---
# <a name="adding-items-to-the-control"></a>將項目加入至控制項

若要將專案新增至清單控制項（[CListCtrl](reference/clistctrl-class.md)），請根據您擁有的資訊，呼叫其中一個[InsertItem](reference/clistctrl-class.md#insertitem)成員函式版本的其中一個。 其中一個版本會採用您準備的[LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw)結構。 因為 `LVITEM` 結構包含數個成員，所有您對於清單控制項項目的屬性擁有更大的控制權。

`LVITEM` 結構的兩個重要成員 (若為報表檢視) 為 `iItem` 和 `iSubItem` 成員。 `iItem` 成員是結構所參考項目的以零為起始的索引，而 `iSubItem` 成員是子項目的以一為起始的索引，或者如果結構包含項目的相關資訊，則是以零為起始的索引。 對於您決定的這兩個成員，當清單控制項在報表檢視中時，會按照每個項目顯示子項目資訊的類型和值。 如需詳細資訊，請參閱[CListCtrl：： SetItem](reference/clistctrl-class.md#setitem)。

其他成員會指定項目的文字、圖示、狀態和項目資料。 「項目資料」是與清單檢視項目關聯的應用程式定義的值。 如需結構的詳細資訊 `LVITEM` ，請參閱[CListCtrl：： GetItem](reference/clistctrl-class.md#getitem)。

`InsertItem` 的其他版本採用一個或多個不同值，對應 `LVITEM` 結構中的成員，可讓您僅初始化您要支援的那些成員。 通常，清單控制項會管理清單項目的儲存體，但是您可以使用「回呼項目」改為在應用程式中儲存部分資訊。 如需詳細資訊，請參閱本主題中的[回呼專案和回呼遮罩](callback-items-and-the-callback-mask.md)和 Windows SDK 中[的回呼專案和回呼遮罩](/windows/win32/Controls/using-list-view-controls)。

如需詳細資訊，請參閱[加入清單-視圖專案和子專案](/windows/win32/Controls/using-list-view-controls)。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
