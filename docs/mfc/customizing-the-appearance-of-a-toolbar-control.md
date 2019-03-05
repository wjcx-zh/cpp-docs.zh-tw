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
ms.openlocfilehash: 8a0db3299ebb54d226edc1434dedbc6a04eb9b00
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302334"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自訂工具列控制項的外觀

類別`CToolBarCtrl`提供許多會影響外觀 （和，有時候，行為） 的工具列物件的樣式。 藉由設定修改工具列物件`dwCtrlStyle`的參數`CToolBarCtrl::Create`(或`CToolBar::CreateEx`) 成員函式，當您第一次建立工具列控制項時。

「 3D 」 方面的工具列按鈕和按鈕文字的位置，則會影響下列樣式：

- **TBSTYLE_FLAT**建立一般的工具列，其中的工具列和按鈕是透明。 按鈕文字會出現在按鈕點陣圖之下。 使用此樣式時，會自動反白顯示游標下的按鈕。

- **TBSTYLE_TRANSPARENT**建立透明的工具列。 在透明的工具列中，工具列是透明，但不是按鈕。 按鈕文字會出現在按鈕點陣圖之下。

- **TBSTYLE_LIST**位置按鈕右邊的按鈕點陣圖的文字。

> [!NOTE]
>  若要防止重新繪製的問題**TBSTYLE_FLAT**並**TBSTYLE_TRANSPARENT**之前工具列物件為可見，就應該設定樣式。

下列樣式會判斷工具列是否允許使用者調整個別的按鈕，在使用拖放功能的工具列物件中的位置，並卸除：

- **TBSTYLE_ALTDRAG**可讓使用者在拖曳時按住 alt 鍵來變更工具列按鈕的位置。 如果未指定此樣式，使用者必須按住 SHIFT 同時拖曳的按鈕。

    > [!NOTE]
    >  **CCS_ADJUSTABLE**必須指定啟用拖曳工具列按鈕的樣式。

- **TBSTYLE_REGISTERDROP**產生**TBN_GETOBJECT**通知訊息來要求卸除目標物件，當滑鼠指標移至工具列按鈕。

其餘的樣式會影響工具列物件的視覺和非視覺化層面：

- **TBSTYLE_WRAPABLE**會建立一個可以有多行按鈕的工具列。 工具列按鈕可以 「 包裝 」 至下一行太窄無法包含在同一行上的所有按鈕的工具列時。 文繞圖就會發生在區隔和行會界限上。

- **TBSTYLE_CUSTOMERASE**產生**NM_CUSTOMDRAW**通知訊息處理時**WM_ERASEBKGND**訊息。

- **TBSTYLE_TOOLTIPS**建立應用程式可以使用工具列中顯示按鈕的描述性文字工具提示控制項。

Toolbar 樣式和延伸的樣式的完整清單，請參閱 <<c0> [ 工具列控制項和按鈕樣式](/windows/desktop/Controls/toolbar-control-and-button-styles)並[工具列延伸樣式](/windows/desktop/Controls/toolbar-extended-styles)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
