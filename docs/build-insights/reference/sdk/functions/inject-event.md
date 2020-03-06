---
title: InjectEvent
description: C++ BUILD Insights SDK InjectEvent 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332842"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`InjectEvent` 函式會在執行[IRelogger](../other-types/irelogger-class.md)介面的 relogger 內呼叫。 它是用來在 relogging 會話的輸出追蹤檔案中寫入 Windows 事件追蹤（ETW）事件。

## <a name="syntax"></a>語法

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>參數

*relogSession*\
Relogging 會話的指標。 Relogging 會話會提供給執行 `IRelogger` 介面的 reloggers。 如需詳細資訊，請參閱[IRelogger](../other-types/irelogger-class.md)。

*providerId*\
適用于 Windows （ETW）提供者 GUID 的事件追蹤（ETW 事件會在其下取得 relogged）。

*eventDescriptor*\
Relogged 之 ETW 事件的 ETW 事件描述元。

*processId*\
Relogged 之 ETW 事件的處理序識別碼（PID）。

*threadId*\
Relogged 之 ETW 事件的執行緒識別碼（TID）。

*processorIndex*\
Relogged 之 ETW 事件的處理器索引。

*時間戳記*\
Relogged 之 ETW 事件的時間戳記。

*資料*\
應該包含在 relogged ETW 事件中的資料指標。

*byteCount*\
資料所指向的資料大小（以位元組為單位） *。*

## <a name="remarks"></a>備註

如需 ETW 概念的詳細資訊，例如*提供者 GUID*和*事件描述*元，請參閱[etw 檔](/windows/win32/etw/about-event-tracing)。 如需如何使用C++ BUILD Insights SDK 來啟動 relogging 會話的詳細資訊，請[參閱重新](relog.md)檢查。

::: moniker-end
