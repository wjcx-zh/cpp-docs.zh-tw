---
title: 簡單事件類
description: C++生成見解 SDK 簡單事件類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 414ff5c1af99acc612384c1ae39f6e12ab051275
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324371"
---
# <a name="simpleevent-class"></a>簡單事件類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`SimpleEvent`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配任何簡單事件。 請參閱[事件表](../event-table.md)`SimpleEvent`以查看 類可以匹配的所有事件。

## <a name="syntax"></a>語法

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了從[其 Event](event.md)基類繼承的`SimpleEvent`成員一起 ,該類還包含以下成員:

### <a name="constructors"></a>建構函式

[簡單事件](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a>簡單事件

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
任何簡單的事件。

::: moniker-end
