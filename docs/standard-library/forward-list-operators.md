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
ms.openlocfilehash: 64a49273cafd72158f176ee34ec271557ebee097
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240666"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; 運算子

## <a name="op_eq_eq"></a> 運算子 = =

測試運算子左邊的轉送清單物件是否等於右邊的轉送清單物件。

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="remarks"></a>備註

這個範本函式會多載 `operator==` 來比較 `forward_list` 範本類別的兩個物件。 函式會傳回 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`。

## <a name="op_neq"></a> 運算子 ！ =

測試運算子左邊的轉送清單物件是否不等於右邊的轉送清單物件。

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

如果清單不相等，便會傳回 **true**；如果清單相等，則會傳回 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left == right)`。

## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的轉送清單物件是否小於右邊的轉送清單物件。

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單小於但不等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

這個範本函式會多載 `operator<` 來比較 `forward_list` 範本類別的兩個物件。 函式會傳回 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`。

## <a name="op_lt_eq"></a> 運算子&lt;=

測試運算子左邊的轉送清單物件是否小於或等於右邊的轉送清單物件。

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單小於或等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(right < left)`。

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的轉送清單物件是否大於右邊的轉送清單物件。

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的清單大於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `right < left`。

## <a name="op_gt_eq"></a> 運算子&gt;=

測試運算子左邊的轉送清單物件是否大於或等於右邊的轉送清單物件。

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="return-value"></a>傳回值

**真**如果運算子左邊的轉送清單大於或等於運算子右邊的轉送清單，否則為**false**。

### <a name="remarks"></a>備註

此範本函式會傳回 `!(left < right)`。
