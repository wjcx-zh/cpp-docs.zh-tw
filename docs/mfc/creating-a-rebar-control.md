---
title: 建立 Rebar 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274446"
---
# <a name="creating-a-rebar-control"></a>建立 Rebar 控制項

[CReBarCtrl](../mfc/reference/crebarctrl-class.md)可見的父物件之前，應該建立物件。 如此可以將繪製發生問題的可能性降到最低。

例如，Rebar 控制項 (用於框架視窗物件) 通常當做工具列控制項的父視窗使用。 因此，Rebar 控制項的父代為框架視窗物件。 由於框架視窗物件是父代，因此父代的 `OnCreate` 成員函式是建立 Rebar 控制項的絕佳位置。

若要使用 `CReBarCtrl` 物件，您通常會執行下列步驟：

### <a name="to-use-a-crebarctrl-object"></a>使用 CReBarCtrl 物件

1. 建構[CReBarCtrl](../mfc/reference/crebarctrl-class.md)物件。

1. 呼叫[Create](../mfc/reference/crebarctrl-class.md#create)建立 Windows rebar 通用控制項，並將其附加至`CReBarCtrl`物件，指定所需的任何樣式。

1. 載入點陣圖，藉由呼叫[cbitmap:: Loadbitmap](../mfc/reference/cbitmap-class.md#loadbitmap)，以當做 rebar 控制項物件的背景。

1. 建立並初始化 Rebar 控制項中將包含的任何子視窗物件 (工具列、對話方塊控制項等)。

1. 初始化**REBARBANDINFO**結構以插入的必要資訊。

1. 呼叫[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)插入現有的子視窗 (例如`m_wndReToolBar`) 插入新的 rebar 控制項。 如需有關如何將群組列插入現有 rebar 控制項的詳細資訊，請參閱 < [Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
