---
title: 開始使用 C++ 組建見解
description: C++生成見解的高級概述。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325721"
---
# <a name="get-started-with-c-build-insights"></a>開始使用 C++ 組建見解

::: moniker range="<=vs-2017"

C++構建見解工具可在 Visual Studio 2019 中使用。 要查看該版本的文檔,請將本文的可視化工作室**版本**選擇器控制項設置為 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range="vs-2019"

C++構建見解是一個工具的集合,可提高對 Microsoft 可視化C++ (MSVC) 工具鏈的可見性。 這些工具收集有關C++生成的資料,並以可説明您回答常見問題的格式呈現資料,例如:

- 我的生成是否足夠並行化?
- 我應該在預編譯的標頭 (PCH) 中包括哪些內容?
- 是否有特定的瓶頸我應該關注以提高我的生成速度?

該技術的主要組成部分是:

- *vcperf.exe,* 一個命令行實用程式,可用於收集生成的痕跡,
- Windows 效能分析器 (WPA) 延伸,允許您在 WPA 中檢視產生追蹤,以及 WPA 中檢視產生追蹤,以及
- C++構建見解 SDK,這是一個軟體開發工具組,用於創建使用C++生成見解資料的工具。

點選以下連結可快速啟動這些元件:

[教學:vcperf 與 Windows 效能分析器](tutorials/vcperf-and-wpa.md)\
瞭解如何收集C++專案的生成跟蹤,以及如何在WPA中查看它們。

[教學:Windows 性能基礎知識](tutorials/wpa-basics.md)\
發現用於分析生成跟蹤的有用 WPA 提示。

[C++建構](reference/sdk/overview.md)\
C++生成見解 SDK 的概述。

::: moniker-end
