---
title: RELOG_DESCRIPTOR結構
description: C++生成見解 SDK RELOG_DESCRIPTOR結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328944"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`RELOG_DESCRIPTOR`結構與[RelogA](../functions/relog-a.md)和[RelogW](../functions/relog-w.md)函數一起使用。 它描述了如何重新記錄 Windows (ETW) 追蹤的事件追蹤。

## <a name="syntax"></a>語法

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | 在重新記錄會話的分析階段,應在 ETW 跟蹤上執行的分析通過數。 |
| `AnalysisCallbacks` | [指定](analysis-callbacks-struct.md)在重新記錄會話分析階段調用哪些函數ANALYSIS_CALLBACKS物件。 |
| `RelogCallbacks` | 指定[在](relog-callbacks-struct.md)重新記錄作業階段的重新記錄階段調用哪些函數RELOG_CALLBACKS物件。 |
| `SystemEventsRetentionFlags` | 指定要在重新記錄的追蹤中保留哪些系統 ETW 事件的[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)位掩碼。 |
| `AnalysisContext` | 以參數傳遞給在中指定的所有回檔函數的使用者提供的上下文`AnalysisCallbacks` |
| `RelogContext` | 以參數傳遞給在中指定的所有回檔函數的使用者提供的上下文`RelogCallbacks` |

## <a name="remarks"></a>備註

在重新記錄工作階段期間重新記錄ETW事件由用戶通過中`RelogCallbacks`指定的回調功能進行控制。 但是,系統 ETW 事件(如 CPU 樣本)不會轉發到這些回調函數。 使用該`SystemEventsRetentionFlags`欄位控制系統 ETW 事件的重新記錄記錄。

`AnalysisCallbacks`和`RelogCallbacks`結構僅接受指向非成員函數的指標。 通過將此限制設置為物件指標,可以繞過此限制。 此物件指標將作為參數傳遞給所有非成員回調函數。 使用此指標可以從非成員回調函數中調用成員函數。

重新記錄會話的分析階段始終在重新記錄階段之前執行。

::: moniker-end
