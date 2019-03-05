---
title: 使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 3242986d66de7d423b8ab744a691ca1904328de8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264205"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件

以下是範例的典型用法[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>若要使用組件中的狀態列控制項

1. 建構 `CStatusBarCtrl` 物件。

1. 呼叫[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)如果您想要設定狀態列控制項的最小高度的繪圖區域。

1. 呼叫[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)設定狀態列控制項的背景色彩。

1. 呼叫[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)設在狀態列控制項，而每個部分的右邊緣的座標中的部分數目。

1. 呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)狀態列控制項的指定部分設定的文字。 已變更，使其在控制項接著接收 WM_PAINT 訊息時，顯示新的文字的控制項部分失效的訊息。

在某些情況下，[狀態] 列只需要顯示一條線的文字。 在此情況下，呼叫以[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 這會將狀態列控制項放 「 簡單 」 模式中，會顯示 單行文字。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
