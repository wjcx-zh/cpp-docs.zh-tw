---
title: 教學課程： Windows Performance Analyzer 基本概念
description: 如何在 Windows Performance Analyzer 中完成基本作業的教學課程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f197e7dfd852cd66039f7279f90e42b0cf75fd86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332226"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>教學課程： Windows Performance Analyzer 基本概念

::: moniker range="<=vs-2017"

Visual Studio C++ 2019 中提供 Build Insights 工具。 若要查看該版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

有效率C++地使用 Build Insights 需要一些 Windows Performance ANALYZER （WPA）知識。 本文可協助您熟悉常見的 WPA 作業。 如需如何使用 WPA 的詳細資訊，請參閱[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)檔。

## <a name="change-the-view-mode"></a>變更 view 模式

WPA 提供兩種基本的視圖模式供您探索追蹤：

- 圖形模式和
- 資料表模式。

您可以使用 [視圖] 窗格頂端的 [視圖模式] 圖示，在兩者之間切換：

![在圖表模式和資料表模式之間切換。](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>選取預設值

大部分C++的 BUILD Insights WPA 視圖都有多個預設值，可供您選擇。 您可以使用 [視圖] 窗格頂端的下拉式功能表，選取您想要的預設值：

![選取預設值。](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>放大和縮小

有些組建追蹤很大，因此很難提供詳細資料。 若要放大您感興趣的區域，請以滑鼠右鍵按一下圖形，然後選取 [**縮放**]。 您隨時都可以選擇 [**復原縮放**] 來返回先前的設定。 下圖顯示使用選取專案和**zoom**命令放大圖形區段的範例：

![放大圖形。](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>依不同的資料行分組

您可以自訂追蹤的顯示方式。 按一下 [視圖] 窗格頂端的齒輪圖示，然後在 [組建瀏覽器] 視圖編輯器中重新排列資料行。 在此對話方塊中的黃線上方找到的資料行，就是您的資料列分組依據的欄位。 在黃色的正上方的資料行是特別的：在圖表視圖中，它會顯示在彩色列上。

此圖顯示連結調用的範例橫條圖。 我們使用齒輪圖示開啟 [組建瀏覽器視圖編輯器] 對話方塊。 然後將 [元件] 和 [名稱] 資料行專案拖曳到黃色的上方。 設定會變更以增加詳細資料的層級，以及查看連結器中實際發生的情況：

![放大圖形。](media/wpa-grouping.gif)

## <a name="see-also"></a>另請參閱

[教學課程： vcperf 和 Windows Performance Analyzer](vcperf-and-wpa.md)\
[參考： vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
[參考： Windows Performance Analyzer views](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
