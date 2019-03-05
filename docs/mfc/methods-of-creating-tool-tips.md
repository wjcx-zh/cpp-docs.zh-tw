---
title: 建立工具提示的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 2ba935f52f24f62dded3b89df1563454cf7e0335
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276711"
---
# <a name="methods-of-creating-tool-tips"></a>建立工具提示的方法

MFC 提供三種類別來建立和管理工具提示控制項：[CWnd](../mfc/reference/cwnd-class.md)， [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)， [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)並[CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)。 這些類別中的工具提示成員函式包裝 Windows 通用控制項 API。 
  `CToolBarCtrl` 類別和 `CToolTipCtrl` 類別衍生自 `CWnd` 類別。

`CWnd` 提供建立和管理工具提示的四個成員函式：[Enabletooltips&lt; 2](../mfc/reference/cwnd-class.md#enabletooltips)， [Canceltooltips&lt](../mfc/reference/cwnd-class.md#canceltooltips)， [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage)，和[OnToolHitTest](../mfc/reference/cwnd-class.md#ontoolhittest)。 請參閱這些個別成員函式以取得如何實作工具提示的詳細資訊。

如果您建立工具列使用`CToolBarCtrl`，您可以實作該工具列，直接使用下列成員函式的工具提示：[GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips)並[SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips)。 請參閱這些個別成員函式和[處理工具提示通知](../mfc/handling-tool-tip-notifications.md)如需有關如何實作工具提示。


  `CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 一個工具提示控制項可以提供多個工具的資訊。 工具可以是視窗 (例如子視窗或控制項)，或是視窗工作區中應用程式定義的矩形區域。 [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)類別衍生自`CToolTipCtrl`，並提供額外的視覺化樣式和功能。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
