---
title: 事件堆疊類
description: C++生成見解 SDK 事件堆疊類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324972"
---
# <a name="eventstack-class"></a>事件堆疊類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

類`EventStack`是[事件](event.md)物件的集合。 從C++生成見解 SDK 接收的所有事件`EventStack`都以 物件的形式出現。 此堆疊中的最後一個條目是當前正在處理的事件。 最後一個條目之前的條目是當前事件的父層次結構。 有關生成見解C++中使用的事件模型的詳細資訊,請參閱[事件表](../event-table.md)。

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

[事件堆疊](#event-stack)

### <a name="functions"></a>函式

[背面](#back)
[運算子 *](#subscript-operator)
[大小](#size)

## <a name="back"></a><a name="back"></a>返回

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>傳回值

表示堆疊中最後一個條目的[RawEvent](raw-event.md)物件。 事件堆疊中的最後一個條目是觸發的事件。

## <a name="eventstack"></a><a name="event-stack"></a>事件堆疊

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>參數

*資料*\
生成的原始`EventStack`數據。

### <a name="remarks"></a>備註

您通常不需要自己構造`EventStack`物件。 當分析或重新記錄工作階段期間處理事件時,C++生成見解 SDK 會為您提供它們。

## <a name="operator"></a><a name="subscript-operator"></a>運算子*

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>參數

*指數*\
要在事件堆疊中訪問的元素的索引。

### <a name="return-value"></a>傳回值

一個[RawEvent](raw-event.md)物件,表示存儲在事件堆疊中*索引*指示的位置的事件。

## <a name="size"></a><a name="size"></a> 大小

```cpp
size_t Size() const;
```

### <a name="return-value"></a>傳回值

事件堆疊的大小。

::: moniker-end
