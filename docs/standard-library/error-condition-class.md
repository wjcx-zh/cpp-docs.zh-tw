---
title: error_condition 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: 1708a3f560f60fe3933406a904d95b4d29890a7f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830770"
---
# <a name="error_condition-class"></a>error_condition 類別

代表使用者定義的錯誤碼。

## <a name="syntax"></a>語法

```cpp
class error_condition;
```

## <a name="remarks"></a>備註

`error_condition` 類型的物件會儲存錯誤碼值和物件指標，該物件表示的錯誤碼[分類](../standard-library/error-category-class.md)可用來回報使用者定義的錯誤。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[error_condition](#error_condition)|建構類型 `error_condition` 的物件。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[value_type](#value_type)|此類型表示預存的錯誤碼值。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[assign](#assign)|可針對錯誤狀況指派錯誤碼值和分類。|
|[類別](#category)|傳回錯誤分類。|
|[清楚](#clear)|清除錯誤碼值和分類。|
|[message](#message)|傳回錯誤碼的名稱。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](#op_eq_eq)|測試 `error_condition` 物件是否相等。|
|[operator！ =](#op_neq)|測試 `error_condition` 物件是否不相等。|
|[運算子<](#op_lt)|測試 `error_condition` 物件是否小於傳入以進行比較的 `error_code` 物件。|
|[運算子 =](#op_eq)|將新的列舉值指派給 `error_condition` 物件。|
|[運算子 bool](#op_bool)|轉換 `error_condition` 類型的變數。|

### <a name="assign"></a><a name="assign"></a> 分配

可針對錯誤狀況指派錯誤碼值和分類。

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>參數

*瓦爾*\
要儲存在 `error_code` 中的錯誤碼值。

*_Cat*\
要儲存在 `error_code` 中的錯誤分類。

#### <a name="remarks"></a>備註

成員函式會將 *val* 儲存為錯誤碼值，並儲存指向 *_Cat*的指標。

### <a name="category"></a><a name="category"></a> 類別

傳回錯誤分類。

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>傳回值

預存的錯誤分類參考。

#### <a name="remarks"></a>備註

### <a name="clear"></a><a name="clear"></a> 清楚

清除錯誤碼值和分類。

```cpp
clear();
```

#### <a name="remarks"></a>備註

成員函式會儲存零的錯誤碼值以及 [generic_category](../standard-library/system-error-functions.md#generic_category) 物件的指標。

### <a name="error_condition"></a><a name="error_condition"></a> error_condition

建構類型 `error_condition` 的物件。

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>參數

*瓦爾*\
要儲存在 `error_condition` 中的錯誤碼值。

*_Cat*\
要儲存在 `error_condition` 中的錯誤分類。

*_Errcode*\
要儲存在 `error_condition` 中的列舉值。

#### <a name="remarks"></a>備註

第一個建構函式會儲存零的錯誤碼值以及 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。

第二個函式會將 *val* 儲存為錯誤碼值，並儲存指向 [error_category](../standard-library/error-category-class.md)的指標。

第三個建構函式會儲存 `(value_type)_Errcode` 作為錯誤碼值，並儲存 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。

### <a name="message"></a><a name="message"></a> 消息

傳回錯誤碼的名稱。

```cpp
string message() const;
```

#### <a name="return-value"></a>傳回值

`string`，表示錯誤碼的名稱。

#### <a name="remarks"></a>備註

此成員函式會傳回 `category().message(value())`。

### <a name="operator"></a><a name="op_eq_eq"></a> operator = =

測試 `error_condition` 物件是否相等。

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果物件相等則為， **`false`** 如果物件不相等。

#### <a name="remarks"></a>備註

成員運算子會傳回 `category() == right.category() && value == right.value()`。

### <a name="operator"></a><a name="op_neq"></a> operator！ =

測試 `error_condition` 物件是否不相等。

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否不相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_condition` 物件不等於 `error_condition` *右邊*傳遞的物件，則為，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `!(*this == right)`。

### <a name="operatorlt"></a><a name="op_lt"></a> 運算元&lt;

測試 `error_condition` 物件是否小於傳入以進行比較的 `error_code` 物件。

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要比較的 `error_condition` 物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_condition` 物件小於 `error_condition` 傳入以進行比較的物件，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `category() < right.category() || category() == right.category() && value < right.value()`。

### <a name="operator"></a><a name="op_eq"></a> 運算子 =

將新的列舉值指派給 `error_condition` 物件。

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>參數

*_Errcode*\
要指派給 `error_condition` 物件的列舉值。

#### <a name="return-value"></a>傳回值

`error_condition` 物件的參考，該物件為成員函式要指派新列舉值的目標 。

#### <a name="remarks"></a>備註

成員運算子會儲存 `(value_type)error` 作為錯誤碼值，並儲存 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。 它會傳回 **`*this`** 。

### <a name="operator-bool"></a><a name="op_bool"></a> 運算子 bool

轉換 `error_condition` 類型的變數。

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>傳回值

`error_condition` 物件的布林值。

#### <a name="remarks"></a>備註

**`true`** 只有當[值](#value)不等於零時，運算子才會傳回可轉換為的值。 傳回型別只能轉換成 **`bool`** 、非 `void *` 或其他已知的純量類型。

### <a name="value"></a><a name="value"></a> 值

傳回預存的錯誤碼值。

```cpp
value_type value() const;
```

#### <a name="return-value"></a>傳回值

[value_type](#value_type) 類型的預存錯誤碼值。

#### <a name="remarks"></a>備註

### <a name="value_type"></a><a name="value_type"></a> value_type

此類型表示預存的錯誤碼值。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>備註

型別定義是的同義字 **`int`** 。
