---
title: 工具列工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373463"
---
# <a name="toolbar-tool-tips"></a>工具列工具提示

工具提示是微小的彈出視窗,當您將滑鼠放在按鈕上一段時間時,該視窗會簡要說明工具列按鈕的用途。 當您使用具有工具列的應用程式嚮導創建應用程式時,會為您提供工具提示支援。 本文介紹了應用程式精靈創建的工具提示支援以及如何向應用程式添加工具提示支援。

本文將說明：

- [工具提示](#_core_activating_tool_tips)

- [飛天狀態列更新](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>工具提示

要啟動應用程式中的工具提示,必須執行以下兩項操作:

- 將CBRS_TOOLTIPS樣式添加到其他樣式(如WS_CHILD、WS_VISIBLE和其他**CBRS_** 樣式),作為*dwStyle*參數傳遞到[CToolBar::創建](../mfc/reference/ctoolbar-class.md#create)函數或[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)中。

- 如下所述,將工具列提示文本(由換行元 (『\n』) 分隔到包含工具列命令的命令列提示符的字串資源。 字串資源分享工具列按鈕的 ID。

#### <a name="to-add-the-tool-tip-text"></a>新增工具提示文字

1. 編輯工具列編輯器中的工具列時,打開給定按鈕的**工具列按鈕屬性**視窗。

1. 在 **「提示」** 框中,指定要顯示在該按鈕的工具提示中的文字。

> [!NOTE]
> 將文字設定為工具列編輯器中的按鈕屬性將替換前一個過程,您必須在其中打開和編輯字串資源。

開啟工具提示的控制列上放置了子控制項,則控制列將顯示控制列上每個子控制元件的工具提示,只要它滿足以下條件:

- 控制項的識別碼不是 - 1。

- 與資源檔中的子控制檔具有相同 ID 的字串表項目具有工具提示字串。

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>飛天狀態列更新

與工具提示相關的功能是「飛天」狀態列更新。 默認情況下,狀態列上的消息僅描述激活按鈕時的特定工具列按鈕。 通過在傳遞給`CToolBar::Create`的樣式清單中包含CBRS_FLYBY,您可以在滑鼠游標通過工具列時更新這些消息,而無需實際啟動按鈕。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [MFC 工具列實現(工具列概述資訊)](../mfc/mfc-toolbar-implementation.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)

- [使用舊工具列](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
