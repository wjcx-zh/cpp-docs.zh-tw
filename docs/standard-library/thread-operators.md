---
title: '&lt;thread&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: e7321831b9356fdb9ae5ce147319726def69efc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215565"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 運算子

||||
|-|-|-|
|[operator！ =](#op_neq)|[操作&gt;](#op_gt)|[操作&gt;=](#op_gt_eq)|
|[操作&lt;](#op_lt)|[操作&lt;&lt;](#op_lt_lt)|[操作&lt;=](#op_lt_eq)|
|[operator = =](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

判斷某個 `thread::id` 物件是否大於或等於另一個。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Left < Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

判斷某個 `thread::id` 物件是否大於另一個。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`Right < Left`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

判斷某個 `thread::id` 物件是否小於或等於另一個。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Right < Left)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

判斷某個 `thread::id` 物件是否小於另一個。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

**`true`** 如果*左*在總排序中的*右邊*，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

運算子會定義所有 `thread::id` 物件的總排序。 這些物件可用來做為關聯容器中的索引鍵。

這個函式不會擲回任何例外狀況。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

比較兩個 `thread::id` 物件是否不相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Left == Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

比較兩個 `thread::id` 物件是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*左面*\
左 `thread::id` 物件。

*再*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

**`true`** 如果兩個物件代表相同的執行執行緒，或如果兩個物件都不是執行的執行緒，則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>操作&lt;&lt;

將 `thread::id` 物件的文字表示插入資料流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>參數

*Ostr*\
[basic_ostream](../standard-library/basic-ostream-class.md) 物件。

*號*\
`thread::id` 物件。

### <a name="return-value"></a>傳回值

*Ostr*。

### <a name="remarks"></a>備註

此函式會將*識別碼*插入*Ostr*中。

如果有兩個 `thread::id` 物件要比較是否相等，則這些物件插入的文字表示會一樣。

## <a name="see-also"></a>另請參閱

[\<thread>](../standard-library/thread.md)
