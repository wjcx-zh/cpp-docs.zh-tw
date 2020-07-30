---
title: '&lt;forward_list&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: beb02a8353c6c5187dd0fa0171518c753eee7868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193337"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt; 運算子

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試運算子左邊的轉送清單物件是否等於右邊的轉送清單物件。

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="remarks"></a>備註

此範本函式會多載 `operator==` 來比較類別樣板的兩個物件 `forward_list` 。 函式會傳回 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試運算子左邊的轉送清單物件是否不等於右邊的轉送清單物件。

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果清單不相等，則為，**`false`** 如果清單相等則為。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left == right)`。

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試運算子左邊的轉送清單物件是否小於右邊的轉送清單物件。

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單小於但不等於運算子右邊的清單，則為，否則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會多載 `operator<` 來比較類別樣板的兩個物件 `forward_list` 。 函式會傳回 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的轉送清單物件是否小於或等於右邊的轉送清單物件。

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單小於或等於運算子右邊的清單，則為，否則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(right < left)`。

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試運算子左邊的轉送清單物件是否大於右邊的轉送清單物件。

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的清單大於運算子右邊的清單，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `right < left`。

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的轉送清單物件是否大於或等於右邊的轉送清單物件。

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`forward_list` 類型的物件。

*再*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的轉送清單大於或等於運算子右邊的轉送清單，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left < right)`。
