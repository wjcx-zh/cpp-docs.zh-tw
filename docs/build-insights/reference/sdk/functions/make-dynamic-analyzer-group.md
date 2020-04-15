---
title: 製作動態分析器群組
description: C++生成見解 SDK 使動態分析器組函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323965"
---
# <a name="makedynamicanalyzergroup"></a>製作動態分析器群組

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MakeDynamicAnalyzerGroup`函數用於創建動態分析器組。 分析器組的成員從左到右逐個接收事件,直到分析跟蹤中的所有事件。

## <a name="syntax"></a>語法

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>參數

*分析儀*\
動態[分析器組中包含的 IAnalyzer](../other-types/ianalyzer-class.md)指標的向量。 這些指標可以是生的,`std::unique_ptr`也可以`std::shared_ptr`是 。

### <a name="return-value"></a>傳回值

動態分析器組。 使用**自動**關鍵字捕獲返回值。

## <a name="remarks"></a>備註

與靜態分析器組不同,動態分析器組的成員不需要在編譯時已知。 您可以根據程式輸入或在執行時根據編譯時未知的其他值選擇分析器組成員。 與靜態分析器組不同,動態分析器組中的[IAnalyzer](../other-types/ianalyzer-class.md)指標具有多態行為,並且虛擬函數調用正確調度。 這種靈活性的代價可能是較慢的事件處理時間。 當所有分析器組成員在編譯時都已知,並且不需要多態行為時,請考慮使用靜態分析器組。 要使用靜態分析器組,請改為除[錯 MakeStaticAnalyzer 群組](make-static-analyzer-group.md)。

動態分析器組可以封裝在靜態分析器組中。 這是透過傳遞其位址[到靜態分析器群組](make-static-analyzer-group.md)。 使用此技術將動態分析器組傳遞給僅接受靜態分析器[群組等函數](analyze.md)。

::: moniker-end
