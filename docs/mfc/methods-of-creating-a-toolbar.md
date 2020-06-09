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
ms.openlocfilehash: b70e6f4dc15023b878bb58d6b7d0739eeb173d53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624257"
---
# <a name="methods-of-creating-a-toolbar"></a>建立工具列的方法

MFC 提供兩個建立工具列的類別： [CToolBar](reference/ctoolbar-class.md)和[CToolBarCtrl](reference/ctoolbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CToolBar`提供工具列通用控制項的所有功能，並為您處理許多必要的通用控制項設定和結構;不過，產生的可執行檔通常會比使用建立的還大 `CToolBarCtrl` 。

`CToolBarCtrl`通常會產生較小的可執行檔， `CToolBarCtrl` 如果您不想要將工具列整合到 MFC 架構中，您可能會想要使用。 如果您打算使用 `CToolBarCtrl` 工具列並將其整合到 mfc 架構中，則必須特別小心將工具列控制項操作傳達給 mfc。 這種通訊並不容易;不過，當您使用時，這是不需要的額外工作 `CToolBar` 。

Visual C++ 提供兩種方式來利用工具列通用控制項。

- 使用建立工具列 `CToolBar` ，然後呼叫[CToolBar：： GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl)以取得成員函式的存取權 `CToolBarCtrl` 。

- 使用[CToolBarCtrl](reference/ctoolbarctrl-class.md)的函式建立工具列。

任一種方法都可讓您存取 toolbar 控制項的成員函式。 當您呼叫 `CToolBar::GetToolBarCtrl`時，會傳回 `CToolBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 如需有關使用來建立工具列的詳細資訊，請參閱[CToolBar](reference/ctoolbar-class.md) `CToolBar` 。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控制項](controls-mfc.md)
