---
title: '&lt;選擇運算&gt;子'
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
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373625"
---
# <a name="ltoptionalgt-operators"></a>&lt;選擇運算&gt;子

## <a name="operator"></a><a name="op_eq_eq"></a>運算子*

測試運算子左邊的 `optional` 物件是否等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

## <a name="operator"></a><a name="op_neq"></a>操作員!

測試運算子左邊的 `optional` 物件是否不等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left == right)`。

## <a name="operatorlt"></a><a name="op_lt"></a>算子&lt;

測試運算子左邊的 `optional` 物件是否小於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單小於但不等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>算子&lt;=

測試運算子左邊的 `optional` 物件是否小於或等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單小於或等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(right < left)`。

## <a name="operatorgt"></a><a name="op_gt"></a>算子&gt;

測試運算子左邊的 `optional` 物件是否大於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單大於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `right < left`。

## <a name="operatorgt"></a><a name="op_gt_eq"></a>算子&gt;=

測試運算子左邊的 `optional` 物件是否大於或等於右邊的 `optional` 物件。

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>參數

*離開*\
類型`optional`的物件`nullopt_t``T`。

*對*\
類型`optional`的物件`nullopt_t``T`。

### <a name="return-value"></a>傳回值

如果運算子左側的 `optional` 大於或等於運算子右側的 `optional`，則為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left < right)`。
