---
title: MakeStaticAnalyzerGroup
description: C++ BUILD Insights SDK MakeStaticAnalyzerGroup 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332814"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticAnalyzerGroup` 函式是用來建立可以傳遞至函式的靜態分析器群組，例如 [[分析](analyze.md)][或 [](relog.md)重新產生]。 分析器群組的成員會從左至右逐一接收事件，直到分析追蹤中的所有事件為止。

## <a name="syntax"></a>語法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>參數

*TAnalyzerPtrs*\
這個參數一律會推算。

*分析器*\
靜態分析器群組中所包含之[IAnalyzer](../other-types/ianalyzer-class.md)指標的參數套件。 這些指標可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。

### <a name="return-value"></a>傳回值

靜態分析器群組。 使用**auto**關鍵字來捕捉傳回值。

## <a name="remarks"></a>備註

不同于動態分析器群組，靜態分析器群組的成員在編譯時期必須是已知的。 此外，靜態分析器群組包含沒有多型行為的[IAnalyzer](../other-types/ianalyzer-class.md)指標。 使用靜態分析器群組分析 Windows 事件追蹤（ETW）追蹤時，`IAnalyzer` 介面的呼叫一律會解析為分析器群組成員直接指向的物件。 這樣的彈性可能會導致事件處理時間更快。 如果在編譯時期無法得知分析器群組的成員，或者您需要 `IAnalyzer` 指標的多型行為，請考慮使用動態分析器群組。 若要使用動態分析器群組，請改為呼叫[MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) 。

::: moniker-end
