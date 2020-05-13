---
title: 使用工具列控制項
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365241"
---
# <a name="working-with-the-toolbar-control"></a>使用工具列控制項

本文介紹如何存[取 CToolBar](../mfc/reference/ctoolbar-class.md)基礎的[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件,以便更好地控制工具列。 這是一個高級主題。

## <a name="procedures"></a>程序

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>存取 CToolBar 物件基礎的工具列公共控制項

1. 呼叫[CToolBar:抓取工具列](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。

`GetToolBarCtrl`返回對[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件的引用。 可以使用引用調用工具列控制類類的成員函數。

> [!CAUTION]
> 雖然調用`CToolBarCtrl` **Get**函數是安全的,但如果您調用**Set**函數,請謹慎。 這是一個高級主題。 通常,您不需要訪問基礎工具列控制件。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [控制項(Windows 常見控制項)](../mfc/controls-mfc.md)

- [工具列基礎知識](../mfc/toolbar-fundamentals.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [動態調整工具列大小](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [飛天狀態列更新](../mfc/toolbar-tool-tips.md)

- [處理工具提示通知](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [處理自訂通知](../mfc/handling-customization-notifications.md)

- [多個工具列](../mfc/toolbar-fundamentals.md)

- [使用舊工具列](../mfc/using-your-old-toolbars.md)

- [控制條](../mfc/control-bars.md)

有關使用 Windows 常見控制項的一般資訊,請參閱[常見控制件](/windows/win32/Controls/common-controls-intro)。

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
