---
title: 分析W
description: C++生成見解 SDK 分析W 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 64d68e4c10c0b77c3e6b08b1ec23735e38a377a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324164"
---
# <a name="analyzew"></a>分析W

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`AnalyzeW`函數用於分析從 Windows (ETW) 追蹤的輸入事件追蹤讀取的 MSVC 事件。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>參數

*輸入紀錄檔*\
要從中讀取事件的輸入 ETW 跟蹤。

*剖析描述子*\
指向[ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)物件的指標。 使用此物件配置分析。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
