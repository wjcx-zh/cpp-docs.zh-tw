---
title: 變更清單控制項樣式
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370808"
---
# <a name="changing-list-control-styles"></a>變更清單控制項樣式

建立清單控制件 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 的視窗樣式後,您可以隨時更改它的視窗樣式。 通過更改視窗樣式,可以更改控制項使用的檢視類型。 例如,要模擬資源管理器,可以提供菜單項或工具列按鈕,以便在不同檢視之間切換控制項:圖示視圖、清單檢視等。

例如,當用戶選擇功能表項時,您可以調用[GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)以檢索控制件的當前樣式,然後調用[SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw)重置樣式。 有關詳細資訊,請參閱在 Windows SDK 中使用[列表檢視控制項](/windows/win32/Controls/using-list-view-controls)。

可用樣式列在["創建](../mfc/reference/clistctrl-class.md#create)" 中。 **樣式**LVS_ICON、LVS_SMALLICON、LVS_LIST**LVS_LIST**和**LVS_REPORT**指定四個清單控**LVS_SMALLICON**件視圖。

## <a name="extended-styles"></a>擴充樣式

除了清單控制件的標準樣式外,還有另一個集,稱為擴展樣式。 這些樣式在 Windows SDK 中的[擴充清單檢視樣式](/windows/win32/Controls/extended-list-view-styles)中討論,提供了自訂清單控制件行為的各種有用功能。 要實現特定樣式的行為(如懸停選擇),請調用[CListCtrl::set 擴展樣式](../mfc/reference/clistctrl-class.md#setextendedstyle),傳遞所需的樣式。 以下範例展示函數呼叫:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> 要使懸停選擇正常工作,還必須**LVS_EX_ONECLICKACTIVATE 或****LVS_EX_TWOCLICKACTIVATE**打開。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
