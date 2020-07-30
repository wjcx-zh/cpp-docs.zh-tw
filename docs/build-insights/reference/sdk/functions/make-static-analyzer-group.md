---
title: MakeStaticAnalyzerGroup
description: C + + Build Insights SDK MakeStaticAnalyzerGroup 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81c5654c78e086af1c33d0791768ceea52575c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224171"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

函式 `MakeStaticAnalyzerGroup` 可用來建立可以傳遞至函式的靜態分析器群組，例如 [`Analyze`](analyze.md) 或 [`Relog`](relog.md) 。 分析器群組的成員會從左至右逐一接收事件，直到分析追蹤中的所有事件為止。

## <a name="syntax"></a>語法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>參數

*TAnalyzerPtrs*\
這個參數一律會推算。

*分析器*\
[`IAnalyzer`](../other-types/ianalyzer-class.md)靜態分析器群組中所包含之指標的參數套件。 這些指標可以是原始、 `std::unique_ptr` 或 `std::shared_ptr` 。

### <a name="return-value"></a>傳回值

靜態分析器群組。 使用 **`auto`** 關鍵字來捕捉傳回值。

## <a name="remarks"></a>備註

不同于動態分析器群組，靜態分析器群組的成員在編譯時期必須是已知的。 此外，靜態分析器群組包含沒有多型 [`IAnalyzer`](../other-types/ianalyzer-class.md) 行為的指標。 使用靜態分析器群組分析 Windows 事件追蹤（ETW）追蹤時，對介面的呼叫 `IAnalyzer` 一律會解析為分析器群組成員直接指向的物件。 這樣的彈性可能會導致事件處理時間更快。 如果在編譯時期無法得知分析器群組的成員，或如果您在指標上需要多型行為 `IAnalyzer` ，請考慮使用動態分析器群組。 若要使用動態分析器群組，請 [`MakeDynamicAnalyzerGroup`](make-static-analyzer-group.md) 改為呼叫。

::: moniker-end
