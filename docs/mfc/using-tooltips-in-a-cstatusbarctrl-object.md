---
title: 在 CStatusBarCtrl 物件中使用工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442536"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 物件中使用工具提示

若要啟用狀態列控制項的工具提示，請使用 SBT_TOOLTIPS 樣式建立 `CStatusBarCtrl` 物件。

> [!NOTE]
>  如果您是使用 `CStatusBar` 物件實作自己的狀態列，請使用 `CStatusBar::CreateEx` 函式。 它可讓您指定內嵌 `CStatusBarCtrl` 物件的其他樣式。

成功建立 `CStatusBarCtrl` 物件之後，請使用[CStatusBarCtrl：： SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext)和[CStatusBarCtrl：： GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext)來設定和抓取特定窗格的提示文字。

當工具提示設定時，只有在組件沒有圖示和文字才會顯示，或者無法在組件中顯示所有文字時才顯示。 在簡單模式中不支援工具提示。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
