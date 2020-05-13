---
title: 分析
description: C++生成見解 SDK 分析函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324100"
---
# <a name="analyze"></a>分析

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Analyze`函數用於分析在追蹤C++生成時從MSVC獲取的Windows (ETW)事件追蹤。 ETW 跟蹤中的事件將按順序轉發到呼叫方提供的分析器組。 此功能支援多路分析,允許連續多次將事件流轉發到分析器組。

## <a name="syntax"></a>語法

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>參數

*TAnalyzer 群組成員*\
始終推導此參數。

*輸入紀錄檔*\
要從中讀取事件的輸入 ETW 跟蹤。

*通道數*\
在輸入跟蹤上運行的分析數。 跟蹤通過每個分析傳遞一次通過提供的分析器組。

*分析儀組*\
用於分析的分析器組。 呼叫[MakeStatic 分析器群組](make-static-analyzer-group.md)以建立分析器群組。 要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)獲得的動態分析器組,首先通過將地址`MakeStaticAnalyzerGroup`傳遞給將其封裝在靜態分析器組中。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
