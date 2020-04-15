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
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375825"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 運算子

||||
|-|-|-|
|[操作員!](#op_neq)|[算子&gt;](#op_gt)|[算子&gt;=](#op_gt_eq)|
|[算子&lt;](#op_lt)|[算子&lt;&lt;](#op_lt_lt)|[算子&lt;=](#op_lt_eq)|
|[運算子*](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>算子&gt;=

判斷某個 `thread::id` 物件是否大於或等於另一個。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Left < Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorgt"></a><a name="op_gt"></a>算子&gt;

判斷某個 `thread::id` 物件是否大於另一個。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`Right < Left`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>算子&lt;=

判斷某個 `thread::id` 物件是否小於或等於另一個。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Right < Left)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorlt"></a><a name="op_lt"></a>算子&lt;

判斷某個 `thread::id` 物件是否小於另一個。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

如果 *「左」* 在總排序中位於*右側*,**則為 true;** 否則,**假**。

### <a name="remarks"></a>備註

運算子會定義所有 `thread::id` 物件的總排序。 這些物件可用來做為關聯容器中的索引鍵。

這個函式不會擲回任何例外狀況。

## <a name="operator"></a><a name="op_neq"></a>操作員!

比較兩個 `thread::id` 物件是否不相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

`!(Left == Right)`

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operator"></a><a name="op_eq_eq"></a>運算子*

比較兩個 `thread::id` 物件是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>參數

*離開*\
左 `thread::id` 物件。

*對*\
右 `thread::id` 物件。

### <a name="return-value"></a>傳回值

如果兩個物件表示相同的執行線程,或者兩個物件都不表示執行線程,**則為 true;** 否則,**假**。

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>算子&lt;&lt;

將 `thread::id` 物件的文字表示插入資料流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>參數

*奧斯特*\
[basic_ostream](../standard-library/basic-ostream-class.md) 物件。

*Id*\
`thread::id` 物件。

### <a name="return-value"></a>傳回值

*奧斯特*.

### <a name="remarks"></a>備註

此函數將*ID*插入*到 Ostr*。

如果有兩個 `thread::id` 物件要比較是否相等，則這些物件插入的文字表示會一樣。

## <a name="see-also"></a>另請參閱

[\<執行緒>](../standard-library/thread.md)
