---
title: 使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442214"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件

以下是[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)使用方式的範例：

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>建立和操作 CToolTipCtrl

1. 建構 `CToolTipCtrl` 物件。

1. 呼叫[create](../mfc/reference/ctooltipctrl-class.md#create)以建立 Windows 工具提示通用控制項，並將它附加至 `CToolTipCtrl` 物件。

1. 呼叫[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)以向工具提示控制項註冊工具，如此一來，當游標位於工具上時，就會顯示儲存在工具提示中的資訊。

1. 呼叫[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)以設定工具提示為工具維護的資訊。

1. 呼叫[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)以設定工具的新周框。

1. 呼叫[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)來測試點，以判斷它是否在指定之工具的周框中，如果是的話，則抓取工具的相關資訊。

1. 呼叫[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) ，以取得使用工具提示控制項註冊的工具計數。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
