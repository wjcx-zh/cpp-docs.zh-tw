---
title: 自訂工具列控制項的外觀
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: ddccb5f05152d95377b430d7492ede3c86926e37
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619288"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自訂工具列控制項的外觀

類別 `CToolBarCtrl` 提供許多樣式，會影響 toolbar 物件的外觀（有時也是行為）。 `dwCtrlStyle` `CToolBarCtrl::Create` `CToolBar::CreateEx` 當您第一次建立 toolbar 控制項時，藉由設定（或）成員函式的參數來修改 toolbar 物件。

下列樣式會影響工具列按鈕的「3D」層面和按鈕文字的位置：

- **TBSTYLE_FLAT**建立一個平面工具列，其中工具列和按鈕都是透明的。 按鈕文字會出現在 [按鈕點陣圖] 底下。 使用此樣式時，游標下方的按鈕會自動反白顯示。

- **TBSTYLE_TRANSPARENT**建立透明工具列。 在透明工具列中，工具列是透明的，但按鈕並不是。 按鈕文字會出現在 [按鈕點陣圖] 底下。

- **TBSTYLE_LIST**將按鈕文字放在按鈕點陣圖的右邊。

> [!NOTE]
> 為避免重新繪製問題，應該先設定 [ **TBSTYLE_FLAT** ] 和 [ **TBSTYLE_TRANSPARENT** ] 樣式，才能看到工具列物件。

下列樣式會決定工具列是否允許使用者使用拖放來重新調整工具列物件內的個別按鈕：

- **TBSTYLE_ALTDRAG**可讓使用者在按住 ALT 時拖曳工具列按鈕的位置，藉以變更其位置。 如果未指定此樣式，則在拖曳按鈕時，使用者必須按住 SHIFT 鍵。

    > [!NOTE]
    >  您必須指定**CCS_ADJUSTABLE**樣式，才能拖曳工具列按鈕。

- **TBSTYLE_REGISTERDROP**當滑鼠指標超過工具列按鈕時，產生**TBN_GETOBJECT**通知訊息來要求放置目標物件。

其餘的樣式會影響工具列物件的視覺和非視覺化層面：

- **TBSTYLE_WRAPABLE**建立可具有多行按鈕的工具列。 當工具列變得太窄而無法在同一行包含所有按鈕時，工具列按鈕可以「換行」到下一行。 換行會發生在分隔和 nongroup 界限上。

- **TBSTYLE_CUSTOMERASE**會在處理**WM_ERASEBKGND**訊息時產生**NM_CUSTOMDRAW**通知訊息。

- **TBSTYLE_TOOLTIPS**建立工具提示控制項，應用程式可以使用它來顯示工具列中按鈕的描述性文字。

如需工具列樣式和擴充樣式的完整清單，請參閱[工具列控制項和按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)和[工具列擴充樣式](/windows/win32/Controls/toolbar-extended-styles)（在 Windows SDK 中）。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控制項](controls-mfc.md)
