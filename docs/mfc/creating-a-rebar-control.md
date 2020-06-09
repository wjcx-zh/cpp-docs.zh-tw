---
title: 建立 Rebar 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 6828fa3b47eaa1e29579b09611d85cd68702c332
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617130"
---
# <a name="creating-a-rebar-control"></a>建立 Rebar 控制項

您應該先建立[CReBarCtrl](reference/crebarctrl-class.md)物件，才能看到父物件。 如此可以將繪製發生問題的可能性降到最低。

例如，Rebar 控制項 (用於框架視窗物件) 通常當做工具列控制項的父視窗使用。 因此，Rebar 控制項的父代為框架視窗物件。 由於框架視窗物件是父代，因此父代的 `OnCreate` 成員函式是建立 Rebar 控制項的絕佳位置。

若要使用 `CReBarCtrl` 物件，您通常會執行下列步驟：

### <a name="to-use-a-crebarctrl-object"></a>使用 CReBarCtrl 物件

1. 建立[CReBarCtrl](reference/crebarctrl-class.md)物件。

1. 呼叫[create](reference/crebarctrl-class.md#create)以建立 Windows Rebar 通用控制項，並將其附加至 `CReBarCtrl` 物件，並指定任何想要的樣式。

1. 載入點陣圖（呼叫[CBitmap：： LoadBitmap](reference/cbitmap-class.md#loadbitmap)），以當做 Rebar 控制項物件的背景使用。

1. 建立並初始化 Rebar 控制項中將包含的任何子視窗物件 (工具列、對話方塊控制項等)。

1. 使用要插入之區段的必要資訊，初始化**REBARBANDINFO**結構。

1. 呼叫[InsertBand](reference/crebarctrl-class.md#insertband)將現有的子視窗（例如 `m_wndReToolBar` ）插入新的 Rebar 控制項。 如需將波段插入現有 Rebar 控制項的詳細資訊，請參閱[Rebar 控制項和](rebar-controls-and-bands.md)群組。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](using-crebarctrl.md)<br/>
[控制項](controls-mfc.md)
