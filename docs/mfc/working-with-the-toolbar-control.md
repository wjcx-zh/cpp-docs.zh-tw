---
title: 使用工具列控制項
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 60cc527493e2a68751c201b998ab171c564d6c1f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510573"
---
# <a name="working-with-the-toolbar-control"></a>使用工具列控制項

本文說明如何存取[CToolBar](../mfc/reference/ctoolbar-class.md)基礎的[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件, 以更充分掌控您的工具列。 這是一個先進的主題。

## <a name="procedures"></a>程序

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>存取 CToolBar 物件基礎的工具列通用控制項

1. 呼叫[CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。

`GetToolBarCtrl`傳回[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件的參考。 您可以使用參考來呼叫 toolbar 控制項類別的成員函式。

> [!CAUTION]
>  雖然呼叫`CToolBarCtrl` **Get**函式是安全的, 但如果您呼叫**Set**函式, 請謹慎使用。 這是一個先進的主題。 通常您不需要存取基礎工具列控制項。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [控制項 (Windows 通用控制項)](../mfc/controls-mfc.md)

- [工具列基本概念](../mfc/toolbar-fundamentals.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [動態調整工具列大小](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [Flyby 狀態列更新](../mfc/toolbar-tool-tips.md)

- [處理工具提示通知](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [處理自訂通知](../mfc/handling-customization-notifications.md)

- [多個工具列](../mfc/toolbar-fundamentals.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

- [控制列](../mfc/control-bars.md)

如需使用 Windows 通用控制項的一般資訊, 請參閱[通用控制項](/windows/win32/Controls/common-controls-intro)。

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
