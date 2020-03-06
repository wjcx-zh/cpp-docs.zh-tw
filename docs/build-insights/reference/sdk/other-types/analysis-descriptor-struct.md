---
title: ANALYSIS_DESCRIPTOR 結構
description: C++ BUILD Insights SDK ANALYSIS_DESCRIPTOR 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332478"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_DESCRIPTOR` 結構與[AnalyzeA](../functions/analyze-a.md)和[AnalyzeW](../functions/analyze-w.md)函數搭配使用。 其中說明如何分析 Windows 事件追蹤（ETW）追蹤。

## <a name="syntax"></a>語法

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `NumberOfPasses` | 應該透過 ETW 追蹤完成的分析傳遞數目。 |
| `Callbacks` | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)物件，指定要在分析會話期間呼叫的函數。 |
| `Context` | 使用者提供的內容，會當做引數傳遞給在中指定的所有回呼函數 `Callbacks` |

## <a name="remarks"></a>備註

`Callbacks` 結構只接受非成員函式的指標。 您可以藉由將 `Context` 設定為物件指標來規避這項限制。 這個物件指標會當做引數傳遞給您所有的非成員回呼函數。 使用這個指標，從您的非成員回呼函式中呼叫成員函式。

::: moniker-end
