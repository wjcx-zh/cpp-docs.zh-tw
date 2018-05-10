---
title: '&lt;system_error&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d0a556505370078f599d6d667fa856723d9bac8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt; 運算子

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a> operator==

測試運算子左邊的物件是否等於右邊的物件。

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`left`|要測試是否相等的物件。|
|`right`|要測試是否相等的物件。|

### <a name="return-value"></a>傳回值

如果物件相等，即為 **true**；如果物件不相等，則為 **false**。

### <a name="remarks"></a>備註

此函式會傳回 `left.category() == right.category() && left.value() == right.value()`。

## <a name="op_neq"></a> operator!=

測試運算子左邊的物件是否不等於右邊的物件。

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`left`|要測試是否不相等的物件。|
|`right`|要測試是否不相等的物件。|

### <a name="return-value"></a>傳回值

如果 `left` 中傳入的物件不等於 `right` 中傳入的物件，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

此函式會傳回 `!(left == right)`。

## <a name="op_lt"></a> operator&lt;

測試物件是否小於傳入的物件以進行比較。

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`left`|要比較的物件。|
|`right`|要比較的物件。|

### <a name="return-value"></a>傳回值

如果 `left` 中傳入的物件小於 `right` 中傳入的物件，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

這個功能測試錯誤順序。

## <a name="see-also"></a>另請參閱

[<system_error>](../standard-library/system-error.md)<br/>
