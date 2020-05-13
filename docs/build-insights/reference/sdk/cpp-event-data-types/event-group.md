---
title: 事件組類
description: C++生成見解 SDK 事件組類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324993"
---
# <a name="eventgroup-class"></a>事件組類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

類`EventGroup`範本是所有組捕獲類的基類。

## <a name="syntax"></a>語法

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>參數

*TActivity*組中包含的活動類型。

## <a name="members"></a>成員

### <a name="functions"></a>函式

[後](#back)
[begin](#begin)
[Front](#front)開始[operator[]](#subscript-operator)
連接前
運算子 * 大小
[Size](#size)[end](#end)

## <a name="back"></a><a name="back"></a>返回

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>傳回值

對組中最後一個活動事件的引用。

## <a name="begin"></a><a name="begin"></a>開始

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>傳回值

指向活動事件組開頭的反覆運算器。

## <a name="end"></a><a name="end"></a>結束

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>傳回值

反覆運算器將一個位置指向活動事件組的末尾。

## <a name="front"></a><a name="front"></a>前面

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>傳回值

對組中第一個活動事件的引用。

## <a name="operator"></a><a name="subscript-operator"></a>運算子*

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>參數

*指數*\
要在活動事件組中訪問的元素的索引。

### <a name="return-value"></a>傳回值

存儲在*索引*指示的位置的事件堆疊中的事件。

## <a name="size"></a><a name="size"></a> 大小

```cpp
size_t Size() const;
```

### <a name="return-value"></a>傳回值

事件組的大小。

::: moniker-end
