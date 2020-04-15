---
title: 教學:Windows 效能分析器基礎知識
description: 有關如何在 Windows 性能分析器中完成基本操作的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323409"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>教學:Windows 效能分析器基礎知識

::: moniker range="<=vs-2017"

C++構建見解工具可在 Visual Studio 2019 中使用。 要查看此版本的文檔,請將本文的可視化工作室**版本**選擇器控制項設定為 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range="vs-2019"

有效地使用C++生成見解需要瞭解Windows性能分析器 (WPA)。 本文可説明您熟悉常見的 WPA 操作。 有關如何使用 WPA 的詳細資訊,請參閱 Windows[性能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)文件。

## <a name="change-the-view-mode"></a>變更檢視模式

WPA 提供兩種基本檢視模式,可供您探索您的追蹤:

- 圖形模式,和
- 表模式。

您可以使用視窗格頂端的檢視模式圖示在它們之間切換:

![在圖形模式和表模式之間切換。](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>選擇預設

大多數C++生成見解 WPA 檢視有多個預設供您選擇。 您可以使用視窗中頂端的下拉選單選擇所需的預設:

![選擇預設。](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>放大和縮小

有些生成痕跡太大,很難找出細節。 要放大您感興趣的區域,請右鍵按一下圖形並選擇 **「縮放**」 。 通過選擇 **「撤銷縮放」 ,** 您始終可以傳回以前的設定。 此影像顯示使用所選取內容和**縮放**指令放大圖形部分的範例:

![放大圖形。](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>依不同欄位組

您可以自定義追蹤的顯示方式。 按按下檢視窗格頂部的齒輪圖示,然後重新排列生成資源管理器檢視編輯器中的列。 在此對話框中黃線上方找到的列是數據列分組的列。 黃線上方的列是特殊的:在圖形視圖中,它顯示在彩色條上。

此圖像顯示連結呼叫的範例條形圖。 我們使用齒輪圖示打開"生成資源管理器視圖編輯器"對話方塊。 然後,我們將"元件"和"名稱"列條目拖動到黃線上方。 變更設定以提高詳細等級,並查看連結器內實際發生的情況:

![放大圖形。](media/wpa-grouping.gif)

## <a name="see-also"></a>另請參閱

[教學:vcperf 與 Windows 效能分析器](vcperf-and-wpa.md)\
[參考: vcperf 指令](/cpp/build-insights/reference/vcperf-commands)\
[參考:Windows 效能分析器檢視](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
