---
title: '&lt;system_error&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420726"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;system_error&gt; 運算子

## <a name="op_eq_eq"></a>operator = =

測試運算子左邊的物件是否等於右邊的物件。

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>參數

*左方*\
要測試是否相等的物件。

*right*\
要測試是否相等的物件。

### <a name="return-value"></a>傳回值

如果物件相等，即為 **true**；如果物件不相等，則為 **false**。

### <a name="remarks"></a>備註

此函式會傳回 `left.category() == right.category() && left.value() == right.value()`。

## <a name="op_neq"></a>operator！ =

測試運算子左邊的物件是否不等於右邊的物件。

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>參數

*左方*\
要測試是否不相等的物件。

*right*\
要測試是否不相等的物件。

### <a name="return-value"></a>傳回值

如果在*左邊*傳遞的物件不等於傳入的物件 *，則***為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

此函式會傳回 `!(left == right)`。

## <a name="op_lt"></a> 運算子&lt;

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

*左方*\
要比較的物件。

*right*\
要比較的物件。

### <a name="return-value"></a>傳回值

如果在*左邊*傳遞的物件小於*傳入的物件*，則**為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個功能測試錯誤順序。

## <a name="op_ostream"></a>運算子&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
