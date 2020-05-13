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
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377468"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自訂工具列控制項的外觀

類`CToolBarCtrl`提供了許多樣式,這些樣式會影響工具欄對象的外觀(偶爾也會影響行為)。 在首次創建工具列控制件時,透過`dwCtrlStyle`設定`CToolBarCtrl::Create`(`CToolBar::CreateEx`或) 成員函數的參數來修改工具列物件。

以下樣式會影響工具列按鈕的「3D」方面和按鈕文本的位置:

- **TBSTYLE_FLAT**創建工具列和按鈕都透明的平面工具列。 按鈕文字顯示在按鈕點陣圖下。 使用此樣式時,游標下方的按鈕將自動突出顯示。

- **TBSTYLE_TRANSPARENT**創建透明工具列。 在透明工具列中,工具列是透明的,但按鈕不是。 按鈕文字顯示在按鈕點陣圖下。

- **TBSTYLE_LIST**將按鈕文字放在按鈕位圖的右側。

> [!NOTE]
> 為了防止重新繪製問題,應在工具列物件可見之前設置**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**樣式。

以下樣式決定工具列是否允許使用者使用拖放重新置放工具列物件中的單個按鈕:

- **TBSTYLE_ALTDRAG**允許用戶通過按住 ALT 時拖動工具列按鈕的位置來更改它的位置。 如果未指定此樣式,則用戶必須在拖動按鈕時按住 SHIFT。

    > [!NOTE]
    >  必須指定**CCS_ADJUSTABLE**樣式才能拖動工具列按鈕。

- **TBSTYLE_REGISTERDROP**生成**TBN_GETOBJECT**通知訊息,當滑鼠指標通過工具列按鈕時請求放置目標物件。

其餘樣式會影響工具列物件的可視和非可視方面:

- **TBSTYLE_WRAPABLE**創建可以具有多行按鈕的工具列。 當工具列變得太窄而無法包含同一行上的所有按鈕時,工具列按鈕可以「換行」到下一行。 換行發生在分離和非組邊界上。

- **TBSTYLE_CUSTOMERASE**在**NM_CUSTOMDRAW處理****WM_ERASEBKGND**消息時生成通知消息。

- **TBSTYLE_TOOLTIPS**建立工具提示控制項,應用程式可以使用該控制程式在工具列中顯示按鈕的描述性文本。

有關工具列樣式與擴充樣式的完整清單,請參閱 Windows SDK 中的[工具列控制元件和按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)以及[工具列擴充樣式](/windows/win32/Controls/toolbar-extended-styles)。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
