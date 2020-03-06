---
title: MakeDynamicAnalyzerGroup
description: C++ BUILD Insights SDK MakeDynamicAnalyzerGroup 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332828"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicAnalyzerGroup` 函數可用來建立動態分析器群組。 分析器群組的成員會從左至右逐一接收事件，直到分析追蹤中的所有事件為止。

## <a name="syntax"></a>語法

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>參數

*分析器*\
動態分析器群組中所包含之[IAnalyzer](../other-types/ianalyzer-class.md)指標的向量。 這些指標可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。

### <a name="return-value"></a>傳回值

動態分析器群組。 使用**auto**關鍵字來捕捉傳回值。

## <a name="remarks"></a>備註

不同于靜態分析器群組，動態分析器群組的成員在編譯時期不需要知道。 您可以根據程式輸入，或在編譯時期未知的其他值，在執行時間選擇分析器群組成員。 不同于靜態分析器群組，動態分析器群組內的[IAnalyzer](../other-types/ianalyzer-class.md)指標具有多型行為，而且會正確分派虛擬函式呼叫。 這項彈性的代價是，事件處理時間可能較慢。 當所有分析器群組成員都在編譯階段為已知時，如果您不需要多型行為，請考慮使用靜態分析器群組。 若要使用靜態分析器群組，請改為呼叫[MakeStaticAnalyzerGroup](make-static-analyzer-group.md) 。

動態分析器群組可以封裝在靜態分析器群組內。 其做法是將其位址傳遞給[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)。 使用這項技術，將動態分析器群組傳遞至僅接受靜態分析器群組的功能，例如[分析](analyze.md)。

::: moniker-end
