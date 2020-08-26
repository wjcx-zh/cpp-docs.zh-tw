---
title: error_code 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: 5bbd67d2967a1a6d070ece54ea464a2a5a2deac9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844453"
---
# <a name="error_code-class"></a>error_code 類別

代表實作特定的低階系統錯誤。

## <a name="syntax"></a>語法

```cpp
class error_code;
```

## <a name="remarks"></a>備註

類型為 `error_code` 類別的物件會儲存錯誤碼值和物件指標，該物件表示的錯誤碼[分類](../standard-library/error-category-class.md)可描述回報的低層級系統錯誤。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[error_code](#error_code)|建構類型 `error_code` 的物件。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[value_type](#value_type)|此類型表示預存的錯誤碼值。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[assign](#assign)|可針對錯誤碼指派錯誤碼值和分類。|
|[類別](#category)|傳回錯誤分類。|
|[清楚](#clear)|清除錯誤碼值和分類。|
|[default_error_condition](#default_error_condition)|傳回預設的錯誤狀況。|
|[message](#message)|傳回錯誤碼的名稱。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](#op_eq_eq)|測試 `error_code` 物件是否相等。|
|[operator！ =](#op_neq)|測試 `error_code` 物件是否不相等。|
|[運算子<](#op_lt)|測試 `error_code` 物件是否小於傳入以進行比較的 `error_code` 物件。|
|[運算子 =](#op_eq)|將新的列舉值指派給 `error_code` 物件。|
|[運算子 bool](#op_bool)|轉換 `error_code` 類型的變數。|

### <a name="assign"></a><a name="assign"></a> 分配

可針對錯誤碼指派錯誤碼值和分類。

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

#### <a name="remarks"></a>備註

### <a name="clear"></a><a name="clear"></a> 清楚

清除錯誤碼值和分類。

```cpp
clear();
```

#### <a name="remarks"></a>備註

成員函式會儲存零的錯誤碼值以及 [generic_category](../standard-library/system-error-functions.md#generic_category) 物件的指標。

### <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

傳回預設的錯誤狀況。

```cpp
error_condition default_error_condition() const;
```

#### <a name="return-value"></a>傳回值

[default_error_condition](../standard-library/error-category-class.md#default_error_condition) 所指定的 [error_condition](../standard-library/error-condition-class.md)。

#### <a name="remarks"></a>備註

此成員函式會傳回 `category().default_error_condition(value())`。

### <a name="error_code"></a><a name="error_code"></a> error_code

建構類型 `error_code` 的物件。

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>參數

*瓦爾*\
要儲存在 `error_code` 中的錯誤碼值。

*_Cat*\
要儲存在 `error_code` 中的錯誤分類。

*_Errcode*\
要儲存在 `error_code` 中的列舉值。

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

測試 `error_code` 物件是否相等。

```cpp
bool operator==(const error_code& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果物件相等則為， **`false`** 如果物件不相等。

#### <a name="remarks"></a>備註

成員運算子會傳回 `category() == right.category() && value == right.value()`。

### <a name="operator"></a><a name="op_neq"></a> operator！ =

測試 `error_code` 物件是否不相等。

```cpp
bool operator!=(const error_code& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否不相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_code` 物件不等於 `error_code` *右邊*傳遞的物件，則為，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `!(*this == right)`。

### <a name="operatorlt"></a><a name="op_lt"></a> 運算元&lt;

測試 `error_code` 物件是否小於傳入以進行比較的 `error_code` 物件。

```cpp
bool operator<(const error_code& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要比較的 error_code 物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_code` 物件小於 `error_code` 傳入以進行比較的物件，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `category() < right.category() || category() == right.category() && value < right.value()`。

### <a name="operator"></a><a name="op_eq"></a> 運算子 =

將新的列舉值指派給 `error_code` 物件。

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

#### <a name="parameters"></a>參數

*_Errcode*\
要指派給 `error_code` 物件的列舉值。

#### <a name="return-value"></a>傳回值

`error_code` 物件的參考，該物件為成員函式要指派新列舉值的目標 。

#### <a name="remarks"></a>備註

成員運算子會儲存 `(value_type)_Errcode` 作為錯誤碼值，並儲存 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。 它會傳回 **`*this`** 。

### <a name="operator-bool"></a><a name="op_bool"></a> 運算子 bool

轉換 `error_code` 類型的變數。

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>傳回值

`error_code` 物件的布林值。

#### <a name="remarks"></a>備註

**`true`** 只有當[值](#value)不等於零時，運算子才會傳回可轉換為的值。 傳回型別只能轉換成 **`bool`** 、非 `void *` 或其他已知的純量類型。

### <a name="value"></a><a name="value"></a> 值

傳回預存的錯誤碼值。

```cpp
value_type value() const;
```

### <a name="return-value"></a>傳回值

[value_type](#value_type) 類型的預存錯誤碼值。

### <a name="value_type"></a><a name="value_type"></a> value_type

此類型表示預存的錯誤碼值。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>備註

這個型別定義是的同義字 **`int`** 。
