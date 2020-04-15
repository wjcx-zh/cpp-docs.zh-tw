---
title: 靜態分析器群組
description: C++生成見解 SDK 使靜態分析器組函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323934"
---
# <a name="makestaticanalyzergroup"></a>靜態分析器群組

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MakeStaticAnalyzerGroup`函數用於創建一個靜態分析器組,該組可以傳遞給[分析或](analyze.md)[重新記錄](relog.md)等函數。 分析器組的成員從左到右逐個接收事件,直到分析跟蹤中的所有事件。

## <a name="syntax"></a>語法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>參數

*TAnalyzerPtrs*\
始終推導此參數。

*分析儀*\
靜態[分析器組中包含的 IAnalyzer](../other-types/ianalyzer-class.md)指標的參數包。 這些指標可以是生的,`std::unique_ptr`也可以`std::shared_ptr`是 。

### <a name="return-value"></a>傳回值

靜態分析器組。 使用**自動**關鍵字捕獲返回值。

## <a name="remarks"></a>備註

與動態分析器組不同,靜態分析器組的成員必須在編譯時知道。 此外,靜態分析器組包含沒有多態行為的[IAnalyzer](../other-types/ianalyzer-class.md)指標。 當使用靜態分析器組分析 Windows (ETW) 追蹤的事件追蹤時`IAnalyzer`,對介面的調用始終解析為分析器組成員直接指向的物件。 這種靈活性的喪失具有更快的事件處理時間的可能性。 如果在編譯時無法知道分析器組的成員,或者在`IAnalyzer`指標上需要多態行為,請考慮使用動態分析器組。 要使用動態分析器組,請改為調用[「動態分析器組](make-static-analyzer-group.md)」。

::: moniker-end
