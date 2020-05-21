---
title: 開始使用 C++ 組建見解
description: C + + Build Insights 的高階總覽。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759221"
---
# <a name="get-started-with-c-build-insights"></a>開始使用 C++ 組建見解

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看該版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range="vs-2019"

C + + Build Insights 是一組工具，可提高 Microsoft Visual C++ （MSVC）工具鏈的可見度。 這些工具會收集 c + + 組建的相關資料，並以可協助您回答常見問題的格式呈現，例如：

- 我的組建是否充分平行化？
- 我應該在預先編譯的標頭（PCH）中包含哪些內容？
- 是否有特定的瓶頸需要專注于增加組建速度？

這項技術的主要元件如下：

- *vcperf*，這是一種命令列公用程式，可讓您用來收集組建的追蹤、
- Windows Performance Analyzer （WPA）延伸模組，可讓您在 WPA 中查看組建追蹤，以及
- c + + Build Insights SDK，這是一種軟體發展工具組，可用於建立您自己的工具，以使用 c + + Build Insights 資料。

## <a name="documentation-sections"></a>檔區段

[教學課程： vcperf 和 Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
瞭解如何收集 c + + 專案的組建追蹤，以及如何在 WPA 中進行查看。

[教學課程： Windows 效能基本概念](tutorials/wpa-basics.md)\
探索有用的 WPA 秘訣來分析您的組建追蹤。

[C + + Build Insights SDK](reference/sdk/overview.md)\
C + + Build Insights SDK 的總覽。

## <a name="articles"></a>文章

如需 c + + Build Insights 的詳細資訊，請參閱官方 c + + 小組 blog 中的文章：

[C + + Build Insights 簡介](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[使用 c + + Build Insights SDK 以程式設計方式分析您的組建](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[使用 c + + Build Insights 尋找組建瓶頸](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[從 c + + Build Insights 使用 PCH 建議的更快速組建](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end
