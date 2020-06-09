---
title: 停駐和浮動工具列
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615841"
---
# <a name="docking-and-floating-toolbars"></a>停駐和浮動工具列

MFC 程式庫支援可停駐的工具列。 可停駐的工具列可以附加或停駐在其父視窗的任一端，也可以在其本身的迷你框架視窗中卸離或浮動。 本文說明如何在您的應用程式中使用可停駐的工具列。

如果您使用應用程式精靈來產生應用程式的基本架構，系統會要求您選擇是否要可停駐工具列。 根據預設，應用程式精靈會產生程式碼，以執行在您的應用程式中放置可停駐的工具列所需的三個動作：

- [在框架視窗中啟用](#_core_enabling_docking_in_a_frame_window)停駐。

- [啟用工具列](#_core_enabling_docking_for_a_toolbar)的停駐。

- 停[駐工具列（至框架視窗）](#_core_docking_the_toolbar)。

如果其中有任何步驟遺失，您的應用程式將會顯示標準工具列。 您必須針對應用程式中的每個可停駐工具列執行最後兩個步驟。

本文涵蓋的其他主題包括：

- [浮動工具列](#_core_floating_the_toolbar)

- [動態調整工具列大小](#_core_dynamically_resizing_the_toolbar)

- [設定固定樣式工具列的換行位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

如需範例，請參閱 MFC 一般範例[DOCKTOOL](../overview/visual-cpp-samples.md) 。

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>在框架視窗中啟用停駐

若要將工具列停駐在框架視窗，必須啟用框架視窗（或目的地）以允許停駐。 這是使用[CFrameWnd：： EnableDocking](reference/cframewnd-class.md#enabledocking)函式來完成，此函式採用一個*DWORD*參數，這是一組樣式位，表示框架視窗接受停駐的那一邊。 如果工具列即將停駐，而且有多個可以停駐的邊，則會以下列順序使用傳遞給的參數中所指定的邊 `EnableDocking` ：上、下、左、右。 如果您想要能夠將控制列固定在任何位置，請將**CBRS_ALIGN_ANY**傳遞至 `EnableDocking` 。

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>啟用工具列的停駐

備妥目的地以進行銜接之後，您必須以類似的方式準備工具列（或來源）。 針對您想要停駐的每個工具列呼叫[CControlBar：： EnableDocking](reference/ccontrolbar-class.md#enabledocking) ，並指定工具列應停駐的目的地邊。 如果在呼叫中指定的兩端都 `CControlBar::EnableDocking` 不符合框架視窗中已啟用停駐的邊，則工具列無法固定，它會浮動。 一旦浮動之後，它仍然是浮動的工具列，無法停駐在框架視窗。

如果您想要的效果是永久浮動工具列，請呼叫 `EnableDocking` 參數為0的。 然後呼叫[CFrameWnd：： FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)。 工具列會保持浮動，永久無法在任何位置停駐。

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>停駐工具列

當使用者嘗試將工具列放在允許停駐的框架視窗側邊時，架構會呼叫[CFrameWnd：:D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) 。

此外，您可以隨時呼叫此函式，將控制列固定至框架視窗。 這通常會在初始化期間完成。 一個以上的工具列可以停駐在框架視窗的特定側邊。

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>浮動工具列

從框架視窗卸離可停駐的工具列稱為浮動工具列。 呼叫[CFrameWnd：： FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)來執行此動作。 指定要浮動的工具列、應放置的目標點，以及決定浮動工具列是水準或垂直的對齊樣式。

當使用者將工具列拖放到停駐的位置，並將它放置在未啟用停駐的位置時，架構會呼叫這個函式。 這可以是框架視窗內部或外部的任何位置。 如同 `DockControlBar` ，您也可以在初始化期間呼叫此函式。

可停駐工具列的 MFC 執行並不會提供某些在某些應用程式中支援可停駐工具列的延伸功能。 不提供可自訂的工具列等功能。

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>動態調整工具列大小

從 Visual C++ 版本4.0，您可以讓應用程式的使用者以動態方式調整浮動工具列的大小。 工具列通常會有一個長線性圖形，以水準方式顯示。 但您可以變更工具列的方向和其形狀。 例如，當使用者將工具列停駐在框架視窗的其中一個垂直邊時，圖形就會變成垂直版面配置。 您也可以使用按鈕的多個資料列，將工具列重新調整成一個矩形。

您可以：

- 將動態調整大小指定為工具列特性。

- 將 [固定大小] 指定為工具列特性。

若要提供這項支援，您可以在對[CToolBar：： Create](reference/ctoolbar-class.md#create)成員函式的呼叫中使用兩個新的工具列樣式。 其中包括：

- **CBRS_SIZE_DYNAMIC**控制列是動態的。

- **CBRS_SIZE_FIXED**控制列已修正。

動態樣式大小可讓您的使用者在工具列浮動時調整其大小，而不是停駐。 工具列會「換行」，需要在使用者拖曳其邊緣時變更形狀。

大小固定樣式會保留工具列的換行狀態，並修正每個資料行中按鈕的位置。 您應用程式的使用者無法變更工具列的形狀。 工具列會在指定的位置（例如按鈕之間的分隔符號位置）換行。 無論工具列為停駐或浮動，它都會維護此圖形。 效果是具有多個按鈕資料行的固定色板。

您也可以使用[CToolBar：： GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle)來傳回工具列上按鈕的狀態和樣式。 按鈕的樣式會決定按鈕的顯示方式，以及它如何回應使用者輸入;狀態會指出按鈕是否處於已包裝的狀態。

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>設定固定樣式工具列的換行位置

針對具有大小固定樣式的工具列，指定工具列要包裝的工具列按鈕索引。 下列程式碼顯示如何在主框架視窗的覆寫中執行此動作 `OnCreate` ：

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 一般範例[DOCKTOOL](../overview/visual-cpp-samples.md)顯示如何使用[CControlBar](reference/ccontrolbar-class.md)和[CToolBar](reference/ctoolbar-class.md)類別的成員函式來管理工具列的動態配置。 請參閱檔案 EDITBAR。DOCKTOOL 中的 CPP。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [工具列基本概念](toolbar-fundamentals.md)

- [工具列工具提示](toolbar-tool-tips.md)

- [使用舊的工具列](using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](mfc-toolbar-implementation.md)
