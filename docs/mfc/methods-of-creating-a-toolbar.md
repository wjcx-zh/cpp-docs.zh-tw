---
title: 建立工具列的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: 5296c0454e035770e196c3d6a4d15291d0c4ca6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612455"
---
# <a name="methods-of-creating-a-toolbar"></a>建立工具列的方法

MFC 提供兩個類別來建立工具列： [CToolBar](../mfc/reference/ctoolbar-class.md)並[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CToolBar` 提供所有工具列通用控制項的功能，也可以處理許多必要的通用控制項設定和結構的資料。不過，產生可執行檔通常會大於使用建立`CToolBarCtrl`。

`CToolBarCtrl` 通常會導致較小的可執行檔，並且可能會想要使用`CToolBarCtrl`如果您不想要整合到 MFC 架構的工具列。 如果您打算使用`CToolBarCtrl`並整合到 MFC 架構的工具列，您必須另花心思將傳達至 MFC 的工具列控制項操作。 這項通訊並不困難;不過，就是不必要的當您使用的其他工作`CToolBar`。

Visual c + + 提供兩種方式可利用工具列通用控制項。

- 建立工具列 using `CToolBar`，然後呼叫[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)以取得存取權`CToolBarCtrl`成員函式。

- 建立工具列 using [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)的建構函式。

這兩種方法可讓您存取工具列控制項的成員函式。 當您呼叫 `CToolBar::GetToolBarCtrl`時，會傳回 `CToolBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 請參閱[CToolBar](../mfc/reference/ctoolbar-class.md)如需有關建構和建立工具列使用`CToolBar`。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

