---
title: '&lt;atomic&gt; 函式'
ms.date: 07/11/2018
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376891"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt; 函式

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

執行不可部分完成比較和交換作業。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
指向存儲類型`Ty`值的*原子*物件的指標。

*Exp*\
指向 `Ty` 類型值的指標。

*價值*\
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

如果值相等,則**為 true,** 否則**為 false**。

### <a name="remarks"></a>備註

這個方法會使用隱含 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數來執行不可部分完成比較和交換作業。 如需詳細資訊，請參閱 [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)。

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

執行*原子比較和交換*操作。

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*\
指向 `Ty` 類型值的指標。

*價值*\
型別 `Ty` 的值。

*訂單1*\
第一個 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數。

*訂單2*\
第二個 `memory_order` 引數。 *Order2*的值`memory_order_release`不能`memory_order_acq_rel`或 ,它不能比訂單*1*的值強。

### <a name="return-value"></a>傳回值

如果值相等,則**為 true,** 否則**為 false**。

### <a name="remarks"></a>備註

*原子比較和交換操作*將*存儲在 Atom*指向的物件中的值與*Exp*指向的值進行比較。如果值相等,則儲存在*由原子*指向的物件中的值將替換為*Value,*`read-modify-write`使用操作 並應用*Order1*指定的記憶體順序約束。 如果值不相等,則操作將*Exp*指向的值替換為存儲在*Atom*指向的物件中的值,並應用*Order2*指定的記憶體順序約束。

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

執行「弱式不可部分完成比較和交換」** 作業。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*\
指向 `Ty` 類型值的指標。

*價值*\
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

如果值相等,則**為 true,** 否則**為 false**。

### <a name="remarks"></a>備註

這個方法會執行具有隱含 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數的*弱式不可部分完成比較和交換作業*。 如需詳細資訊，請參閱 [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)。

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

執行「弱式不可部分完成比較和交換」** 作業。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*\
指向 `Ty` 類型值的指標。

*價值*\
型別 `Ty` 的值。

*訂單1*\
第一個 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數。

*訂單2*\
第二個 `memory_order` 引數。 *Order2*的值`memory_order_release`不能`memory_order_acq_rel`或 ,也不能比*Order1*的值強。

### <a name="return-value"></a>傳回值

如果值相等,則**為 true,** 否則**為 false**。

### <a name="remarks"></a>備註

*原子比較和交換操作*的強弱味道都保證,如果預期值和當前值不相等,它們不會存儲新值。 如果預期值和當前值相等,則強風味保證將存儲新值。 弱味有時可能返回**false,** 並且即使當前值和預期值相等,也不會存儲新值。 換句話說,函數將返回**false,** 但以後對預期值的檢查可能會顯示它沒有變化,因此應該比較為相等。

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

使用*值*替換*Atom*的儲存值。

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

交換前*Atom*的儲存值。

### <a name="remarks"></a>備註

函數`atomic_exchange`執行一`read-modify-write`個 操作`memory_order_seq_cst`,使用[memory_order](../standard-library/atomic-enums.md#memory_order_enum)將存儲在*Atom*中的值與*值*交換。

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

將*Atom*的儲存值取代為*值*。

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `Ty` 的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

交換前*Atom*的儲存值。

### <a name="remarks"></a>備註

函數`atomic_exchange_explicit`執行一`read-modify-write`個 操作,在*Order*指定的記憶體約束中將存儲在*Atom*中*的值與值*交換。

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

將值新增至儲存於 `atomic` 物件的現有值。

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型指標之 `atomic` 物件的指標。

*價值*\
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

函數`atomic_fetch_add`執行一`read-modify-write`個 操作`memory_order_seq_cst`,使用[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束在*原子*中以原子方式將*值*添加到存儲的值。

當原子型態`atomic_address`為時 *,值*有類型`ptrdiff_t`,操作將儲存`char *`的指標視為 。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

將值新增至儲存於 `atomic` 物件的現有值。

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型指標之 `atomic` 物件的指標。

*價值*\
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

函數`atomic_fetch_add_explicit``read-modify-write`執行操作,在指定`Order`的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束內,以原子方式將*值*添加到*Atom*中的儲存值。

atomic 類型是 `atomic_address` 時，`Value` 會具有類型 `ptrdiff_t`，而且作業會將儲存的指標視為 `char *`。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

對某個值和儲存於 `atomic` 物件的現有值執行位元 `and`。

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

函數`atomic_fetch_and`執行一`read-modify-write`個 操作`memory_order_seq_cst`,使用[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束將`and`*Atom*的儲存*值*替換為值的位值和存儲在*Atom*中的當前值。

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

對某個值和儲存於 `atomic` 物件的現有值執行位元 `and`。

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

函數`atomic_fetch_and_explicit`執行一`read-modify-write`個 操作,在*Order*指定的記憶體約束`and`中,將*Atom*的儲存值替換為位*值*和存儲在*Atom*中的當前值。

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

對某個值和儲存於 `atomic` 物件的現有值執行位元 `or`。

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

函數`atomic_fetch_or`執行一`read-modify-write`個 操作`memory_order_seq_cst`,使用[memory_order](../standard-library/atomic-enums.md#memory_order_enum)將*Atom*的儲存值`or`替換為位*值*和存儲在*Atom*中的當前值。

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

對某個值和儲存於 `atomic` 物件的現有值執行位元 `or`。

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

該`atomic_fetch_or_explicit`函數執行`read-modify-write`一個操作,在*Order*指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束內,將`or` *Atom*的儲存值替換為位*值*和存儲在*Atom*中的當前值。

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

將儲存於 `atomic` 物件的現有值減去某個值。

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型指標之 `atomic` 物件的指標。

*價值*\
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

函數`atomic_fetch_sub``memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)使用`read-modify-write`memory_order 規範 執行一個操作,在*原子*中從儲存的值中從儲存值中從原子中從原子中從原子中從原子中減去*值*。

當原子型態`atomic_address`為時 *,值*有類型`ptrdiff_t`,操作將儲存`char *`的指標視為 。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

將儲存於 `atomic` 物件的現有值減去某個值。

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型指標之 `atomic` 物件的指標。

*價值*\
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

函數`atomic_fetch_sub_explicit`執行一`read-modify-write`個 操作,在`Order`指定的 memory_order約束內,在*Atom*中儲存的值中從儲存值中從原子中從原子中從儲存值中從原子中從原子中從[原子](../standard-library/atomic-enums.md#memory_order_enum)中減去*值*。

當原子型態`atomic_address`為時 *,值*有類型`ptrdiff_t`,操作將儲存`char *`的指標視為 。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

對某個值和儲存於 `atomic` 物件的現有值執行位元 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

函數`atomic_fetch_xor`執行一`read-modify-write`個 操作`memory_order_seq_cst`,使用[memory_order](../standard-library/atomic-enums.md#memory_order_enum)將*Atom*的儲存值`exclusive or`替換為位*值*和存儲在*Atom*中的當前值。

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

對某個值和儲存於 `atomic` 物件的現有值執行位元 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `T` 的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

函數`atomic_fetch_xor_explicit`執行一`read-modify-write`個 操作,在*Order*指定的`exclusive or`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束中,將*Atom*的儲存值替換為位*值*和存儲在*Atom*中的當前值。

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

將[atomic_flag](../standard-library/atomic-flag-structure.md)物件中的**bool**標誌memory_order 中[memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`設定為**false。**

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>參數

*國旗*\
`atomic_flag` 物件的指標。

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束中,將[atomic_flag](../standard-library/atomic-flag-structure.md)物件中的**bool**標誌設置為**false。**

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*國旗*\
`atomic_flag` 物件的指標。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

在`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)的約束下,將[atomic_flag](../standard-library/atomic-flag-structure.md)物件中的**bool**標誌設置**為 true。**

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>參數

*國旗*\
`atomic_flag` 物件的指標。

### <a name="return-value"></a>傳回值

*旗標*的初始值 。

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)約束中,將[atomic_flag](../standard-library/atomic-flag-structure.md)物件中的**bool**標誌設置為**true。**

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*國旗*\
`atomic_flag` 物件的指標。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

*旗標*的初始值 。

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

設定 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*價值*\
型別 `Ty` 的值。

### <a name="remarks"></a>備註

`atomic_init` 不是不可部分完成作業。 它不具備執行緒安全。

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

指定 `atomic` 物件上的不可部分完成作業是否為「無鎖定」**。

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
儲存 `T` 類型值之 `atomic` 物件的指標。

### <a name="return-value"></a>傳回值

如果*原子*上的原子操作是無鎖的,**則為 true;** 否則,**假**。

### <a name="remarks"></a>備註

如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是無鎖定。 如果此函式傳回 true，則類型適合用於訊號處理常式。

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

擷取 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
包含 `atomic` 類型值之 `Ty` 物件的指標。

### <a name="return-value"></a>傳回值

存儲在*Atom*中檢索的值。

### <a name="remarks"></a>備註

`atomic_load` 會隱含地使用 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)內，擷取 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
包含 `atomic` 類型值之 `Ty` 物件的指標。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 請不要使用 `memory_order_release` 或 `memory_order_acq_rel`。

### <a name="return-value"></a>傳回值

存儲在*Atom*中檢索的值。

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

作為呼叫執行緒中具有相同執行緒中所執行訊號處理常式之其他範圍間的「範圍」**，這是一種記憶體同步處理原始物件，可強制執行載入/儲存作業之間的順序。

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*以*\
決定範圍類型的記憶體順序條件約束。

### <a name="remarks"></a>備註

*Order*參數確定圍欄類型。

|||
|-|-|
|`memory_order_relaxed`|範圍沒有作用。|
|`memory_order_consume`|範圍是取得範圍。|
|`memory_order_acquire`|範圍是取得範圍。|
|`memory_order_release`|範圍是釋放範圍。|
|`memory_order_acq_rel`|範圍同時是取得範圍和釋放範圍。|
|`memory_order_seq_cst`|範圍同時是取得範圍和釋放範圍，因此會一致。|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

以不可部分完成方式將值儲存在不可部分完成的物件中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
不可部分完成的物件指標，該物件包含 `Ty` 類型的值。

*價值*\
型別 `Ty` 的值。

### <a name="remarks"></a>備註

`atomic_store`在`memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)限制中儲存*Atom*指向的物件中*的值*。

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

以不可部分完成方式將值儲存在不可部分完成的物件中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*原子*\
包含 `atomic` 類型值之 `Ty` 物件的指標。

*價值*\
型別 `Ty` 的值。

*以*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 請不要使用 `memory_order_consume`、`memory_order_acquire` 或 `memory_order_acq_rel`。

### <a name="remarks"></a>備註

`atomic_store`在*Atom*指向的物件中儲存*值*,在*Order*`memory_order`指定的物件中。

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

在沒有相關聯不可部分完成作業的情況下，作為「範圍」**，這是一種記憶體同步處理原始物件，可強制執行載入/儲存作業之間的順序。

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*以*\
決定範圍類型的記憶體順序條件約束。

### <a name="remarks"></a>備註

*Order*參數確定圍欄類型。

|||
|-|-|
|`memory_order_relaxed`|範圍沒有作用。|
|`memory_order_consume`|範圍是取得範圍。|
|`memory_order_acquire`|範圍是取得範圍。|
|`memory_order_release`|範圍是釋放範圍。|
|`memory_order_acq_rel`|範圍同時是取得範圍和釋放範圍。|
|`memory_order_seq_cst`|範圍同時是取得範圍和釋放範圍，因此會一致。|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

移除相依性。

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>參數

*精 氨 酸*\
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

傳回數為*Arg*。 *Arg*的評估不依賴於函數調用。 透過中斷可能的相依性鏈結，此函式可能會讓編譯器產生更具效率的程式碼。

## <a name="see-also"></a>另請參閱

[\<原子>](../standard-library/atomic.md)
