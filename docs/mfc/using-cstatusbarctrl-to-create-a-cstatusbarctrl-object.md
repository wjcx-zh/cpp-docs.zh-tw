---
title: 使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442390"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件

以下是一般使用[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的範例：

### <a name="to-use-a-status-bar-control-with-parts"></a>若要搭配使用狀態列控制項與元件

1. 建構 `CStatusBarCtrl` 物件。

1. 如果您想要設定狀態列控制項的繪製區域的最小高度，請呼叫[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) 。

1. 呼叫[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)來設定狀態列控制項的背景色彩。

1. 呼叫[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)來設定狀態列控制項中的元件數目，以及每個元件右邊緣的座標。

1. 呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)以設定狀態列控制項的指定部分中的文字。 此訊息會使控制項中已變更的部分失效，使其在控制項下一次收到 WM_PAINT 訊息時顯示新的文字。

在某些情況下，狀態列只需要顯示一行文字。 在此情況下，請呼叫[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 這會將狀態列控制項放入「簡單」模式，以顯示單行文字。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
