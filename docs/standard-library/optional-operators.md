---
title: '&lt;選擇性 &gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: c7eca76f71f12e7f7fe0e60c0a4cfe456d54c374
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224678"
---
# <a name="ltoptionalgt-operators"></a>&lt;選擇性 &gt; 運算子

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試運算子左邊的 `optional` 物件是否等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試運算子左邊的 `optional` 物件是否不等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left == right)`。

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試運算子左邊的 `optional` 物件是否小於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單小於但不等於運算子右邊的清單，則為，否則為。否則為 **`false`** 。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的 `optional` 物件是否小於或等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單小於或等於運算子右邊的清單，則為，否則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(right < left)`。

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試運算子左邊的 `optional` 物件是否大於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單大於運算子右邊的清單，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `right < left`。

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的 `optional` 物件是否大於或等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*左面*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

*再*\
類型為 `optional` 、或的物件 `nullopt_t` `T` 。

### <a name="return-value"></a>傳回值

**`true`** 如果 `optional` 運算子左邊的大於或等於運算子右邊的，則為，否則為 `optional` **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left < right)`。
