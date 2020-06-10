---
title: 管理工具提示控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 61bc35e8b19ba7645736b939acac6cdaa6cb7316
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622416"
---
# <a name="manipulating-the-tool-tip-control"></a>管理工具提示控制項

`CToolTipCtrl` 類別提供一組成員函式，其可以控制 `CToolTipCtrl` 物件和工具提示視窗的各種屬性。

您可以使用[GetDelayTime](reference/ctooltipctrl-class.md#getdelaytime)和[SetDelayTime](reference/ctooltipctrl-class.md#setdelaytime)的呼叫來設定和抓取工具提示視窗的初始、快顯和 reshow 持續時間。

使用下列函式變更工具提示視窗的外觀：

- [GetMargin](reference/ctooltipctrl-class.md#getmargin)和[setmargin:](reference/ctooltipctrl-class.md#setmargin)會抓取並設定工具提示框線與工具提示文字之間的寬度。

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth)和[setmaxtipwidth:](reference/ctooltipctrl-class.md#setmaxtipwidth)會抓取並設定工具提示視窗的最大寬度。

- [GetTipBkColor](reference/ctooltipctrl-class.md#gettipbkcolor)和[settipbkcolor:](reference/ctooltipctrl-class.md#settipbkcolor)會抓取並設定工具提示視窗的背景色彩。

- [GetTipTextColor](reference/ctooltipctrl-class.md#gettiptextcolor)和[settiptextcolor:](reference/ctooltipctrl-class.md#settiptextcolor)會抓取並設定工具提示視窗的文字色彩。

為了讓工具提示控制項可以收到重要訊息的通知 (例如 WM_LBUTTONXXX 訊息)，您必須將訊息轉送至工具提示控制項。 此轉送的最佳方法是在擁有者視窗的函式中呼叫[CToolTipCtrl：： RelayEvent](reference/ctooltipctrl-class.md#relayevent) `PreTranslateMessage` 。 下列範例說明可能的方法 (假設工具提示控制項名為 `m_ToolTip`)：

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

若要立即移除工具提示視窗，請呼叫[Pop](reference/ctooltipctrl-class.md#pop)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](using-ctooltipctrl.md)<br/>
[控制項](controls-mfc.md)
