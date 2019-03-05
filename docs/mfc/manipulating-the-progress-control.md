---
title: 管理進度控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289152"
---
# <a name="manipulating-the-progress-control"></a>管理進度控制項

有三種方式可變更進度控制項的目前位置 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md))。

- 可依照預設的遞增數量變更位置。

- 可依照任意數量變更位置。

- 可以特定值變更位置。

### <a name="to-change-the-position-by-a-preset-amount"></a>依照預設的數量變更位置

1. 使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)成員函式設定遞增數量。 根據預設，這個值會是 10。 這個值通常設定為控制項的其中一個初始設定。 間距值可以是負數。

1. 使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)成員函式遞增位置。 這會造成控制項自行重繪。

    > [!NOTE]
    >  `StepIt` 會導致位置換行。 例如，指定的範圍是 1-100，間距為 20 而位置為 90，`StepIt`會將位置設為 10。

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>依照任意數量變更位置

1. 使用[OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos)成員函式來變更位置。 `OffsetPos` 會接受負值。

    > [!NOTE]
    >  `OffsetPos` 不同於 `StepIt`，不會將位置換行。 會調整新位置為保持在範圍內。

### <a name="to-change-the-position-to-a-specific-value"></a>將位置變更為特定值

1. 使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)成員函式來將位置設定為特定值。 必要時，將新位置調整為在範圍內。

通常，進度控制項只用於輸出。 若要取得目前的位置，而不會指定新的值，使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。

## <a name="see-also"></a>另請參閱

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
