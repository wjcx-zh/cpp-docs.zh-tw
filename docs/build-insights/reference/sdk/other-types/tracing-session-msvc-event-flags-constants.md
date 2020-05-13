---
title: TRACING_SESSION_MSVC_EVENT_FLAGS常量
description: C++生成見解 SDK TRACING_SESSION_MSVC_EVENT_FLAGS常量引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_MSVC_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f7cf94221abc69f2069d02473d2ef1316ee8f0a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323481"
---
# <a name="tracing_session_msvc_event_flags-constants"></a>TRACING_SESSION_MSVC_EVENT_FLAGS常量

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

常`TRACING_SESSION_MSVC_EVENT_FLAGS`量用於描述在跟蹤期間要收集的MSVC事件。 使用它們初始化[TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)結構`MsvcEventFlags`的欄位。

## <a name="syntax"></a>語法

```cpp
static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_BASIC                                = 0x0001ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_FILES                       = 0x0004ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_TEMPLATE_INSTANTIATIONS     = 0x0008ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_BACKEND_FUNCTIONS                    = 0x1000ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_ALL                                  = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成員

| 名稱 | 這個旗標開啟的事件 |
|--|--|
| `TRACING_SESSION_MSVC_EVENT_FLAGS_BASIC` | 此標誌與以下事件相關聯。 默認情況下,C++生成見解 SDK 會啟動它,即使未顯式指定也是如此。 無法禁用這些事件。<br/><br/>[BACK_END_PASSBOTTOM_UP](../event-table.md#back-end-pass) [ ](../event-table.md#bottom-up)<br/>[C1_DLL](../event-table.md#c1-dll)<br/>[C2_DLL](../event-table.md#c2-dll)<br/>[CODE_GENERATION](../event-table.md#code-generation)<br/>[COMMAND_LINE](../event-table.md#command-line)<br/>[編譯 器](../event-table.md#compiler)<br/>[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)<br/>[EXP_OUTPUT](../event-table.md#exp-output)<br/>[FILE_INPUT](../event-table.md#file-input)<br/>[FRONT_END_PASS](../event-table.md#front-end-pass)<br/>[FRONT_END_PASS](../event-table.md#front-end-pass)<br/>[IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)<br/>[LIB_OUTPUT](../event-table.md#lib-output)<br/>[連線](../event-table.md#linker)<br/>[LTCG](../event-table.md#ltcg)<br/>[OBJ_OUTPUT](../event-table.md#obj-output)<br/>[OPT_ICF](../event-table.md#opt-icf)<br/>[OPT_LBR](../event-table.md#opt-lbr)<br/>[OPT_REF](../event-table.md#opt-ref)<br/>[通過1](../event-table.md#pass1)<br/>[PASS2](../event-table.md#pass2)<br/>[PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref)<br/>[執行緒](../event-table.md#thread)<br/>[TOP_DOWN](../event-table.md#top-down)<br/>[WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_FILES` | [FRONT_END_FILE](../event-table.md#front-end-file) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_TEMPLATE_INSTANTIATIONS` | [SYMBOL_NAME](../event-table.md#symbol-name)<br/>[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_BACKEND_FUNCTIONS` | [FORCE_INLINEE](../event-table.md#force-inlinee)<br/>[功能](../event-table.md#function) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_ALL` | 此標誌將打開所有事件。 |

::: moniker-end
