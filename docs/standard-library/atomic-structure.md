---
title: atomic 結構 | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 298fe2751cf25355e2075a2870c34bf17cedc222
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="atomic-structure"></a>atomic 結構

描述的物件，執行預存值類型的不可部分完成的作業*Ty*。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>成員

|成員|描述|
|----------|-----------------|
|**建構函式**||
|[atomic](#atomic)|建構不可部分完成物件。|
|**運算子**||
|[atomic:: operator Ty](#op_ty)|讀取並傳回預存值。 ([atomic::load](#load))|
|[atomic:: operator =](#op_eq)|使用指定的值來取代預存值。 ([atomic::store](#store))|
|[atomic:: operator + +](#op_inc)|遞增預存值。 僅供整數和指標特製化使用。|
|[atomic:: operator + =](#op_add_eq)|將指定的值加入預存值。 僅供整數和指標特製化使用。|
|[atomic:: operator-](#op_dec)|遞減預存值。 僅供整數和指標特製化使用。|
|[atomic:: operator =](#op_sub_eq)|將預存值減去指定的值。 僅供整數和指標特製化使用。|
|[atomic:: operator （& a) =](#op_and_eq)|執行位元以及指定的值和儲存的值。 僅供整數特製化使用。|
|[atomic:: operator&#124;=](#op_or_eq)|執行位元或指定的值和儲存的值。 僅供整數特製化使用。|
|[atomic:: operator ^ =](#op_xor_eq)|執行位元互斥或指定的值和儲存的值。 僅供整數特製化使用。|
|**函式**||
|[compare_exchange_strong](#compare_exchange_strong)|執行*atomic_compare_and_exchange*作業**這**，並傳回結果。|
|[compare_exchange_weak](#compare_exchange_weak)|執行*weak_atomic_compare_and_exchange*作業**這**，並傳回結果。|
|[fetch_add](#fetch_add)|將指定的值加入預存值。|
|[fetch_and](#fetch_and)|執行位元以及指定的值和儲存的值。|
|[fetch_or](#fetch_or)|執行位元或指定的值和儲存的值。|
|[fetch_sub](#fetch_sub)|將預存值減去指定的值。|
|[fetch_xor](#fetch_xor)|執行位元互斥或指定的值和儲存的值。|
|[is_lock_free](#is_lock_free)|指定是否在不可部分完成的作業**這**是*鎖定可用*。 如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」。|
|[負載](#load)|讀取並傳回預存值。|
|[store](#store)|使用指定的值來取代預存值。|

## <a name="remarks"></a>備註

型別*Ty*必須*可完整複製*。 也就使用[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)複製其位元組必須產生有效*Ty*比較為等於原始物件的物件。 [Compare_exchange_weak](#compare_exchange_weak)和[compare_exchange_strong](#compare_exchange_strong)成員函式使用[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)來判斷兩個*Ty*值相等。 這些函式不會使用*Ty*-定義**運算子 = =**。 成員函式**不可部分完成**使用**memcpy**複製值的型別*Ty*。

部分特製化，* * 不可部分完成\<Ty * > * *，存在於所有指標類型。 特製化可以將位移加入 Managed 指標值，或從中減去位移。 型別引數的算術運算**ptrdiff_t**並調整該引數的大小根據*Ty*與一般位址算術一致。

除了每個整數類資料類型有特製化**bool**。 每個特製化都會提供一組豐富的方法來進行不可部分完成算術和邏輯作業。

||||
|-|-|-|
|**不可部分完成\<char >**|**不可部分完成\<簽署 char >**|**不可部分完成\<char 不帶正負號 >**|
|**不可部分完成\<char16_t >**|**不可部分完成\<char32_t >**|**不可部分完成\<wchar_t >**|
|**不可部分完成\<簡短 >**|**不可部分完成\<不帶正負號短 >**|**不可部分完成\<int >**|
|**不可部分完成\<不帶正負號的 int >**|**不可部分完成\<長 >**|**不可部分完成\<不帶正負號長時間 >**|
|**不可部分完成\<長長 >**|**不可部分完成\<unsigned long long >**|

整數類資料的特製化衍生自對應**atomic_integral**型別。 例如，**不可部分完成\<不帶正負號的 int >** 衍生自**atomic_uint**。

## <a name="requirements"></a>需求

**標頭：** \<不可部分完成 >

**命名空間：** std

## <a name="atomic"></a> atomic:: atomic

建構不可部分完成物件。

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
初始化值。

### <a name="remarks"></a>備註

無法複製或移動不可部分完成的物件。

具現化的不可部分完成的物件\<*Ty*> 只接受型別引數的建構函式會初始化*Ty*而不是使用彙總初始化。 不過，可以初始化 atomic_integral 物件只能透過使用彙總初始化。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic:: operator *Ty*

指定的範本不可部分完成類型的運算子\<*Ty*>。 擷取中的預存的值**\*這**。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>備註

這個運算子會套用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_eq"></a> atomic:: operator =

儲存指定的值。

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
A *Ty*物件。

### <a name="return-value"></a>傳回值

傳回*值*。

## <a name="op_inc"></a> atomic:: operator + +

遞增預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞增的值。最後兩個運算子會傳回前遞增的值。 運算子使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_add_eq"></a> atomic:: operator + =

將指定的值加入預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
將整數類資料類型或指標的值。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含相加的結果。

### <a name="remarks"></a>備註

這個運算子會使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_dec"></a> atomic:: operator-

遞減預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞減的值。最後兩個運算子會傳回前遞減的值。 運算子使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_sub_eq"></a> atomic:: operator =

將預存值減去指定的值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
將整數類資料類型或指標的值。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含的減法運算的結果。

### <a name="remarks"></a>備註

這個運算子會使用**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_and_eq"></a> atomic:: operator （& a) =

執行位元和指定的值和預存的值上的**\*這**。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

### <a name="return-value"></a>傳回值

結果的位元和。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**的位元和*值*以及目前的值儲存在 **\*這**，條件約束內**memory_order_seq_cst** [memory_order](atomic-enums.md)。

## <a name="op_or_eq"></a> atomic:: operator&#124;=

執行位元或指定的值和預存的值上的**\*這**。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

### <a name="return-value"></a>傳回值

結果的位元或。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**的位元或*值*以及目前的值儲存在 **\*這**，條件約束內**memory_order_seq_cst** [memory_order](atomic-enums.md)條件約束。

## <a name="op_xor_eq"></a> atomic:: operator ^ =

執行位元互斥上指定的值和儲存的值或**\*這**。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

### <a name="return-value"></a>傳回值

位元互斥的結果或。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**與位元互斥或*值*以及目前的值儲存在**\*這**，條件約束內**memory_order_seq_cst** [memory_order](atomic-enums.md)條件約束。

## <a name="compare_exchange_strong"></a> atomic:: compare_exchange_strong

上執行不可部分完成的比較和交換運算**\*這**。

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*Exp*<br/>
型別的值*Ty*。

*值*<br/>
型別的值*Ty*。

*Order1*<br/>
第一個 **memory_order** 引數。

*Order2*<br/>
第二個**memory_order**引數。

### <a name="return-value"></a>傳回值

A **bool**表示數值比較結果。

### <a name="remarks"></a>備註

此不可部分完成的比較和交換作業會比較儲存在值**\*這**與*Exp*。如果值相等，作業會取代值儲存在**\*這**與*值*使用讀取-修改-寫入作業，並套用是記憶體順序條件約束所指定*Order1*。 如果值不相等，作業所使用的值會儲存在**\*這**取代*Exp*和適用於所指定的記憶體順序條件約束*Order2*.

不具有第二個多載， **memory_order**使用隱含*Order2*的值為基礎*Order1*。 如果*Order1*是**memory_order_acq_rel**， *Order2*是**memory_order_acquire**。 如果*Order1*是**memory_order_release**， *Order2*是**memory_order_relaxed**。 在其他情況下， *Order2*等於*Order1*。

對於多載，以兩個**memory_order**參數、 值*Order2*不得**memory_order_release**或**memory_order_acq_rel**，且不能比的值更強*Order1*。

## <a name="compare_exchange_weak"></a> atomic:: compare_exchange_weak

弱式不可部分完成比較和交換作業對**\*這**。

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*Exp*<br/>
型別的值*Ty*。

*值*<br/>
型別的值*Ty*。

*Order1*<br/>
第一個 **memory_order** 引數。

*Order2*<br/>
第二個**memory_order**引數。

### <a name="return-value"></a>傳回值

A **bool**表示數值比較結果。

### <a name="remarks"></a>備註

此不可部分完成的比較和交換作業會比較儲存在值**\*這**與*Exp*。如果值相等，作業會取代值儲存在**\*這**與*值*使用讀取-修改-寫入作業，並套用是記憶體順序條件約束所指定*Order1*。 如果值不相等，作業所使用的值會儲存在**\*這**取代*Exp*和適用於所指定的記憶體順序條件約束*Order2*.

弱式不可部分完成比較和交換作業執行交換，如果比較的值相等。 如果值不相等，不保證會執行交換操作。

不具有第二個多載， **memory_order**使用隱含*Order2*的值為基礎*Order1*。 如果*Order1*是**memory_order_acq_rel**， *Order2*是**memory_order_acquire**。 如果*Order1*是**memory_order_release**， *Order2*是**memory_order_relaxed**。 在其他情況下， *Order2*等於*Order1*。

對於多載，以兩個**memory_order**參數、 值*Order2*不得**memory_order_release**或**memory_order_acq_rel**，且不能比的值更強*Order1*。

## <a name="exchange"></a> atomic:: exchange

使用指定的值取代儲存的值**\*這**。

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

儲存的值**\*這**交換之前。

### <a name="remarks"></a>備註

這項作業執行讀取-修改-寫入作業，使用*值*取代值儲存在**\*這**，所指定的記憶體條件約束內*順序*。

## <a name="fetch_add"></a> atomic:: fetch_add

擷取儲存的值**\*這**，然後將指定的值加入至儲存的值。

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含的值儲存在**\*這**新增之前。

### <a name="remarks"></a>備註

**Fetch_add**方法執行讀取-修改-寫入作業，以不可分割方式新增*值*中的預存值**\*這**，並套用記憶體所指定的條件約束*順序*。

## <a name="fetch_and"></a> atomic:: fetch_and

執行位元上的值和儲存在現有值和**\*這**。

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

A *Ty*包含結果的位元的物件和。

### <a name="remarks"></a>備註

**Fetch_and**方法會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**的位元和*值*和目前值，會儲存在**\*這**，所指定的記憶體條件約束內*順序*。

## <a name="fetch_or"></a> atomic:: fetch_or

執行位元上的值和儲存在現有值或**\*這**。

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

A *Ty*包含結果的位元的物件或。

### <a name="remarks"></a>備註

**Fetch_or**方法會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**的位元或*值*和目前的值儲存於**\*這**，所指定的記憶體條件約束內*順序*。

## <a name="fetch_sub"></a> atomic:: fetch_sub

將預存值減去指定的值。

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含的減法運算的結果。

### <a name="remarks"></a>備註

**Fetch_sub**方法執行讀取-修改-寫入作業，以不可分割方式減去*值*中的預存值**\*這**，記憶體中所指定的條件約束*順序*。

## <a name="fetch_xor"></a> atomic:: fetch_xor

執行位元互斥的值，以及儲存在現有值或**\*這**。

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
型別的值*Ty*。

*順序*<br/>
**memory_order**。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含的位元互斥結果或。

### <a name="remarks"></a>備註

**Fetch_xor**方法會執行的讀取-修改-寫入作業，以取代儲存的值**\*這**與位元互斥或*值*和目前的值會儲存在**\*這**，並套用所指定的記憶體條件約束*順序*。

## <a name="is_lock_free"></a> atomic:: is_lock_free

指定是否在不可部分完成的作業**\*這**是可用的鎖定。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>傳回值

如果不可部分完成，則為 true 的作業**\*這**會鎖定可用，否則為 false。

### <a name="remarks"></a>備註

不可部分完成的型別沒有不可部分完成的作業，在該類型上使用鎖定時可用的鎖定。

## <a name="load"></a> atomic:: load

擷取中的預存的值**\*這**，在指定的記憶體條件約束。

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>參數

*順序*<br/>
**memory_order**。 *順序*不得**memory_order_release**或**memory_order_acq_rel**。

### <a name="return-value"></a>傳回值

擷取的值儲存在**\*這**。

## <a name="store"></a> atomic:: store

儲存指定的值。

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>參數

*值*<br/>
A *Ty*物件。

*順序*<br/>
A **memory_order**條件約束。

### <a name="remarks"></a>備註

此成員函式會以不可分割方式儲存*值*中`*this`，所指定的記憶體條件約束內*順序*。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)<br/>
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
