---
title: promise 類別 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 2b62f4b4be278fc3cc29e32c323c9a0936598d44
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058028"
---
# <a name="promise-class"></a>promise 類別

描述「非同步提供者」。

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
|[swap](#swap)|交換這個承諾與指定之承諾物件的「相關聯非同步狀態」。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[promise::operator=](#op_eq)|這個承諾物件共用狀態的指派。|

## <a name="inheritance-hierarchy"></a>繼承階層

*承諾*<br/>

## <a name="requirements"></a>需求

**標頭：** \<未來 >

**命名空間：** std

## <a name="get_future"></a>  promise::get_future

傳回 [future](../standard-library/future-class.md) 物件，它具有和這個承諾相同的「相關聯非同步狀態」。

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>備註

如果承諾物件是空的，這個方法會擲回 [error_code](../standard-library/error-code-class.md) 為 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯的非同步狀態的承諾物件呼叫這個方法，方法會擲回 `future_error` 為 `error_code` 的 `future_already_retrieved`。

## <a name="op_eq"></a>  promise::operator=

從指定的 `promise` 物件轉移「相關聯非同步狀態」。

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*<br/>
`promise` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

此運算子轉移相關聯的非同步狀態，從*其他*。 轉移之後，*其他*是*空白*。

## <a name="promise"></a>  promise::promise 建構函式

建構 `promise` 物件。

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>參數

*Al*<br/>
記憶體配置器。 如需詳細資訊，請參閱 [\<allocators>](../standard-library/allocators-header.md)。

*其他*<br/>
`promise` 物件。

### <a name="remarks"></a>備註

第一個建構函式建構*空*`promise`物件。

第二個建構函式會建構空`promise`物件，並使用*Al*進行記憶體配置。

第三個建構函式建構`promise`物件，並將轉移相關聯的非同步狀態，從*其他*，並將保留*其他*空白。

## <a name="set_exception"></a>  promise::set_exception

以不可部分完成的方式將例外狀況儲存為此 `promise` 物件的結果，並將「相關聯非同步狀態」設定為「就緒」。

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>參數

*專有*<br/>
由這個方法儲存為例外狀況結果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>備註

如果 `promise` 物件沒有相關聯非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫`set_exception`、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

由於此方法的緣故，封鎖於相關聯非同步狀態上的任何執行緒會解除封鎖。

## <a name="set_exception_at_thread_exit"></a>  promise::set_exception_at_thread_exit

以不可部分完成方式設定這個 `promise` 的結果以指出例外狀況，而且只有在目前執行緒中所有執行緒區域物件已終結後 (通常是在執行緒結束) 傳遞通知。

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>參數

*專有*<br/>
由這個方法儲存為例外狀況結果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>備註

如果 promise 物件沒有「相關聯非同步狀態」，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫 [set_exception](#set_exception)、`set_exception_at_thread_exit`、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

與 [set_exception](#set_exception) 相反，直到目前執行緒的所有執行緒區域物件皆已終結後，這個方法才會將相關聯非同步狀態設為就緒。 通常，除非目前的執行緒結束，否則被封鎖於關聯非同步狀態的執行緒不會解除封鎖。

## <a name="set_value"></a>  promise::set_value

以不可部分完成的方式將值儲存為此 `promise` 物件的結果，並將「相關聯非同步狀態」設定為「就緒」。

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>參數

*val*<br/>
要儲存為結果的值。

### <a name="remarks"></a>備註

如果 `promise` 物件沒有相關聯非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫[set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、`set_value` 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

由於此方法的緣故，封鎖於相關聯非同步狀態上的任何執行緒會解除封鎖。

第一種方法也會擲回任何例外狀況時擲回*Val*複製到相關聯的非同步狀態。 在此情況下，相關聯非同步狀態將不會設定為就緒。

第二種方法也會擲回任何例外狀況時擲回*Val*移至相關聯的非同步狀態。 在此情況下，相關聯非同步狀態將不會設定為就緒。

部分特製化`promise<Ty&>`，儲存的值實際上是參考*Val*。

對於特製化的 `promise<void>`，儲存值不存在。

## <a name="set_value_at_thread_exit"></a>  promise::set_value_at_thread_exit

以不可部分完成的方式將值儲存為此 `promise` 物件的結果。

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>參數

*val*<br/>
要儲存為結果的值。

### <a name="remarks"></a>備註

如果 promise 物件沒有「相關聯非同步狀態」，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。

如果已經針對具有同一個相關聯非同步狀態的 `promise` 物件呼叫 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 `set_value_at_thread_exit`，則這個方法會擲回含有 `promise_already_satisfied` 錯誤碼的 `future_error`。

與 `set_value` 相反，直到目前執行緒的所有執行緒區域物件皆已終結後，才會將相關聯非同步狀態設為就緒。 通常，除非目前的執行緒結束，否則被封鎖於關聯非同步狀態的執行緒不會解除封鎖。

第一種方法也會擲回任何例外狀況時擲回*Val*複製到相關聯的非同步狀態。

第二種方法也會擲回任何例外狀況時擲回*Val*移至相關聯的非同步狀態。

部分特製化`promise<Ty&>`，預存的值實際上是參考*Val*。

對於特製化的 `promise<void>`，儲存值不存在。

## <a name="swap"></a>  promise::swap

交換這個承諾物件與指定之物件的「相關聯非同步狀態」。

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*<br/>
`promise` 物件。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
