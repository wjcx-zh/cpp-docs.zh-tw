---
title: EventStack 類別
description: C++ BUILD Insights SDK EventStack 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333402"
---
# <a name="eventstack-class"></a>EventStack 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`EventStack` 類別是[事件](event.md)物件的集合。 從C++ BUILD Insights SDK 收到的所有事件都是以 `EventStack` 物件的形式提供。 此堆疊中的最後一個專案是目前正在處理的事件。 最後一個專案前面的專案是目前事件的父階層。 如需有關在 Build Insights 中C++使用之事件模型的詳細資訊，請參閱[事件資料表](../event-table.md)。

## <a name="syntax"></a>語法

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

[EventStack](#event-stack)

### <a name="functions"></a>Functions

[Back](#back)
[operator []](#subscript-operator)
[大小](#size)

## <a name="back"></a>返回

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>傳回值

[RawEvent](raw-event.md)物件，代表堆疊中的最後一個專案。 事件堆疊中的最後一個專案就是觸發的事件。

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>參數

*資料*\
建立 `EventStack` 的原始資料。

### <a name="remarks"></a>備註

您通常不需要自行建立 `EventStack` 物件。 當在分析或 relogging 會話期間C++處理事件時，BUILD Insights SDK 會提供這些資訊給您。

## <a name="subscript-operator"></a>operator []

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>參數

*索引*\
要在事件堆疊中存取之元素的索引。

### <a name="return-value"></a>傳回值

[RawEvent](raw-event.md)物件，代表儲存在事件堆疊中由*索引*所指示之位置的事件。

## <a name="size"></a>容量

```cpp
size_t Size() const;
```

### <a name="return-value"></a>傳回值

事件堆疊的大小。

::: moniker-end
