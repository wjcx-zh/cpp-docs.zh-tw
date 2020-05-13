---
title: 使用 CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366475"
---
# <a name="using-cspinbuttonctrl"></a>使用 CSpinButtonCtrl

*旋轉按鈕*控制項(也稱為*向上向下*控制項)提供一對箭頭,用戶可以按下該箭頭來調整值。 這個值為*目前位置*。 此位置會保持在微調按鈕的範圍內。 當使用者按一下向上箭號時，此位置會朝最大值移動，當使用者按一下向下箭號時，此位置會朝最小值移動。

旋轉按鈕控制項由[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)類在 MFC 中表示。

> [!NOTE]
> 根據預設，微調按鈕的範圍具有最大值為零 (0) 和最小值為 100。 因為最大值小於最小值，因此按一下向上箭號會遞減位置，按一下向下箭號會遞增位置。 使用[CSpinButtonCtrl:設置範圍](../mfc/reference/cspinbuttonctrl-class.md#setrange)來調整這些值。

通常，目前位置會顯示於附屬控制項中。 套件的套件為*好友視窗*。 有關旋轉按鈕控制項的說明,請參閱 Windows SDK 中的[「向上向下控制件](/windows/win32/Controls/up-down-controls)」。

在 Visual Studio 中，若要建立一個微調控制項以及一個編輯控制項協同視窗，請先將編輯控制項加入至對話方塊或視窗，然後再拖曳微調控制項。 選擇旋轉控制項,並將自動**好友**與**將好友整數屬性設定為** **True**。 還設置**對齊**屬性;**右對齊**最典型。 這些設定將編輯控制項設定為協同視窗，因為它的定位順序直接位在編輯控制項之前。 編輯控制項會顯示整數，而微調控制項會內嵌在編輯控制項的右邊。 或者,您可以使用[CSpinButtonCtrl:setRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)方法設置旋轉控制項的有效範圍。 微調控制項和協同視窗之間不需要透過事件處理常式進行溝通，它們會直接交換資料。 如果將自旋控制件用於其他目的,例如,透過一系列視窗或對話框進行頁面,則為UDN_DELTAPOS消息添加處理程式,並在那裡執行自定義操作。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [微調按鈕樣式](../mfc/spin-button-styles.md)

- [微調按鈕成員函式](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)
