---
title: 事件類別
description: C++生成見解 SDK 事件類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324970"
---
# <a name="event-class"></a>事件類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Event`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配任何事件。

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

### <a name="functions"></a>函式

[資料](#data)
[事件 Id](#event-id)\
[事件實例 Id](#event-instance-id)\
[事件名稱](#event-name)\
[事件寬名稱](#event-wide-name)\
[行程代碼](#process-id)\
[處理器索引](#processor-index)\
[執行緒 Id](#thread-id)\
[滴答頻率](#tick-frequency)\
[時間 戳](#timestamp)

## <a name="event"></a><a name="entity"></a> 事件

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
任何事件。

## <a name="data"></a><a name="data"></a>資料

```cpp
const void* Data() const;
```

### <a name="return-value"></a>傳回值

指向此事件中包含的額外數據的指標。 有關如何解釋此欄位的詳細資訊,請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="eventid"></a><a name="event-id"></a>事件 Id

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>傳回值

標識事件類型的數位。 有關事件識別碼的清單,請參閱[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>事件實例 Id

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>傳回值

唯一標識跟蹤內事件的數位。 多次分析或重新記錄同一跟蹤時,此值不會更改。 使用此值可識別多個分析或重新記錄通過同一跟蹤中的同一事件。

## <a name="eventname"></a><a name="event-name"></a>事件名稱

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>傳回值

包含[事件 Id](#event-id)識別的事件類型名稱的 ANSI 字串。

## <a name="eventwidename"></a><a name="event-wide-name"></a>事件寬名稱

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>傳回值

包含[EventId](#event-id)識別的事件名稱的寬字串。

## <a name="processid"></a><a name="process-id"></a>行程代碼

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>傳回值

事件發生的進程的標識碼。

## <a name="processorindex"></a><a name="processor-index"></a>處理器索引

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>傳回值

事件發生的邏輯處理器的零基索引。

## <a name="threadid"></a><a name="thread-id"></a>執行緒 Id

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>傳回值

發生事件的線程的標識符。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答頻率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以此事件的刻度為單位的持續時間時,每秒使用的刻度數。

## <a name="timestamp"></a><a name="timestamp"></a>時間 戳

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>傳回值

如果事件是活動,則此函數將返回在活動啟動時捕獲的刻度值。 對於簡單事件,此函數返回事件發生時捕獲的刻度值。

::: moniker-end
