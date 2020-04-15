---
title: promise 類別
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323046"
---
# <a name="promise-class"></a>promise 類別

描述「非同步提供者」**。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[承諾](#promise)|建構 `promise` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_future](#get_future)|傳回與這項承諾相關聯的 [future](../standard-library/future-class.md)。|
|[set_exception](#set_exception)|以不可部分完成的方式設定這項承諾的結果以指出例外狀況。|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|以不可部分完成的方式設定這項承諾的結果以指出例外狀況，而且只有在目前執行緒中所有執行緒區域物件已終結後 (通常是在執行緒結束) 傳遞通知。|
|[set_value](#set_value)|以不可部分完成的方式設定這項承諾的結果以指出值。|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|以不可部分完成的方式設定這項承諾的結果以指出值，而且只有在目前執行緒中所有執行緒區域物件已終結後 (通常是在執行緒結束) 傳遞通知。|
|[交換](#swap)|交換這個承諾與指定之承諾物件的「相關聯非同步狀態」**。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[承諾::操作員*](#op_eq)|這個承諾物件共用狀態的指派。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

*承諾*

## <a name="requirements"></a>需求

**標題:**\<未來>

**命名空間：** std

## <a name="promiseget_future"></a><a name="get_future"></a>承諾::get_future

傳回 [future](../standard-library/future-class.md) 物件，它具有和這個承諾相同的「相關聯非同步狀態」**。

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>備註

如果承諾物件是空的，這個方法會擲回 [error_code](../standard-library/error-code-class.md) 為 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯的非同步狀態的承諾物件呼叫這個方法，方法會擲回 `future_error` 為 `error_code` 的 `future_already_retrieved`。

## <a name="promiseoperator"></a><a name="op_eq"></a>承諾::操作員*

從指定的 `promise` 物件轉移「相關聯非同步狀態」**。

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
`promise` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

此運算符從*其他*傳輸關聯的非同步狀態。 轉移後,*其他*為*空*。

## <a name="promisepromise-constructor"></a><a name="promise"></a>承諾::p羅馬結構器

建構 `promise` 物件。

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>參數

*鋁*\
記憶體配置器。 有關詳細資訊[\<,請參閱分配器>。](../standard-library/allocators-header.md)

*其他*\
`promise` 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構空的** `promise` 物件。

第二個構造函數建構一個`promise`空物件,並使用*Al*進行記憶體分配。

第三個構造函數構造一`promise`個物件,並從*其他*傳輸關聯的異步狀態,並將*其他*為空。

## <a name="promiseset_exception"></a><a name="set_exception"></a>承諾::set_exception

以不可部分完成的方式將例外狀況儲存為此 `promise` 物件的結果，並將「相關聯非同步狀態」** 設定為「就緒」**。

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>參數

*Exc*\
由這個方法儲存為例外狀況結果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>備註

如果 `promise` 物件沒有相關聯非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫`set_exception`、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

由於此方法的緣故，封鎖於相關聯非同步狀態上的任何執行緒會解除封鎖。

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>承諾::set_exception_at_thread_exit

以不可部分完成方式設定這個 `promise` 的結果以指出例外狀況，而且只有在目前執行緒中所有執行緒區域物件已終結後 (通常是在執行緒結束) 傳遞通知。

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>參數

*Exc*\
由這個方法儲存為例外狀況結果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>備註

如果 promise 物件沒有「相關聯非同步狀態」**，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果[已為](#set_exception)有相同`set_exception_at_thread_exit`關聯 的`promise`非同步狀態的物件[set_exception、set_value](#set_value)或[set_value_at_thread_exit,](#set_value_at_thread_exit)則此方法會引發`future_error``promise_already_satisfied`有的錯誤代碼 。

與 [set_exception](#set_exception) 相反，直到目前執行緒的所有執行緒區域物件皆已終結後，這個方法才會將相關聯非同步狀態設為就緒。 通常，除非目前的執行緒結束，否則被封鎖於關聯非同步狀態的執行緒不會解除封鎖。

## <a name="promiseset_value"></a><a name="set_value"></a>承諾::set_value

以不可部分完成的方式將值儲存為此 `promise` 物件的結果，並將「相關聯非同步狀態」** 設定為「就緒」**。

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>參數

*瓦爾*\
要儲存為結果的值。

### <a name="remarks"></a>備註

如果 `promise` 物件沒有相關聯非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫[set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、`set_value` 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

由於此方法的緣故，封鎖於相關聯非同步狀態上的任何執行緒會解除封鎖。

第一種方法還會引發將*Val*複製到關聯的非同步狀態時引發的任何異常。 在此情況下，相關聯非同步狀態將不會設定為就緒。

第二種方法還會引發在*將 Val*移動到關聯的異步狀態時引發的任何異常。 在此情況下，相關聯非同步狀態將不會設定為就緒。

對於部分專業化化`promise<Ty&>`,存儲的值實際上是對*Val*的引用。

對於特製化的 `promise<void>`，儲存值不存在。

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>承諾::set_value_at_thread_exit

以不可部分完成的方式將值儲存為此 `promise` 物件的結果。

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>參數

*瓦爾*\
要儲存為結果的值。

### <a name="remarks"></a>備註

如果 promise 物件沒有「相關聯非同步狀態」**，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 `set_value_at_thread_exit`，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

與 `set_value` 相反，直到目前執行緒的所有執行緒區域物件皆已終結後，才會將相關聯非同步狀態設為就緒。 通常，除非目前的執行緒結束，否則被封鎖於關聯非同步狀態的執行緒不會解除封鎖。

第一種方法還會引發將*Val*複製到關聯的非同步狀態時引發的任何異常。

第二種方法還會引發在*將 Val*移動到關聯的異步狀態時引發的任何異常。

對於部分專業化`promise<Ty&>`化,存儲值實際上是對*Val*的引用。

對於特製化的 `promise<void>`，儲存值不存在。

## <a name="promiseswap"></a><a name="swap"></a>承諾::交換

交換這個承諾物件與指定之物件的「相關聯非同步狀態」**。

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
`promise` 物件。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
