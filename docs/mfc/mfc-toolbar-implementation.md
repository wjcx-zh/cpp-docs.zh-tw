---
title: MFC 工具列實作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a95b5460ee28894d087d1896cbbac03cfb509166
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391198"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具列實作

工具列是[控制列](../mfc/control-bars.md)，包含控制項的點陣圖影像。 這些映像的行為可能會像按鈕、 核取方塊或選項按鈕。 MFC 提供類別[CToolbar](../mfc/reference/ctoolbar-class.md)管理工具列。

如果您啟用它，MFC 工具列的使用者可以將它們停駐視窗邊緣，或它們 「 浮動 」 任一處內的應用程式視窗。 MFC 不支援類似的開發環境中的可自訂工具列。

MFC 也支援工具提示： 描述工具列按鈕的用途，當您將滑鼠游標放在按鈕上的小型快顯視窗。 根據預設，當使用者按下工具列按鈕，狀態字串會出現在 [狀態] 列 （如果有的話）。 您可以啟用 「 即時 」 更新為顯示狀態的字串，當滑鼠置於按鈕上方未按下它時的狀態列。

> [!NOTE]
>  根據 MFC 4.0 版，工具列工具提示會實作與使用 Windows 95 和更新版本的功能，而不先前的實作特定 MFC。

回溯相容性，MFC 會保留舊的工具列實作類別中`COldToolBar`。 舊版的 MFC 的文件描述`COldToolBar`下`CToolBar`。

應用程式精靈中選取 [工具列] 選項，在您的程式中建立第一個工具列。 您也可以建立額外的工具列。

下列這篇文章中介紹：

- [工具列按鈕](#_core_toolbar_buttons)

- [停駐和浮動工具列](#_core_docking_and_floating_toolbars)

- [工具列和工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 類別](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具列點陣圖](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> 工具列按鈕

在工具列中的按鈕是類似於功能表中的項目。 這兩種使用者介面物件產生命令，藉由提供處理常式函式會處理您的程式。 通常是工具列按鈕複製的功能表命令，提供相同功能的替代使用者介面的功能。 這類重複資料刪除會排列僅透過指定按鈕和功能表項目相同的識別碼。

您可以讓按鈕，在工具列中的顯示且運作為按鈕、 核取方塊或選項按鈕。 如需詳細資訊，請參閱類別[CToolBar](../mfc/reference/ctoolbar-class.md)。

##  <a name="_core_docking_and_floating_toolbars"></a> 停駐和浮動工具列

MFC 工具列可以：

- 保持為靜態沿著其父視窗的一端。

- 拖曳和 「 停駐 」，或附加，使用者對您指定的父視窗的任何側邊。

- 「 浮動 」，或從框架視窗中，在它自己的迷你框架視窗讓使用者可以移動至任何合適的位置中卸離。

- 調整大小，而浮點數。

如需詳細資訊，請參閱文章[停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)。

##  <a name="_core_toolbars_and_tool_tips"></a> 工具列和工具提示

MFC 工具列也可以設定為要顯示 「 工具提示 」，其中包含工具列按鈕的用途的簡短文字描述的小型快顯視窗。 當使用者移動滑鼠移至工具列按鈕，工具提示視窗隨即顯示，提供提示。 如需詳細資訊，請參閱文章[工具列工具提示](../mfc/toolbar-tool-tips.md)。

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 和 CToolBarCtrl 類別

管理您的應用程式透過類別的工具列[CToolBar](../mfc/reference/ctoolbar-class.md)。 根據 MFC 4.0 版，`CToolBar`具有也實作類似的使用可在 Windows 95 或更新版本，則工具列通用控制項和 Windows NT 3.51 （含） 以後版本。

這項重新實作導致較少的 MFC 程式碼，用於工具列，因為 MFC 使用的作業系統支援。 重新實作也會改善功能。 您可以使用`CToolBar`成員函式來操作工具列，或您可以取得參考基礎[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件，並呼叫其成員函式工具列自訂和其他功能。

> [!TIP]
>  如果您已投入大量資源的較舊的 MFC 實作`CToolBar`，仍會支援。 請參閱文章[使用您舊的工具列](../mfc/using-your-old-toolbars.md)。

另請參閱 MFC 一般範例[DOCKTOOL](../visual-cpp-samples.md)。

##  <a name="_core_the_toolbar_bitmap"></a> 工具列點陣圖

一旦建構好之後，`CToolBar`物件載入單一點陣圖，其中包含每個按鈕的一個映像建立工具列影像。 應用程式精靈 會建立標準工具列點陣圖，您可以自訂 Visual c + +[工具列編輯器](../windows/toolbar-editor.md)。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [工具列基本概念](../mfc/toolbar-fundamentals.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)並[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

## <a name="see-also"></a>另請參閱

[工具列](../mfc/toolbars.md)<br/>
[工具列編輯器](../windows/toolbar-editor.md)

