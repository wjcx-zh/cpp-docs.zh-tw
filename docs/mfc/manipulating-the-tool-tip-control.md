---
title: 管理工具提示控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 336ba8466e1d1eefbd07d35c4856b273faea7537
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377366"
---
# <a name="manipulating-the-tool-tip-control"></a>管理工具提示控制項

`CToolTipCtrl` 類別提供一組成員函式，其可以控制 `CToolTipCtrl` 物件和工具提示視窗的各種屬性。

初始、 快顯和重新顯示期間，可以設定工具提示視窗，並擷取透過呼叫[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)並[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)。

使用下列函式變更工具提示視窗的外觀：

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)並[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)擷取和設定之間的工具提示框線和工具提示文字。

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)並[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)擷取和設定的最大寬度的工具提示 視窗。

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)並[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)擷取和設定背景色彩的工具提示 視窗。

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)並[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)擷取和設定文字色彩的工具提示 視窗。

為了讓工具提示控制項的重要訊息，例如 WM_LBUTTONXXX 訊息，通知您必須將訊息轉送至您的工具提示控制項。 進行這項轉送的最佳方法是呼叫[Relayevent](../mfc/reference/ctooltipctrl-class.md#relayevent)，請在`PreTranslateMessage`主控視窗的函式。 下列範例說明可能的方法 (假設工具提示控制項名為 `m_ToolTip`)：

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

若要立即移除工具提示視窗，請呼叫[快顯](../mfc/reference/ctooltipctrl-class.md#pop)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

