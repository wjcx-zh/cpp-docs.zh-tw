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
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369766"
---
# <a name="docking-and-floating-toolbars"></a>停駐和浮動工具列

Microsoft 基礎類庫支援可停靠工具列。 可停靠工具列可以附加或停靠到其父視窗的任何一側,也可以在其自己的迷你框架視窗中分離或浮動。 本文介紹如何在應用程式中使用可停靠工具列。

如果使用應用程式精靈產生應用程式的骨架,系統將要求您選擇是否需要可停靠工具列。 預設情況下,應用程式精靈產生程式碼,這些程式執行在應用程式中放置可停靠工具列所需的三個操作:

- [在框架視窗中開啟停靠](#_core_enabling_docking_in_a_frame_window)。

- [開啟工具列的停靠](#_core_enabling_docking_for_a_toolbar)。

- [停靠工具列(停靠到框架視窗)。](#_core_docking_the_toolbar)

如果缺少這些步驟中的任何一個,則應用程式將顯示一個標準工具列。 必須為應用程式中的每個可停靠工具列執行最後兩個步驟。

本文介紹的其他主題包括:

- [浮動工具列](#_core_floating_the_toolbar)

- [動態調整工具列大小](#_core_dynamically_resizing_the_toolbar)

- [設定固定樣式工具列的換行位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

有關示例,請參閱 MFC 常規示例[DOCKTOOL。](../overview/visual-cpp-samples.md)

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>在框架視窗中開啟停靠

要將工具列停靠到框架視窗,必須啟用框架視窗(或目標)以允許停靠。 這是使用[CFrameWnd::啟用停靠](../mfc/reference/cframewnd-class.md#enabledocking)函數完成的,該函數採用一個*DWORD*參數,該參數是一組樣式位,指示幀視窗的哪一側接受停靠。 如果工具列即將停靠,並且有多個邊可以停靠,則傳遞給的參數中指示的邊`EnableDocking`按以下順序使用:頂部、底部、左側、右側。 如果希望能夠停靠控制欄 **,CBRS_ALIGN_ANY傳遞到**`EnableDocking`。

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>開啟工具列嵌入

準備好停靠目標后,必須以類似方式準備工具列(或源)。 調用[CControlBar:為](../mfc/reference/ccontrolbar-class.md#enabledocking)要停靠的每個工具列啟用停靠,指定工具列應停靠到的目標邊。 如果在調用中指定的任何邊數都`CControlBar::EnableDocking`與框架視窗中啟用的停靠的邊匹配,工具列將無法停靠 - 它將浮動。 浮動後,它仍然是一個浮動工具列,無法停靠到框架視窗。

如果所需的效果是永久浮動工具列,請調用`EnableDocking`參數為 0。 然後呼叫[CFramewnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)。 工具列保持浮動狀態,永久無法停靠到任何位置。

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>停駐工具列

當用戶嘗試將工具列放在允許停靠的幀視窗的一側時,框架將調用[CFrameWnd::DockControlBar。](../mfc/reference/cframewnd-class.md#dockcontrolbar)

此外,您可以隨時調用此功能以將控制條停靠到幀視窗。 這通常在初始化期間完成。 多個工具列可以停靠到框架視窗的特定側。

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>浮動工具列

從框架視窗分離可停靠工具列稱為浮動工具列。 調用[CFramewnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)執行此操作。 指定要浮動的工具列、應放置工具列的點以及確定浮動工具列是水準工具列還是垂直的對齊樣式。

當使用者將工具列拖離其停靠位置並將其拖放到未啟用停靠的位置時,框架將調用此功能。 這可以位於框架視窗內外的任意位置。 與`DockControlBar`,您還可以在初始化期間調用此函數。

可停靠工具列的 MFC 實現不提供某些支援可停靠工具列的應用程式中的擴充功能。 不提供可自定義工具列等功能。

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>動態調整工具列大小

從 Visual C++ 版本 4.0 起,您可以讓應用程式的使用者動態調整浮動工具列的大小。 通常,工具列具有長線性形狀,水平顯示。 但是,您可以更改工具列的方向和形狀。 例如,當使用者將工具列停靠在框架視窗的垂直邊上時,形狀將變為垂直佈局。 還可以將工具列重塑為具有多行按鈕的矩形。

您可以：

- 指定動態大小調整為工具列特徵。

- 將固定大小調整指定為工具列特徵。

要提供此支援,在調用[CToolBar:::創建](../mfc/reference/ctoolbar-class.md#create)成員函數時,有兩種新的工具列樣式可供使用。 其中包括：

- **CBRS_SIZE_DYNAMIC**控制欄是動態的。

- **CBRS_SIZE_FIXED**控制欄已固定。

大小動態樣式允許使用者在工具列浮動時調整其大小,但在停靠工具列時不會調整工具列的大小。 工具列在使用者拖動其邊緣時需要更改形狀的位置"換行"。

大小固定樣式保留工具列的換行狀態,固定按鈕在每個列中的位置。 應用程式的使用者無法更改工具列的形狀。 工具列在指定位置進行換行,例如按鈕之間的分隔符位置。 無論工具列是停靠還是浮動,它都保持此形狀。 效果是具有多列按鈕的固定調色板。

您還可以使用[CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)為工具列上的按鈕返回狀態和樣式。 按鈕的樣式確定按鈕的顯示方式以及按鈕對使用者輸入的回應方式;狀態指示按鈕是否處於包裝狀態。

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>設定固定樣式工具列的換行位置

對於具有大小固定樣式的工具列,請指定工具列將換行的工具列按鈕索引。 以下代碼展示如何在主框架視窗的`OnCreate`重寫中執行此操作:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 常規示例[DOCKTOOL](../overview/visual-cpp-samples.md)演示如何使用類[CControlBar](../mfc/reference/ccontrolbar-class.md)和[CToolBar](../mfc/reference/ctoolbar-class.md)的成員函數來管理工具列的動態佈局。 請參閱檔 EDITBAR。在 DOCKTOOL 中的 CPP。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [工具列基礎知識](../mfc/toolbar-fundamentals.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [使用舊工具列](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
