---
title: error_category 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 218596ff5b81e99f4787efe2582fdc2752533cec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840163"
---
# <a name="error_category-class"></a>error_category 類別

表示物件的抽象、通用基底，以描述錯誤碼的分類。

## <a name="syntax"></a>語法

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>備註

下列兩個預先定義的物件會實作 `error_category`：[generic_category](../standard-library/system-error-functions.md#generic_category) 和 [system_category](../standard-library/system-error-functions.md#system_category)。

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[value_type](#value_type)|此類型表示預存的錯誤碼值。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[default_error_condition](#default_error_condition)|儲存錯誤狀況物件的錯誤碼值。|
|[等效](#equivalent)|傳回的值可指定錯誤物件是否相等。|
|[generic_category](#generic)||
|[message](#message)|傳回指定錯誤碼的名稱。|
|[name](#name)|傳回分類的名稱。|
|[system_category](#system)||

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#op_as)|指派運算子。|
|[operator = =](#op_eq_eq)|測試 `error_category` 物件是否相等。|
|[operator！ =](#op_neq)|測試 `error_category` 物件是否不相等。|
|[運算子<](#op_lt)|測試 [error_category](../standard-library/error-category-class.md) 物件是否小於傳入以進行比較的 `error_category` 物件。|

## <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

儲存錯誤狀況物件的錯誤碼值。

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>參數

`_Errval`\
要儲存在 [error_condition](../standard-library/error-condition-class.md) 中的錯誤碼值。

### <a name="return-value"></a>傳回值

傳回 `error_condition(_Errval, *this)`。

### <a name="remarks"></a>備註

### <a name="equivalent"></a><a name="equivalent"></a> 等效

傳回的值可指定錯誤物件是否相等。

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>參數

*_Errval*\
要比較的錯誤碼值。

*_Cond*\
要比較的 [error_condition](../standard-library/error-condition-class.md) 物件。

*_Code*\
要比較的 [error_code](../standard-library/error-code-class.md) 物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果分類和值相等;否則為 **`false`** 。

#### <a name="remarks"></a>備註

第一個成員函式會傳回 `*this == _Cond.category() && _Cond.value() == _Errval`。

第二個成員函式會傳回 `*this == _Code.category() && _Code.value() == _Errval`。

### <a name="generic_category"></a><a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a> 消息

傳回指定錯誤碼的名稱。

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>參數

*瓦爾*\
要描述的錯誤碼值。

#### <a name="return-value"></a>傳回值

傳回類別之錯誤碼 *val* 的描述性名稱。 如果錯誤碼無法辨識，則會傳回 `"unknown error"` 。

#### <a name="remarks"></a>備註

### <a name="name"></a><a name="name"></a> 名稱

傳回分類的名稱。

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>傳回值

傳回分類的名稱 (其為以 Null 結束的位元組字串)。

### <a name="operator"></a><a name="op_as"></a> 運算子 =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a> operator = =

測試 `error_category` 物件是否相等。

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果物件相等則為， **`false`** 如果物件不相等，則為。

#### <a name="remarks"></a>備註

此成員運算子會傳回 `this == &right`。

### <a name="operator"></a><a name="op_neq"></a> operator！ =

測試 `error_category` 物件是否不相等。

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要測試是否不相等的物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_category` 物件不等於 `error_category` *右邊*傳遞的物件，則為，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `(!*this == right)`。

### <a name="operatorlt"></a><a name="op_lt"></a> 運算元&lt;

測試 [error_category](../standard-library/error-category-class.md) 物件是否小於傳入以進行比較的 `error_category` 物件。

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>參數

*對*\
要比較的 `error_category` 物件。

#### <a name="return-value"></a>傳回值

**`true`** 如果 `error_category` 物件小於 `error_category` 傳入以進行比較的物件，否則為 **`false`** 。

#### <a name="remarks"></a>備註

成員運算子會傳回 `this < &right`。

### <a name="system_category"></a><a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a> value_type

此類型表示預存的錯誤碼值。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>備註

這個型別定義是的同義字 **`int`** 。
