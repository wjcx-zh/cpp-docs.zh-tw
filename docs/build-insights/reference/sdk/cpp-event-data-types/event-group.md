---
title: EventGroup 類別
description: C++ BUILD Insights SDK EventGroup 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333430"
---
# <a name="eventgroup-class"></a>EventGroup 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`EventGroup` 類別範本是所有群組捕捉類別的基類。

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

*TActivity*包含在群組中的活動類型。

## <a name="members"></a>成員

### <a name="functions"></a>Functions

[Back](#back)
[開始](#begin)
[結束](#end)
[Front](#front)
[operator []](#subscript-operator)
[大小](#size)

## <a name="back"></a>返回

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>傳回值

群組中最後一個活動事件的參考。

## <a name="begin"></a>起點

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>傳回值

指向活動事件群組開頭的反覆運算器。

## <a name="end"></a>成品

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>傳回值

反覆運算器，指向活動事件群組結尾之後的一個位置。

## <a name="front"></a>前端

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>傳回值

群組中第一個活動事件的參考。

## <a name="subscript-operator"></a>operator []

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>參數

*索引*\
活動事件群組中要存取之元素的索引。

### <a name="return-value"></a>傳回值

事件堆疊中的事件，儲存于*索引*所指示的位置。

## <a name="size"></a>容量

```cpp
size_t Size() const;
```

### <a name="return-value"></a>傳回值

事件群組的大小。

::: moniker-end
