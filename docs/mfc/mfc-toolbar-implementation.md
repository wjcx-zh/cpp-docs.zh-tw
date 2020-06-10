---
title: MFC 工具列實作
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 7876e9403389c19a24e5a482534d0f223eaa4bf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626118"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具列實作

工具列是一種[控制](control-bars.md)列，其中包含控制項的點陣圖影像。 這些影像的行為可以像是按鈕、核取方塊或選項按鈕。 MFC 提供類別[CToolbar](reference/ctoolbar-class.md)來管理工具列。

如果您啟用它，MFC 工具列的使用者可以將它們固定到視窗邊緣，或在應用程式視窗內的任何位置「浮動」。 MFC 不支援像是開發環境中的自訂工具列。

MFC 也支援工具提示：當您將滑鼠置於按鈕上方時，用來描述工具列按鈕用途的小型快顯視窗。 根據預設，當使用者按下工具列按鈕時，狀態列中會出現狀態字串（如果有的話）。 您可以啟用「即時」狀態列更新，以在滑鼠停留在按鈕上時顯示狀態字串，而不需要按它。

> [!NOTE]
> 從 MFC 版本4.0，工具列和工具提示會使用 Windows 95 和更新版本的功能來執行，而不是 MFC 特有的先前的執行。

為了回溯相容性，MFC 會在類別中保留較舊的工具列執行 `COldToolBar` 。 舊版 MFC 的檔描述于 `COldToolBar` 之下 `CToolBar` 。

選取應用程式精靈中的 [工具列] 選項，以在程式中建立第一個工具列。 您也可以建立其他工具列。

本文會引進下列內容：

- [工具列按鈕](#_core_toolbar_buttons)

- [停駐和浮動工具列](#_core_docking_and_floating_toolbars)

- [工具列和工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 類別](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具列點陣圖](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>工具列按鈕

工具列中的按鈕類似于功能表中的專案。 這兩種類型的使用者介面物件都會產生命令，而您的程式會藉由提供處理常式函式來處理。 工具列按鈕通常會複製功能表命令的功能，並為相同的功能提供替代的使用者介面。 這類重複的相片順序是將按鈕和功能表項目相同的識別碼提供給您。

您可以讓工具列中的按鈕出現，並做為按鈕、核取方塊或選項按鈕的行為。 如需詳細資訊，請參閱類別[CToolBar](reference/ctoolbar-class.md)。

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>停駐和浮動工具列

MFC 工具列可以：

- 維持在其父視窗的一邊。

- 由使用者拖曳並「停駐」或附加至您所指定之父視窗的任一側邊或側邊。

- 在它自己的迷你框架視窗中「浮動」或卸離框架視窗，讓使用者可以將它移到任何方便的位置。

- 浮動時調整大小。

如需詳細資訊，請參閱[銜接和浮動工具列](docking-and-floating-toolbars.md)一文。

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>工具列和工具提示

MFC 工具列也可以顯示「工具提示」-小型的快顯視窗，其中包含工具列按鈕用途的簡短文字描述。 當使用者將滑鼠移到工具列按鈕上方時，工具提示視窗會彈出以提供提示。 如需詳細資訊，請參閱[工具列工具提示](toolbar-tool-tips.md)一文。

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>CToolBar 和 CToolBarCtrl 類別

您可以透過 [類別[CToolBar](reference/ctoolbar-class.md)] 來管理應用程式的工具列。 從 MFC 4.0 版起， `CToolBar` 已根據重新實作為使用 windows 95 或更新版本以及 WINDOWS NT 3.51 版或更新版本所提供的工具列通用控制項。

這個重新實作會導致工具列的 MFC 程式碼較少，因為 MFC 會使用作業系統支援。 重新實作也改善了功能。 您可以使用 `CToolBar` 成員函式來操作工具列，或者可以取得基礎[CToolBarCtrl](reference/ctoolbarctrl-class.md)物件的參考，並呼叫其成員函式以進行工具列自訂和其他功能。

> [!TIP]
> 如果您在的舊版 MFC 執行中投入大量投資 `CToolBar` ，仍然可以使用該支援。 請參閱[使用舊的工具列](using-your-old-toolbars.md)一文。

另請參閱 MFC 一般範例[DOCKTOOL](../overview/visual-cpp-samples.md)。

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>工具列點陣圖

在結構化之後， `CToolBar` 物件會藉由載入單一點陣圖（其中每個按鈕包含一個影像）來建立工具列影像。 應用程式精靈會建立標準工具列點陣圖，您可以使用 [Visual C++[工具列編輯器](../windows/toolbar-editor.md)] 進行自訂。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [工具列基本概念](toolbar-fundamentals.md)

- [停駐和浮動工具列](docking-and-floating-toolbars.md)

- [工具列工具提示](toolbar-tool-tips.md)

- [使用工具列控制項](working-with-the-toolbar-control.md)

- [使用舊的工具列](using-your-old-toolbars.md)

- [CToolBar](reference/ctoolbar-class.md)和[CToolBarCtrl](reference/ctoolbarctrl-class.md)類別

## <a name="see-also"></a>另請參閱

[工具列](toolbars.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)
