---
title: ANALYSIS_DESCRIPTOR結構
description: C++生成見解 SDK ANALYSIS_DESCRIPTOR結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323618"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`ANALYSIS_DESCRIPTOR`結構與[分析A](../functions/analyze-a.md)[和分析W](../functions/analyze-w.md)函數一起使用。 它描述了如何分析 Windows (ETW) 追蹤的事件追蹤。

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
| `NumberOfPasses` | 應通過ETW跟蹤執行的分析次數。 |
| `Callbacks` | 指定[在](analysis-callbacks-struct.md)分析會話期間調用哪些函數ANALYSIS_CALLBACKS物件。 |
| `Context` | 以參數傳遞給在`Callbacks` |

## <a name="remarks"></a>備註

結構`Callbacks`僅接受指向非成員函數的指標。 您可以通過`Context`設置 到物件指標來繞過此限制。 此物件指標將作為參數傳遞給所有非成員回調函數。 使用此指標可以從非成員回調函數中調用成員函數。

::: moniker-end
