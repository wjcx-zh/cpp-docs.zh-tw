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
ms.openlocfilehash: b7dbae03b23c26c96aa0db740b749ba728a353d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475604"
---
# <a name="toolbar-tool-tips"></a>工具列工具提示

工具提示會顯示工具列按鈕的用途的簡短描述，當您將滑鼠游標移到按鈕上放一段時間的小型的快顯視窗。 當您建立應用程式有一個工具列應用程式精靈 時，工具提示支援被提供給您。 這篇文章說明這兩個工具提示支援應用程式精靈 」 和 「 如何將工具提示支援新增至您的應用程式所建立的。

本文涵蓋：

- [啟用工具提示](#_core_activating_tool_tips)

- [Flyby 狀態列更新](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> 啟用工具提示

若要啟用應用程式中的工具提示，您必須執行兩件事：

- CBRS_TOOLTIPS 樣式加入其他樣式 (例如 WS_CHILD、 WS_VISIBLE，和其他**CBRS_** 樣式) 做為傳遞*cheaderctrl:: Create*參數[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)函式或[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)。

- 下列程序中所述，將附加工具列的提示文字，以新行字元 ('\n') 分隔包含工具列命令的命令列提示字元的字串資源。 字串資源共用的工具列按鈕的識別碼。

#### <a name="to-add-the-tool-tip-text"></a>若要新增的工具提示文字

1. 您正在編輯工具列編輯器的工具列，開啟**工具列按鈕屬性**指定按鈕的視窗。

1. 在 **提示**方塊中，指定您想要出現在該按鈕的工具提示的文字。

> [!NOTE]
>  設定文字，如按鈕屬性工具列編輯器會取代先前的程序，您必須用來開啟並編輯字串資源。

如果使用啟用的工具提示的控制列置於它的子控制項，將控制列會顯示控制列上的每一個子控制項的工具提示，只要符合下列準則：

- 控制項的 ID 是-1。

- 字串資料表項目具有相同識別碼的資源檔中的子控制項的工具提示字串。

##  <a name="_core_fly_by_status_bar_updates"></a> Flyby 狀態列更新

工具提示的相關功能是 「 flyby"狀態列更新。 根據預設，狀態 列上的訊息會描述特定工具列按鈕，啟動 按鈕時。 藉由在傳遞至樣式的清單中包括 CBRS_FLYBY `CToolBar::Create`，您可以將滑鼠游標經過工具列而不需實際啟用按鈕時，更新這些訊息。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [MFC 工具列實作 （在工具列上的概觀資訊）](../mfc/mfc-toolbar-implementation.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)並[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)

