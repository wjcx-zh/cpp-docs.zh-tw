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
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622438"
---
# <a name="manipulating-the-progress-control"></a>管理進度控制項

有三種方式可變更進度控制項（[CProgressCtrl](reference/cprogressctrl-class.md)）的目前位置。

- 可依照預設的遞增數量變更位置。

- 可依照任意數量變更位置。

- 可以特定值變更位置。

### <a name="to-change-the-position-by-a-preset-amount"></a>依照預設的數量變更位置

1. 使用[SetStep](reference/cprogressctrl-class.md#setstep)成員函式來設定增量量。 根據預設，這個值是10。 這個值通常設定為控制項的其中一個初始設定。 間距值可以是負數。

1. 使用[StepIt](reference/cprogressctrl-class.md#stepit)成員函式來遞增位置。 這會造成控制項自行重繪。

    > [!NOTE]
    >  `StepIt` 會導致位置換行。 例如，假設某個範圍為 1-100、步驟為20，而位置為90，則會將 `StepIt` 位置設定為10。

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>依照任意數量變更位置

1. 使用[OffsetPos](reference/cprogressctrl-class.md#offsetpos)成員函式來變更位置。 `OffsetPos` 會接受負值。

    > [!NOTE]
    >  `OffsetPos` 不同於 `StepIt`，不會將位置換行。 會調整新位置為保持在範圍內。

### <a name="to-change-the-position-to-a-specific-value"></a>將位置變更為特定值

1. 使用[SetPos](reference/cprogressctrl-class.md#setpos)成員函式，將位置設定為特定值。 必要時，將新位置調整為在範圍內。

通常，進度控制項只用於輸出。 若要取得目前的位置，而不指定新的值，請使用[GetPos](reference/cprogressctrl-class.md#getpos)。

## <a name="see-also"></a>另請參閱

[使用 CProgressCtrl](using-cprogressctrl.md)<br/>
[控制項](controls-mfc.md)
