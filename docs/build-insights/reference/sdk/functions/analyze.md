---
title: 分析
description: C++ BUILD Insights SDK 會分析函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332863"
---
# <a name="analyze"></a>分析

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`Analyze` 函數可用來分析追蹤C++組建時，從 MSVC 取得的 Windows 事件追蹤（ETW）追蹤。 ETW 追蹤中的事件會依序轉送至呼叫者所提供的分析器群組。 此函式支援多階段分析，允許在資料列中多次將事件資料流程轉送至分析器群組。

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

*TAnalyzerGroupMembers*\
這個參數一律會推算。

*inputLogFile*\
您想要從中讀取事件的輸入 ETW 追蹤。

*numberOfPasses*\
要在輸入追蹤上執行的分析傳遞數目。 追蹤會在每一次分析通過時，透過提供的分析器群組來傳遞。

*analyzerGroup*\
用於分析的分析器群組。 呼叫[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)以建立分析器群組。 若要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)取得的動態分析器群組，請先將其位址傳遞給 `MakeStaticAnalyzerGroup`，以將其封裝在靜態分析器群組內。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
