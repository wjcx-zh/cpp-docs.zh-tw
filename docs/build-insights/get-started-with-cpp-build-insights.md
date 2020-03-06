---
title: 開始使用 C++ 組建見解
description: C++組建深入解析的高階總覽。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332003"
---
# <a name="get-started-with-c-build-insights"></a>開始使用 C++ 組建見解

::: moniker range="<=vs-2017"

Visual Studio C++ 2019 中提供 Build Insights 工具。 若要查看該版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights 是一組工具，可讓您更深入瞭解 Microsoft Visual C++ （MSVC）工具鏈。 工具會收集有關您C++組建的資料，並以可協助您回答常見問題的格式呈現，例如：

- 我的組建是否充分平行化？
- 我應該在預先編譯的標頭（PCH）中包含哪些內容？
- 是否有特定的瓶頸需要專注于增加組建速度？

這項技術的主要元件如下：

- *vcperf*，這是一種命令列公用程式，可讓您用來收集組建的追蹤、
- Windows Performance Analyzer （WPA）延伸模組，可讓您在 WPA 中查看組建追蹤，以及
- C++ BUILD insights SDK 是一種軟體發展工具組，可用於建立您自己的C++工具，以取用 Build Insights 資料。

按一下下列連結，即可快速開始使用這些元件：

[教學課程： vcperf 和 Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
瞭解如何收集C++專案的組建追蹤，以及如何在 WPA 中進行查看。

[教學課程： Windows 效能基本概念](tutorials/wpa-basics.md)\
探索有用的 WPA 秘訣來分析您的組建追蹤。

Build Insights SDK\ [ C++ ](reference/sdk/overview.md)
C++ BUILD Insights SDK 的總覽。

::: moniker-end
