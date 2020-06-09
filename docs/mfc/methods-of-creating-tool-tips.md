---
title: 建立工具提示的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 26f31705068df009e906d50451efa9ea6572d7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625448"
---
# <a name="methods-of-creating-tool-tips"></a>建立工具提示的方法

MFC 提供三個類別來建立和管理工具提示控制項： [CWnd](reference/cwnd-class.md)、 [CToolBarCtrl](reference/ctoolbarctrl-class.md)、 [CToolTipCtrl](reference/ctooltipctrl-class.md)和[CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md)。 這些類別中的工具提示成員函式包裝 Windows 通用控制項 API。 `CToolBarCtrl` 類別和 `CToolTipCtrl` 類別衍生自 `CWnd` 類別。

`CWnd`提供四個成員函式來建立和管理工具提示： [EnableToolTips](reference/cwnd-class.md#enabletooltips)、 [CancelToolTips](reference/cwnd-class.md#canceltooltips)、 [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)和[OnToolHitTest](reference/cwnd-class.md#ontoolhittest)。 請參閱這些個別成員函式以取得如何實作工具提示的詳細資訊。

如果您使用建立工具列 `CToolBarCtrl` ，您可以使用下列成員函式，直接為該工具列執行工具提示： [GetToolTips](reference/ctoolbarctrl-class.md#gettooltips)和[SetToolTips](reference/ctoolbarctrl-class.md#settooltips)。 如需如何執行工具提示的詳細資訊，請參閱這些個別成員函式和[處理工具提示通知](handling-tool-tip-notifications.md)。

`CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 一個工具提示控制項可以提供多個工具的資訊。 工具可以是視窗 (例如子視窗或控制項)，或是視窗工作區中應用程式定義的矩形區域。 [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md)類別衍生自 `CToolTipCtrl` ，並提供其他視覺化樣式和功能。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](using-ctooltipctrl.md)<br/>
[控制項](controls-mfc.md)
