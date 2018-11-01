---
title: 滑桿控制項樣式
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: 7b143d0d27bcb8ee975d4056cf0a307db7b330c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588730"
---
# <a name="slider-control-styles"></a>滑桿控制項樣式

滑桿控制項 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 可以具有垂直或水平方向。 它們可以在其中一側具有刻度標記，或兩側皆有或兩側皆沒有。 它們也可以用來指定連續值的範圍。 這些屬性是藉由使用滑桿控制樣式來控制，您在建立滑桿控制項時會指定該樣式。

TBS_HORZ 和 TBS_VERT 樣式會判斷滑桿控制項的方向。 如果您不指定方向，滑桿控制項會是水平方向。

TBS_AUTOTICKS 樣式會建立在其範圍值中有針對每個增量有刻度記號的滑桿控制項。 當您呼叫時自動加入這些刻度[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成員函式。 如果您未指定 TBS_AUTOTICKS，您可以使用成員函式，例如[SetTic](../mfc/reference/csliderctrl-class.md#settic)並[SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)，以指定的刻度標記位置。 若要建立不顯示刻度標記的滑桿控制項，您可以使用 TBS_NOTICKS 樣式。

您可以在滑桿控制項的任一或兩側顯示刻度標記。 對於水平滑桿控制項，您可以指定 TBS_BOTTOM 或 TBS_TOP 樣式。 對於垂直滑桿控制項，您可以指定 TBS_RIGHT 或 TBS_LEFT 樣式。 （TBS_BOTTOM 和 TBS_RIGHT 是預設設定）。若是任一方向之滑桿控制項兩端的刻度標記，指定 TBS_BOTH 樣式。

只有當您在建立時，會指定 TBS_ENABLESELRANGE 樣式，滑桿控制項可以顯示的選取範圍。 當滑桿控制項具有此樣式時，刻度標記會位於選取範圍的開始和結束位置，顯示為三角形 (而非垂直虛線)，並會反白顯示選取範圍。 例如，選取範圍可能適用於簡單的排程應用程式。 使用者可以選取對應一天內小時數的刻度標記範圍來識別排定會議的時間。

根據預設，滑桿控制項的滑桿長度會隨著選取範圍而變更。 如果滑桿控制項具有 TBS_FIXEDLENGTH 樣式，滑桿的長度會保持不變即使選取範圍已變更。 具有 TBS_NOTHUMB 樣式的滑桿控制項不包含滑桿。

## <a name="see-also"></a>另請參閱

[使用 CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

