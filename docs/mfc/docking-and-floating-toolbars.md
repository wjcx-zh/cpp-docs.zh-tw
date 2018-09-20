---
title: 停駐和浮動工具列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95990ef4f1d2b1c6eb4278f645226e57b67e15e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399017"
---
# <a name="docking-and-floating-toolbars"></a>停駐和浮動工具列

Microsoft Foundation 類別程式庫支援可停駐工具列。 可停駐工具列可以連接，或停駐，它的父視窗的任何一側或中斷連結，或浮動，在自己的迷你框架視窗中。 這篇文章說明如何在您的應用程式中使用可停駐工具列。

如果您使用應用程式精靈 來產生您的應用程式的基本架構時，系統會要求您選擇是否要讓可停駐工具列。 根據預設，應用程式精靈 會產生執行三項動作將可停駐工具列放在您的應用程式所需的程式碼：

- [啟用 停駐在框架視窗中](#_core_enabling_docking_in_a_frame_window)。

- [啟用工具列停駐](#_core_enabling_docking_for_a_toolbar)。

- [將工具列停駐 （框架視窗）](#_core_docking_the_toolbar)。

如果遺漏任何這些步驟，您的應用程式會顯示標準 工具列。 必須執行最後兩個步驟，在您的應用程式中的每個可停駐工具列。

本文章涵蓋的其他主題包括：

- [浮動工具列](#_core_floating_the_toolbar)

- [動態調整大小的工具列](#_core_dynamically_resizing_the_toolbar)

- [已修正樣式工具列的設定自動換行位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

請參閱 MFC 一般範例[DOCKTOOL](../visual-cpp-samples.md)的範例。

##  <a name="_core_enabling_docking_in_a_frame_window"></a> 啟用 停駐在框架視窗

若要將工具列停駐在框架視窗，框架視窗 （或目的地） 必須啟用才能允許停駐。 這是使用[CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking)函式，其會採用其中一個*DWORD*樣式的一組參數的位元會指出哪一側的框架視窗接受停駐。 如果工具列是將要停駐，且有多個可能要停駐的側邊，指示中的側邊參數傳遞至`EnableDocking`可依下列順序： 頂端、 底端、 左、 右。 如果您想要停駐控制項列任何位置，則會傳遞**CBRS_ALIGN_ANY**至`EnableDocking`。

##  <a name="_core_enabling_docking_for_a_toolbar"></a> 啟用工具列停駐

您已備妥目的地停駐之後，您必須以類似的方式來準備工具列 （或來源）。 呼叫[CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking)的每個您想要停駐的工具列中，指定目的地邊工具列應該停駐。 如果沒有呼叫中指定的側邊`CControlBar::EnableDocking`符合側邊的停駐在框架視窗啟用，不能停駐工具列，它會浮動。 一旦浮動的話，它會維持浮動工具列，無法停駐在框架視窗。

如果您想要的效果是永久浮動工具列，呼叫`EnableDocking`的參數為 0。 然後呼叫[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)。 工具列會維持浮動狀態，永遠無法停駐任何位置。

##  <a name="_core_docking_the_toolbar"></a> 停駐工具列

這個架構會呼叫[CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar)使用者嘗試卸除的側邊的框架視窗可停駐工具列。

此外，您可以呼叫此函式在框架視窗停駐控制列的任何時間。 這通常是在初始化期間完成。 一個以上的工具列可以固定到特定的邊的框架視窗。

##  <a name="_core_floating_the_toolbar"></a> 浮動工具列

卸離從框架視窗的可停駐工具列，會呼叫 「 浮動工具列 」。 呼叫[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)若要這樣做。 指定要浮動工具列、 點它應放置的位置，以及判斷浮動工具列是否水平或垂直對齊樣式。

當使用者拖曳工具列停駐位置，並將它放在其中停駐未啟用的位置，架構會呼叫此函式。 這可以是任何位置的內部或外部框架視窗。 如同`DockControlBar`，您也可以在初始化期間呼叫此函式。

可停駐工具列的 MFC 實作不提供部分支援可停駐工具列的某些應用程式中的擴充功能。 不會提供可自訂的工具列等功能。

##  <a name="_core_dynamically_resizing_the_toolbar"></a> 動態調整大小的工具列

截至 Visual c + + 4.0 版，您可以讓您的應用程式動態調整大小浮動工具列上的使用者。 一般而言，工具列上有很長的線性的圖形，水平方式顯示。 但是，您可以變更工具列的方向和形狀。 比方說，當使用者在框架視窗垂直側邊的其中一個將工具列停駐，圖形會變更為垂直配置。 它也可調整成的矩形的按鈕的多個資料列的 工具列。

您可以：

- 指定動態調整大小成工具列的特性。

- 指定固定的大小調整成工具列的特性。

若要提供這項支援，有兩個用於呼叫新的工具列樣式[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)成員函式。 包括：

- **CBRS_SIZE_DYNAMIC**控制列是動態的。

- **CBRS_SIZE_FIXED**固定的控制列。

大小動態樣式可讓您調整工具列的大小，雖然它浮動窗格，但只有在停駐時不的使用者。 工具列 「 包裝 」 在需要時變更形狀，隨著使用者拖曳其邊緣。

已修正樣式的大小會保留工具列上，修正每個資料行中的 按鈕位置的自動換行狀態。 您的應用程式使用者無法變更工具列的圖形。 工具列會包裝在指定的位置，例如按鈕之間的分隔符號位置。 它會維護此圖形工具列是否停駐或浮動。 效果是固定的調色盤，具有多個資料行的按鈕。

您也可以使用[CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)傳回您在工具列上的狀態和按鈕樣式。 按鈕的樣式會判斷按鈕的顯示方式，以及它如何回應使用者輸入，該狀態會告訴按鈕是否處於已包裝的狀態。

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> 已修正樣式工具列的設定自動換行位置

針對具有大小固定樣式的工具列中，指定工具列按鈕的工具列會自動換行的索引。 下列程式碼示範如何在您的主框架視窗中執行這項操作`OnCreate`覆寫：

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 一般範例[DOCKTOOL](../visual-cpp-samples.md)示範如何使用類別的成員函式[CControlBar](../mfc/reference/ccontrolbar-class.md)並[CToolBar](../mfc/reference/ctoolbar-class.md)管理動態配置的工具列。 請參閱檔案 EDITBAR。在 DOCKTOOL CPP。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [工具列基本概念](../mfc/toolbar-fundamentals.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [使用舊的工具列](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)

