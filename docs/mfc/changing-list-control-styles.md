---
title: 變更清單控制項樣式
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: b3cc65ce6ef0e84eaa2f6738cb18b6b862a6473a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509046"
---
# <a name="changing-list-control-styles"></a>變更清單控制項樣式

建立清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 之後, 您可以隨時變更其視窗樣式。 藉由變更視窗樣式, 您可以變更控制項使用的檢視類型。 例如, 若要模擬 Explorer, 您可能會提供功能表項目或工具列按鈕, 以便在不同的視圖之間切換控制項: 圖示視圖、清單視圖等等。

例如, 當使用者選取您的功能表項目時, 您可以呼叫[GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)來取得控制項目前的樣式, 然後呼叫[SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw)來重設樣式。 如需詳細資訊, 請參閱在 Windows SDK 中[使用清單視圖控制項](/windows/win32/Controls/using-list-view-controls)。

[[建立](../mfc/reference/clistctrl-class.md#create)] 中列出可用的樣式。 **LVS_ICON**、 **LVS_SMALLICON**、 **LVS_LIST**和**LVS_REPORT**樣式會指定四個清單控制項 views。

## <a name="extended-styles"></a>延伸樣式

除了清單控制項的標準樣式以外, 還有另一個集合, 稱為擴充樣式。 這些樣式 (在 Windows SDK 的[擴充清單視圖樣式](/windows/win32/Controls/extended-list-view-styles)中討論) 提供了各種實用的功能, 可自訂清單控制項的行為。 若要執行特定樣式的行為 (例如暫留選取), 請呼叫[CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), 並傳遞所需的樣式。 下列範例示範函式呼叫:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  若要讓暫留選取作業正常, 您也必須開啟**LVS_EX_ONECLICKACTI加值稅E**或**LVS_EX_TWOCLICKACTI加值稅E** 。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
