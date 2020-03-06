---
title: SimpleEvent 類別
description: C++ BUILD Insights SDK SimpleEvent 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c30f81236138328322d8c870d4ad69d9988b49a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333045"
---
# <a name="simpleevent-class"></a>SimpleEvent 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`SimpleEvent` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對任何簡單的事件。 請參閱[事件資料表](../event-table.md)，以查看 `SimpleEvent` 類別可以比對的所有事件。

## <a name="syntax"></a>語法

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了來自其[事件](event.md)基類的繼承成員之外，`SimpleEvent` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[SimpleEvent](#simple-event)

## <a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
任何簡單的事件。

::: moniker-end
