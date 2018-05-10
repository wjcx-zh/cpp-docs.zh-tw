---
title: '&lt;thread&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
dev_langs:
- C++
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 1f5f523b19581fe11f01266c90e6b8612da125fc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 運算子

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a> operator&gt;=

判斷某個 `thread::id` 物件是否大於或等於另一個。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

`!(Left < Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="op_gt"></a> operator&gt;

判斷某個 `thread::id` 物件是否大於另一個。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

`Right < Left`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="op_lt_eq"></a> operator&lt;=

判斷某個 `thread::id` 物件是否小於或等於另一個。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

`!(Right < Left)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="op_lt"></a>  operator&lt;

判斷某個 `thread::id` 物件是否小於另一個。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

如果 `Left` 在總排序中位於 `Right` 之前，即為 `true`，否則為 `false`。

### <a name="remarks"></a>備註

運算子會定義所有 `thread::id` 物件的總排序。 這些物件可用來做為關聯容器中的索引鍵。

這個函式不會擲回任何例外狀況。

## <a name="op_neq"></a> operator!=

比較兩個 `thread::id` 物件是否不相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

`!(Left == Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="op_eq_eq"></a> operator==

比較兩個 `thread::id` 物件是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

`Left` 左邊`thread::id`物件。

`Right` 右邊`thread::id`物件。

### <a name="return-value"></a>傳回值

如果這兩個物件代表執行的同一個執行緒，或者這兩個物件都未代表執行的執行緒，即為 `true`，否則為 `false`。

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="op_lt_lt"></a> operator&lt;&lt;

將 `thread::id` 物件的文字表示插入資料流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>參數

`Ostr` A [basic_ostream](../standard-library/basic-ostream-class.md)物件。

`Id` A`thread::id`物件。

### <a name="return-value"></a>傳回值

`Ostr`.

### <a name="remarks"></a>備註

此函式會將 `Id` 插入 `Ostr`。

如果有兩個 `thread::id` 物件要比較是否相等，則這些物件插入的文字表示會一樣。

## <a name="see-also"></a>另請參閱

[\<thread>](../standard-library/thread.md)<br/>
