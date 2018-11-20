---
title: MFC 中的狀態列實作
ms.date: 11/19/2018
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: 521b24646b673159d14e89bd57ea698a7ba73381
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175363"
---
# <a name="status-bar-implementation-in-mfc"></a>MFC 中的狀態列實作

A [CStatusBar](../mfc/reference/cstatusbar-class.md)物件是一種控制列的資料列文字輸出窗格。 輸出窗格通常用來做為訊息列和狀態指示器。 範例包括簡要說明所選取的功能表命令的功能表說明訊息行和顯示狀態的 SCROLL LOCK、 NUM LOCK 和其他索引鍵的指標。

根據 MFC 4.0 版，狀態列會使用類別實作[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)，其可封裝狀態列通用控制項。 回溯相容性，MFC 會保留舊的狀態 列實作類別中`COldStatusBar`。 舊版的 MFC 的文件描述`COldStatusBar`下`CStatusBar`。

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)，成員函式新增到 MFC 4.0 可讓您善加利用狀態列自訂和其他功能的 Windows 通用控制項的支援。 `CStatusBar` 成員函式可讓您大部分的 Windows 通用控制項; 的功能不過，當您呼叫`GetStatusBarCtrl`，您可以提供給您的狀態列更多狀態列的特性。 當您呼叫`GetStatusBarCtrl`，它會傳回參考`CStatusBarCtrl`物件。 您可以使用該參考來操作狀態列控制項。

下圖顯示一個狀態列會顯示數個指標。

![狀態列](../mfc/media/vc37dy1.gif "狀態列") <br/>
狀態列

工具列上，例如狀態列物件內嵌在其父框架視窗中，當建構自動建構的框架視窗。 [狀態] 列中，所有的控制列，例如，會自動終結以及父框架時終結。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [更新狀態列窗格的文字](../mfc/updating-the-text-of-a-status-bar-pane.md)

- MFC 類別[CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [控制列](../mfc/control-bars.md)

- [對話方塊列](../mfc/dialog-bars.md)

- [工具列 （MFC 工具列實作）](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>另請參閱

[狀態列](../mfc/status-bars.md)

