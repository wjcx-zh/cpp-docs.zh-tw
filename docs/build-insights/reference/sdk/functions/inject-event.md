---
title: 注入事件
description: C++生成見解 SDK 注入事件函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324043"
---
# <a name="injectevent"></a>注入事件

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

函數`InjectEvent`在實現[IRelogger](../other-types/irelogger-class.md)介面的重新記錄器中調用。 它用於在重新記錄作業階段的輸出追蹤檔中為 Windows (ETW) 事件編寫事件追蹤。

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

*重新登入工作階段*\
指向重新記錄會話的指標。 為實現`IRelogger`介面的重新記錄提供重新記錄會話。 有關詳細資訊,請參閱[IRelogger](../other-types/irelogger-class.md)。

*提供程式 Id*\
Windows (ETW) 提供程式 GUID 的事件追蹤,根據該追蹤,ETW 事件將重新記錄。

*事件描述子*\
已重新記錄的 ETW 事件的 ETW 事件描述符。

*行程代碼*\
重新記錄的 ETW 事件的程序識別碼 (PID)。

*執行緒 Id*\
已重新記錄的 ETW 事件的線程識別碼 (TID)。

*處理器索引*\
重新記錄的 ETW 事件的處理器索引。

*時間 戳*\
已重新記錄的 ETW 事件的時間戳。

*資料*\
指向應包含在重新記錄的 ETW 事件中的數據的指標。

*位元組計數*\
數據的大小(以位元組為單位)由*資料*指向。

## <a name="remarks"></a>備註

有關 ETW 概念的詳細資訊(如*提供者介面與**事件描述 ),* 請參閱[ETW 文件](/windows/win32/etw/about-event-tracing)。 有關如何使用C++生成見解 SDK 啟動重新紀錄記錄工作階段的詳細資訊,請參閱[Relog](relog.md)。

::: moniker-end
