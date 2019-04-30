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
ms.openlocfilehash: 6ec4ff879b70e4d2cc16a3328217660db695e859
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377133"
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

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong

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

*Atom*<br/>
指標*atomic*物件，其中儲存型別的值`Ty`。

*Exp*<br/>
指向 `Ty` 類型值的指標。

*值*<br/>
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

**真**如果值相等，否則為**false**。

### <a name="remarks"></a>備註

這個方法會使用隱含 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數來執行不可部分完成比較和交換作業。 如需詳細資訊，請參閱 [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)。

## <a name="atomic_compare_exchange_strong_explicit"></a> atomic_compare_exchange_strong_explicit

執行「不可部分完成比較和交換」作業。

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

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*<br/>
指向 `Ty` 類型值的指標。

*值*<br/>
型別 `Ty` 的值。

*Order1*<br/>
第一個 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數。

*Order2*<br/>
第二個 `memory_order` 引數。 值*Order2*無法`memory_order_release`或是`memory_order_acq_rel`，它不能高於值*diffgr:id="order1*。

### <a name="return-value"></a>傳回值

**真**如果值相等，否則為**false**。

### <a name="remarks"></a>備註

*不可部分完成比較和交換作業*所指向之物件中儲存的值會比較*Atom*所指向的值*Exp*。如果值等於，值所指向之物件中儲存*atom*會取代*值*使用`read-modify-write`作業，並套用所的記憶體順序條件約束所指定*diffgr:id="order1*。 如果值不相等，作業將會取代所指向的值*Exp*的值，會儲存在所指的物件*Atom*和適用於記憶體順序條件約束所指定*Order2*。

## <a name="atomic_compare_exchange_weak"></a> atomic_compare_exchange_weak

執行「弱式不可部分完成比較和交換」作業。

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

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*<br/>
指向 `Ty` 類型值的指標。

*值*<br/>
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

**真**如果值相等，否則為**false**。

### <a name="remarks"></a>備註

這個方法會執行具有隱含 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數的*弱式不可部分完成比較和交換作業*。 如需詳細資訊，請參閱 [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)。

## <a name="atomic_compare_exchange_weak_explicit"></a> atomic_compare_exchange_weak_explicit

執行「弱式不可部分完成比較和交換」作業。

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

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*Exp*<br/>
指向 `Ty` 類型值的指標。

*值*<br/>
型別 `Ty` 的值。

*Order1*<br/>
第一個 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數。

*Order2*<br/>
第二個 `memory_order` 引數。 值*Order2*不得`memory_order_release`或是`memory_order_acq_rel`，也不能高於值*diffgr:id="order1*。

### <a name="return-value"></a>傳回值

**真**如果值相等，否則為**false**。

### <a name="remarks"></a>備註

強式和弱式類別*不可部分完成比較和交換作業*保證，它們不會儲存新值的預期和目前值是否不相等。 強式的類別可保證，它就會將新的值，預期值和目前值是否相等。 弱式類別可能有時會傳回**false**和未儲存的新值，即使目前與預期的值是否相等。 換句話說，此函數會傳回**false**，但它並未變更，並因此應該有比較為相等，可能會顯示預期值日後檢查。

## <a name="atomic_exchange"></a> atomic_exchange

會使用*值*若要取代的儲存的值*Atom*。

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

預存的值*Atom*交換之前。

### <a name="remarks"></a>備註

`atomic_exchange`函式會執行`read-modify-write`交換所儲存的值的作業*Atom*具有*值*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a> atomic_exchange_explicit

取代預存的值*Atom*具有*值*。

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

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `Ty` 的值。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

預存的值*Atom*交換之前。

### <a name="remarks"></a>備註

`atomic_exchange_explicit`函式會執行`read-modify-write`交換所儲存的值的作業*Atom*具有*值*，所指定的記憶體條件約束內*順序*。

## <a name="atomic_fetch_add"></a> atomic_fetch_add

將值新增至儲存於 `atomic` 物件的現有值。

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `T` 類型指標之 `atomic` 物件的指標。

*值*<br/>
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

`atomic_fetch_add`函式會執行`read-modify-write`作業，以自動新增*值*中的預存值*Atom*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

當不可部分完成類型是`atomic_address`，*值*具有型別`ptrdiff_t`，並在作業將儲存的指標視為`char *`。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a> atomic_fetch_add_explicit

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

*Atom*<br/>
儲存 `T` 類型指標之 `atomic` 物件的指標。

*值*<br/>
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

`atomic_fetch_add_explicit`函式會執行`read-modify-write`作業，以自動新增*值*中的預存值*Atom*內[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束所指定之`Order`。

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

## <a name="atomic_fetch_and"></a> atomic_fetch_and

對某個值和儲存於 `atomic` 物件的現有值執行位元 `and`。

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_and`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`and`的*值*和目前的值儲存在*Atom*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

## <a name="atomic_fetch_and_explicit"></a> atomic_fetch_and_explicit

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

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_and_explicit`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`and`的*值*和目前的值儲存在*Atom*，在所指定的記憶體條件約束*順序*。

## <a name="atomic_fetch_or"></a> atomic_fetch_or

對某個值和儲存於 `atomic` 物件的現有值執行位元 `or`。

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_or`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`or`的*值*和目前的值儲存在*Atom*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_fetch_or_explicit"></a> atomic_fetch_or_explicit

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

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_or_explicit`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`or`的*值*和目前的值儲存在*Atom*內[memory_order](../standard-library/atomic-enums.md#memory_order_enum)所指定的條件約束*順序*。

## <a name="atomic_fetch_sub"></a> atomic_fetch_sub

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

*Atom*<br/>
儲存 `T` 類型指標之 `atomic` 物件的指標。

*值*<br/>
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

`atomic_fetch_sub`函式會執行`read-modify-write`作業以不可分割方式減去*值*中的預存值*Atom*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

當不可部分完成類型是`atomic_address`，*值*具有型別`ptrdiff_t`，並在作業將儲存的指標視為`char *`。

也會針對整數類型多載這項作業︰

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a> atomic_fetch_sub_explicit

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

*Atom*<br/>
儲存 `T` 類型指標之 `atomic` 物件的指標。

*值*<br/>
型別 `ptrdiff_t` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的指標值。

### <a name="remarks"></a>備註

`atomic_fetch_sub_explicit`函式會執行`read-modify-write`作業以不可分割方式減去*值*中的預存值*Atom*內[memory_order](../standard-library/atomic-enums.md#memory_order_enum)所指定的條件約束`Order`。

當不可部分完成類型是`atomic_address`，*值*具有型別`ptrdiff_t`，並在作業將儲存的指標視為`char *`。

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

## <a name="atomic_fetch_xor"></a> atomic_fetch_xor

對某個值和儲存於 `atomic` 物件的現有值執行位元 `exclusive or`。

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_xor`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`exclusive or`的*值*和目前的值儲存在*Atom*，並使用`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_fetch_xor_explicit"></a> atomic_fetch_xor_explicit

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

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `T` 的值。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

緊接著執行作業前之 atomic 物件所包含的值。

### <a name="remarks"></a>備註

`atomic_fetch_xor_explicit`函式會執行`read-modify-write`作業的預存的值取代*Atom*的位元`exclusive or`的*值*和目前的值儲存在*Atom*內[memory_order](../standard-library/atomic-enums.md#memory_order_enum)所指定的條件約束*順序*。

## <a name="atomic_flag_clear"></a> atomic_flag_clear

集合**bool**中的旗標[atomic_flag](../standard-library/atomic-flag-structure.md)物件**false**內`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>參數

*旗標*<br/>
`atomic_flag` 物件的指標。

## <a name="atomic_flag_clear_explicit"></a> atomic_flag_clear_explicit

設定**bool**中的旗標[atomic_flag](../standard-library/atomic-flag-structure.md)物件**false**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*旗標*<br/>
`atomic_flag` 物件的指標。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flag_test_and_set"></a> atomic_flag_test_and_set

集**bool**中的旗標[atomic_flag](../standard-library/atomic-flag-structure.md)物件**true**，條件約束內`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>參數

*旗標*<br/>
`atomic_flag` 物件的指標。

### <a name="return-value"></a>傳回值

初始值*旗標*。

## <a name="atomic_flag_test_and_set_explicit"></a> atomic_flag_test_and_set_explicit

設定**bool**中的旗標[atomic_flag](../standard-library/atomic-flag-structure.md)物件 **，則為 true**，在指定[memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*旗標*<br/>
`atomic_flag` 物件的指標。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>傳回值

初始值*旗標*。

## <a name="atomic_init"></a> atomic_init

設定 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `Ty` 類型值之 `atomic` 物件的指標。

*值*<br/>
型別 `Ty` 的值。

### <a name="remarks"></a>備註

`atomic_init` 不是不可部分完成作業。 它不具備執行緒安全。

## <a name="atomic_is_lock_free"></a> atomic_is_lock_free

指定 `atomic` 物件上的不可部分完成作業是否為「無鎖定」。

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
儲存 `T` 類型值之 `atomic` 物件的指標。

### <a name="return-value"></a>傳回值

**true**如果不可部分完成的作業上*Atom*無鎖定，否則**false**。

### <a name="remarks"></a>備註

如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是無鎖定。 如果此函式傳回 true，則類型適合用於訊號處理常式。

## <a name="atomic_load"></a> atomic_load

擷取 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
包含 `atomic` 類型值之 `Ty` 物件的指標。

### <a name="return-value"></a>傳回值

擷取的值，會儲存在*Atom*。

### <a name="remarks"></a>備註

`atomic_load` 會隱含地使用 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_load_explicit"></a> atomic_load_explicit

在指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)內，擷取 `atomic` 物件中的預存值。

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
包含 `atomic` 類型值之 `Ty` 物件的指標。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 請不要使用 `memory_order_release` 或 `memory_order_acq_rel`。

### <a name="return-value"></a>傳回值

擷取的值，會儲存在*Atom*。

## <a name="atomic_signal_fence"></a> atomic_signal_fence

作為呼叫執行緒中具有相同執行緒中所執行訊號處理常式之其他範圍間的「範圍」，這是一種記憶體同步處理原始物件，可強制執行載入/儲存作業之間的順序。

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*Order*<br/>
決定範圍類型的記憶體順序條件約束。

### <a name="remarks"></a>備註

*順序*引數決定範圍類型。

|||
|-|-|
|`memory_order_relaxed`|範圍沒有作用。|
|`memory_order_consume`|範圍是取得範圍。|
|`memory_order_acquire`|範圍是取得範圍。|
|`memory_order_release`|範圍是釋放範圍。|
|`memory_order_acq_rel`|範圍同時是取得範圍和釋放範圍。|
|`memory_order_seq_cst`|範圍同時是取得範圍和釋放範圍，因此會一致。|

## <a name="atomic_store"></a> atomic_store

以不可部分完成方式將值儲存在不可部分完成的物件中。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>參數

*Atom*<br/>
不可部分完成的物件指標，該物件包含 `Ty` 類型的值。

*值*<br/>
型別 `Ty` 的值。

### <a name="remarks"></a>備註

`atomic_store` 會儲存*值*所指向之物件中*Atom*內`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)條件約束。

## <a name="atomic_store_explicit"></a> atomic_store_explicit

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

*Atom*<br/>
包含 `atomic` 類型值之 `Ty` 物件的指標。

*值*<br/>
型別 `Ty` 的值。

*Order*<br/>
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 請不要使用 `memory_order_consume`、`memory_order_acquire` 或 `memory_order_acq_rel`。

### <a name="remarks"></a>備註

`atomic_store` 會儲存*值*所指向之物件中*Atom*內`memory_order`所指定*順序*。

## <a name="atomic_thread_fence"></a> atomic_thread_fence

在沒有相關聯不可部分完成作業的情況下，作為「範圍」，這是一種記憶體同步處理原始物件，可強制執行載入/儲存作業之間的順序。

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>參數

*Order*<br/>
決定範圍類型的記憶體順序條件約束。

### <a name="remarks"></a>備註

*順序*引數決定範圍類型。

|||
|-|-|
|`memory_order_relaxed`|範圍沒有作用。|
|`memory_order_consume`|範圍是取得範圍。|
|`memory_order_acquire`|範圍是取得範圍。|
|`memory_order_release`|範圍是釋放範圍。|
|`memory_order_acq_rel`|範圍同時是取得範圍和釋放範圍。|
|`memory_order_seq_cst`|範圍同時是取得範圍和釋放範圍，因此會一致。|

## <a name="kill_dependency"></a> kill_dependency

移除相依性。

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>參數

*引數*<br/>
型別 `Ty` 的值。

### <a name="return-value"></a>傳回值

傳回值是*Arg*。 評估*Arg*並不包含函式呼叫的相依性。 透過中斷可能的相依性鏈結，此函式可能會讓編譯器產生更具效率的程式碼。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)<br/>
