---
title: 教學課程： Windows Performance Analyzer 基本概念
description: 如何在 Windows Performance Analyzer 中完成基本作業的教學課程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4473e3682a6e00e0eef61cb73d7450976bcc0c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507729"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>教學課程： Windows Performance Analyzer 基本概念

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看此版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range="vs-2019"

使用 c + + Build Insights 實際上需要 Windows Performance Analyzer (WPA) 的知識。 本文可協助您熟悉常見的 WPA 作業。 如需有關如何使用 WPA 的詳細資訊，請參閱 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 檔。

## <a name="change-the-view-mode"></a>變更視圖模式

WPA 提供兩種基本的視圖模式，讓您探索追蹤：

- 圖形模式和
- 資料表模式。

您可以使用 [view] 窗格頂端的視圖模式圖示來切換它們：

![在圖形模式和資料表模式之間切換。](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>選取預設值

大部分的 c + + Build Insights WPA 視圖都有多個預設值，可供您選擇。 您可以使用 [view] 窗格頂端的下拉式功能表來選取您想要的預設值：

![選取預設值。](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>放大和縮小

某些組建追蹤很大，因此難以提供詳細資料。 若要放大您感興趣的區域，請在圖表上按一下滑鼠右鍵，然後選取 [ **縮放**]。 您一律可以選擇 [ **復原縮放**]，回到先前的設定。 此圖顯示使用選取專案和 **zoom** 命令來放大圖表區段的範例：

![顯示圖形上放大的短片。](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>依不同的資料行分組

您可以自訂追蹤的顯示方式。 按一下 [視圖] 窗格頂端的齒輪圖示，然後在 [Build Explorer 視圖編輯器] 中重新排列資料行。 在此對話方塊的黃色線上方找到的資料行，就是您的資料列分組依據的資料行。 黃色直線上方的資料行很特殊：在圖形視圖中，它會顯示在彩色橫條上。

此影像顯示連結調用的範例橫條圖。 我們使用齒輪圖示來開啟 [組建 Explorer 視圖編輯器] 對話方塊。 然後，將 [元件] 和 [名稱] 資料行專案拖曳到黃色線上方。 設定會變更以增加詳細資料層級，並查看連結器中實際發生的情況：

![顯示如何以不同資料行分組的短片。](media/wpa-grouping.gif)

## <a name="see-also"></a>另請參閱

[教學課程： vcperf 和 Windows Performance Analyzer](vcperf-and-wpa.md)\
[參考： vcperf 命令](../reference/vcperf-commands.md)\
[參考： Windows Performance Analyzer 視圖](../reference/wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
