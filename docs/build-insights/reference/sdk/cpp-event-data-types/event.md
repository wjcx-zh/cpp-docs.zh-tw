---
title: 事件類別
description: C++ BUILD Insights SDK 事件類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333395"
---
# <a name="event-class"></a>事件類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`Event` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對任何事件。

## <a name="syntax"></a>語法

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

[事件](#entity)

### <a name="functions"></a>Functions

[Data](#data)
[EventId](#event-id)\
[EventInstanceId](#event-instance-id)\
[事件名稱](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="entity"></a>發生

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
任何事件。

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>傳回值

包含在此事件中之額外資料的指標。 如需如何解讀此欄位的詳細資訊，請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>傳回值

識別事件種類的數位。 如需事件識別碼的清單，請參閱[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>傳回值

可唯一識別追蹤內事件的數位。 當分析或 relogging 相同的追蹤多次時，此值不會變更。 使用此值來識別多個分析或 relogging 傳遞相同追蹤中的相同事件。

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>傳回值

ANSI 字串，其中包含[EventId](#event-id)所識別之事件種類的名稱。

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>傳回值

寬字元串，包含[EventId](#event-id)所識別的事件名稱。

## <a name="process-id"></a>進程

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>傳回值

發生事件之進程的識別碼。

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>傳回值

發生事件之邏輯處理器的以零為基底的索引。

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>傳回值

發生事件之執行緒的識別碼。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以這個事件的刻度測量的持續時間時，每秒所要使用的刻度數。

## <a name="timestamp"></a>戳

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>傳回值

如果事件是活動，此函式會傳回活動開始時所捕捉到的滴答值。 針對簡單事件，此函式會傳回事件發生時所捕捉的滴答值。

::: moniker-end
