---
title: TRACING_SESSION_OPTIONS 結構
description: 深入瞭解 c + + Build Insights SDK TRACING_SESSION_OPTIONS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f7c53abc14c4862ccb73f94acd2e325eb3d4a6fa
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742771"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

將 `TRACING_SESSION_OPTIONS` [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 或 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 結構初始化時，會使用此結構。 它描述追蹤收集期間要捕捉的事件。

## <a name="syntax"></a>語法

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>成員

| 名稱 | 描述 |
|--|--|
| `SystemEventFlags` | 用來描述要捕捉的系統事件的位元遮罩。 如需詳細資訊，請參閱 [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md)。 |
| `MsvcEventFlags` | 用來描述要捕捉之 MSVC 事件的位元遮罩。 如需詳細資訊，請參閱 [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md)。 |

::: moniker-end
