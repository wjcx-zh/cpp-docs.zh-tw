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
ms.openlocfilehash: 38811be765d4427c4083b8f142b54fb67b9076a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359324"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具列實作

工具列是包含控制的元件的點陣圖影像的控制[列](../mfc/control-bars.md)。 這些圖像可以像按鈕、複選框或單選按鈕一樣。 MFC 提供[CToolbar](../mfc/reference/ctoolbar-class.md)類來管理工具列。

如果啟用它,MFC 工具列的用戶可以將它們停靠到視窗邊緣,或將其「浮動」到應用程式視窗中的任意位置。 MFC 不支援開發環境中的可自定義工具列。

MFC 還支援工具提示:在將滑鼠放在按鈕上時描述工具列按鈕用途的小彈出視窗。 默認情況下,當使用者按下工具列按鈕時,狀態列中將顯示一個狀態字串(如果有)。 您可以啟動「飛過」狀態列更新,以在滑鼠位於按鈕上時顯示狀態字串,而無需按按它。

> [!NOTE]
> 自 MFC 版本 4.0 起,工具列和工具提示使用 Windows 95 和更高版本的功能實現,而不是特定於 MFC 的先前實現。

對於向後相容性,MFC 在`COldToolBar`類 中保留較舊的工具列實現。 MFC 早期版本的文檔`COldToolBar``CToolBar`在下 描述。

通過在「應用程式精靈」中選擇工具列選項,創建程式中的第一個工具列。 您還可以創建其他工具列。

本文介紹了以下內容:

- [工具列按鈕](#_core_toolbar_buttons)

- [停駐和浮動工具列](#_core_docking_and_floating_toolbars)

- [工具列與工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 類別](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具列點陣圖](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>工具列按鈕

工具列中的按鈕與功能表中的項目類似。 這兩種使用者介面物件都會生成命令,程式通過提供處理程式函數來處理這些命令。 通常工具列按鈕複製功能表命令的功能,為相同的功能提供替代使用者介面。 這種重複只需為按鈕和功能表項提供相同的 ID 即可進行排列。

您可以使工具列中的按鈕顯示並顯示為按鈕、複選框或單選按鈕。 有關詳細資訊,請參閱類[CToolBar](../mfc/reference/ctoolbar-class.md)。

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>停駐和浮動工具列

MFC 工具列可以:

- 沿其父視窗的一側保持靜止。

- 由使用者拖動並「停靠」或附加到您指定的父視窗的任何一側或側面。

- 在自己的迷你框架視窗中「浮動」或脫離框架視窗,以便使用者可以將其移動到任何方便的位置。

- 浮動時調整大小。

有關詳細資訊,請參閱文章[停靠與浮動工具列](../mfc/docking-and-floating-toolbars.md)。

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>工具列與工具提示

MFC 工具列也可以顯示「工具提示」 - 包含工具列按鈕用途的簡短文字說明的微小彈出視窗。 當使用者將滑鼠移到工具列按鈕上時,工具提示視窗將彈出以提供提示。 有關詳細資訊,請參閱文章[工具列工具提示](../mfc/toolbar-tool-tips.md)。

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>CToolBar 和 CToolBarCtrl 類別

您可以通過[CToolBar](../mfc/reference/ctoolbar-class.md)類管理應用程式的工具列。 MFC 版本 4.0`CToolBar`起, 已重新實現,以使用 Windows 95 或更高版本下可用的工具列通用控制項以及 Windows NT 版本 3.51 或更高版本。

這種重新實現會導致工具列的 MFC 代碼減少,因為 MFC 利用了作業系統支援。 重新實現還可以提高功能。 您可以使用`CToolBar`成員函數操作工具列,也可以獲取對基礎[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件的引用,並調用其成員函數進行工具列自定義和其他功能。

> [!TIP]
> 如果您已投入大量資金對 的舊 MFC 實現`CToolBar`,則該支援仍然可用。 請參閱[使用舊工具列](../mfc/using-your-old-toolbars.md)的文章。

另請參閱 MFC 一般範例[DOCKTOOL](../overview/visual-cpp-samples.md)。

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>工具列點陣圖

建構後,`CToolBar`物件透過載入單個點陣圖來建立工具列影像,該位圖包含每個按鈕的一個影像。 應用程式精靈建立標準工具列點圖,您可以使用可視化C++[工具列編輯器](../windows/toolbar-editor.md)進行自訂。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [工具列基礎知識](../mfc/toolbar-fundamentals.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

## <a name="see-also"></a>另請參閱

[工具列](../mfc/toolbars.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)
