---
title: 在 CStatusBarCtrl 物件中使用工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374700"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 物件中使用工具提示

要啟用狀態列控制件的工具提示,`CStatusBarCtrl`請使用SBT_TOOLTIPS樣式創建物件。

> [!NOTE]
> 如果您是使用 `CStatusBar` 物件實作自己的狀態列，請使用 `CStatusBar::CreateEx` 函式。 它允許您為嵌入`CStatusBarCtrl`物件指定其他樣式。

成功建立`CStatusBarCtrl`物件後,請使用[CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext)和[CStatusBarCtrl::獲取提示文本](../mfc/reference/cstatusbarctrl-class.md#gettiptext)來設置和檢索特定窗格的提示文本。

當工具提示設定時，只有在組件沒有圖示和文字才會顯示，或者無法在組件中顯示所有文字時才顯示。 在簡單模式中不支援工具提示。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
