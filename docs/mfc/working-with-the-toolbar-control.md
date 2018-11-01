---
title: 使用工具列控制項
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 856f45f4b9c78f5bd7d1a2e712f3fe9acd8004f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652045"
---
# <a name="working-with-the-toolbar-control"></a>使用工具列控制項

這篇文章說明如何存取[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件基礎[CToolBar](../mfc/reference/ctoolbar-class.md)為了進一步控制您的工具列。 這是進階的主題。

## <a name="procedures"></a>程序

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>若要存取基礎 CToolBar 物件工具列通用控制項

1. 呼叫[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。

`GetToolBarCtrl` 傳回的參考[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件。 您可以使用參考来呼叫的工具列控制項類別成員函式。

> [!CAUTION]
>  同時呼叫`CToolBarCtrl`**取得**函式的安全性，如果您呼叫小心**設定**函式。 這是進階的主題。 通常您應該不需要存取基礎的工具列控制項。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [控制項 （Windows 通用控制項）](../mfc/controls-mfc.md)

- [工具列基本概念](../mfc/toolbar-fundamentals.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [動態調整大小的工具列](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [Flyby 狀態列更新](../mfc/toolbar-tool-tips.md)

- [處理工具提示告知](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)並[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [處理自訂告知](../mfc/handling-customization-notifications.md)

- [多個工具列](../mfc/toolbar-fundamentals.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

- [控制列](../mfc/control-bars.md)

如需使用 Windows 通用控制項的一般資訊，請參閱 <<c0> [ 通用控制項](/windows/desktop/Controls/common-controls-intro)。

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)

