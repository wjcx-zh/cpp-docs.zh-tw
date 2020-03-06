---
title: AnalyzeA
description: C++ BUILD Insights SDK AnalyzeA 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9f5a7b91bf0cd6fd45f97880a99e1f56a85d74ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332912"
---
# <a name="analyzea"></a>AnalyzeA

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalyzeA` 函數可用來分析從 Windows 事件追蹤（ETW）追蹤讀取的 MSVC 事件。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE AnalyzeA(
    const char*                inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>參數

*inputLogFile*\
您想要從中讀取事件的輸入 ETW 追蹤。

*analysisDescriptor*\
[ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)物件的指標。 使用此物件來設定分析。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
