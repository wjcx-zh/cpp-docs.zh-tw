---
title: 建立狀態列的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: a2301301d0012bd93ffedd0452dec140174402e0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276880"
---
# <a name="methods-of-creating-a-status-bar"></a>建立狀態列的方法

MFC 提供建立狀態列的兩個類別：[CStatusBar](../mfc/reference/cstatusbar-class.md)並[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CStatusBar` 提供的所有功能的通用控制項狀態列，它會自動與互動功能表和工具列，以及處理許多必要的通用控制項設定和結構的資料。不過，產生可執行檔通常會大於使用建立`CStatusBarCtrl`。

`CStatusBarCtrl` 通常會導致較小的可執行檔，並且可能會想要使用`CStatusBarCtrl`如果您不想要整合的 MFC 架構中的 [狀態] 列。 如果您打算使用`CStatusBarCtrl`並整合到 MFC 架構的 [狀態] 列，您必須另花心思將傳達至 MFC 的控制項操作的狀態列。 這項通訊並不困難;不過，就是不必要的當您使用的其他工作`CStatusBar`。

Visual c + + 提供兩種方式可利用通用狀態列。

- 建立使用狀態列`CStatusBar`，然後呼叫[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)以取得存取權`CStatusBarCtrl`成員函式。

- 建立使用狀態列[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的建構函式。

這兩種方法可讓您存取狀態列控制項的成員函式。 當您呼叫 `CStatusBar::GetStatusBarCtrl`時，會傳回 `CStatusBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 請參閱[CStatusBar](../mfc/reference/cstatusbar-class.md)如需有關建構和建立狀態列使用`CStatusBar`。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
