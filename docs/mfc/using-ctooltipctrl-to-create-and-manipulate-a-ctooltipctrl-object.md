---
title: 使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: b0f008c70eeb43455408e5b0ad302df6b923608e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261202"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件

以下是範例[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)使用量：

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>建立和操作 CToolTipCtrl

1. 建構 `CToolTipCtrl` 物件。

1. 呼叫[Create](../mfc/reference/ctooltipctrl-class.md#create)建立 Windows 的工具提示通用控制項，並將其附加至`CToolTipCtrl`物件。

1. 呼叫[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)向工具提示控制項，註冊工具，以便在游標位於工具上時，會顯示工具提示中所儲存的資訊。

1. 呼叫[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)設定工具提示會維護工具的資訊。

1. 呼叫[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)設定工具的新週框矩形。

1. 呼叫[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)若要測試的點，以判斷其是否在指定之工具的週框矩形內，如果是的話，擷取工具的相關資訊。

1. 呼叫[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount)擷取計數的工具向 工具提示控制項。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
