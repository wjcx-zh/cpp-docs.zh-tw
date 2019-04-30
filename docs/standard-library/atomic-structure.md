---
title: atomic 結構
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 258812f033d34f040d96847581d6f51692a933b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376665"
---
# <a name="atomic-structure"></a>atomic 結構

描述執行預存值上不可部分完成的作業類型的物件*Ty*。

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
|[atomic::operator=](#op_eq)|使用指定的值來取代預存值。 ([atomic::store](#store))|
|[atomic::operator++](#op_inc)|遞增預存值。 僅供整數和指標特製化使用。|
|[atomic::operator+=](#op_add_eq)|將指定的值加入預存值。 僅供整數和指標特製化使用。|
|[atomic::operator--](#op_dec)|遞減預存值。 僅供整數和指標特製化使用。|
|[atomic::operator-=](#op_sub_eq)|將預存值減去指定的值。 僅供整數和指標特製化使用。|
|[atomic::operator&=](#op_and_eq)|執行位元和指定的值和預存的值上。 僅供整數特製化使用。|
|[atomic::operator&#124;=](#op_or_eq)|執行位元或指定的值和預存的值上。 僅供整數特製化使用。|
|[atomic::operator^=](#op_xor_eq)|執行位元互斥或指定的值和預存的值上。 僅供整數特製化使用。|
|**函式**||
|[compare_exchange_strong](#compare_exchange_strong)|會執行*atomic_compare_and_exchange*上的作業**這**，並傳回結果。|
|[compare_exchange_weak](#compare_exchange_weak)|會執行*weak_atomic_compare_and_exchange*上的作業**這**，並傳回結果。|
|[fetch_add](#fetch_add)|將指定的值加入預存值。|
|[fetch_and](#fetch_and)|執行位元和指定的值和預存的值上。|
|[fetch_or](#fetch_or)|執行位元或指定的值和預存的值上。|
|[fetch_sub](#fetch_sub)|將預存值減去指定的值。|
|[fetch_xor](#fetch_xor)|執行位元互斥或指定的值和預存的值上。|
|[is_lock_free](#is_lock_free)|指定是否在不可部分完成的作業**這**會*無鎖定*。 如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」。|
|[load](#load)|讀取並傳回預存值。|
|[store](#store)|使用指定的值來取代預存值。|

## <a name="remarks"></a>備註

型別*Ty*必須*簡*。 也就使用[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)複製其位元組必須產生有效*Ty*比較為相等的原始物件的物件。 [Compare_exchange_weak](#compare_exchange_weak)並[compare_exchange_strong](#compare_exchange_strong)成員函式會使用[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)來判斷兩個*Ty*值相等。 將不會使用這些函式*Ty*-定義`operator==`。 成員函式`atomic`使用`memcpy`複製值的型別*Ty*。

部分特製化**不可部分完成\<Ty \* >** ，存在的所有指標類型。 特製化可以將位移加入 Managed 指標值，或從中減去位移。 算術運算會接受類型的引數`ptrdiff_t`，並調整的大小根據該引數*Ty*與一般位址算術一致。

除了每個整數類資料類型的特製**bool**。 每個特製化都會提供一組豐富的方法來進行不可部分完成算術和邏輯作業。

||||
|-|-|-|
|**atomic\<char>**|**不可部分完成\<char&lt;3 >**|**不可部分完成\<unsigned char >**|
|**atomic\<char16_t>**|**atomic\<char32_t>**|**atomic\<wchar_t>**|
|**atomic\<short>**|**不可部分完成\<unsigned short >**|**atomic\<int>**|
|**不可部分完成\<不帶正負號的 int >**|**atomic\<long>**|**不可部分完成\<不帶正負號長時間 >**|
|**atomic\<long long>**|**不可部分完成\<unsigned long long >**|

整數特製化衍生自對應的 `atomic_integral` 類型。 例如， **atomic\<不帶正負號的 int >** 衍生自`atomic_uint`。

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

是具現化的不可部分完成的物件\<*Ty*> 接受類型引數的建構函式可以只初始化*Ty*而不是由使用彙總初始設定。 不過，可以初始化 atomic_integral 物件只能藉由使用彙總初始化。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic:: operator *Ty*

指定範本中，不可部分完成類型的運算子\<*Ty*>。 擷取中的預存的值**\*這**。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>備註

此運算子會套用`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_eq"></a> atomic::operator=

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

## <a name="op_inc"></a> atomic::operator++

遞增預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞增後的值;最後兩個運算子會傳回遞增之前的值。 使用運算子`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_add_eq"></a> atomic::operator+=

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
整數或指標的值。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含相加的結果。

### <a name="remarks"></a>備註

這個運算子會使用`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_dec"></a> atomic::operator--

遞減預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞減的值;最後兩個運算子會傳回遞減之前的值。 使用運算子`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_sub_eq"></a> atomic::operator-=

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
整數或指標的值。

### <a name="return-value"></a>傳回值

A *Ty*物件，包含減法運算的結果。

### <a name="remarks"></a>備註

這個運算子會使用`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_and_eq"></a> atomic::operator&=

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

位元的結果和。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業的預存的值取代**\*這**的位元以及*值*和目前的值儲存在 **\*這**，條件約束內`memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="op_or_eq"></a> atomic::operator&#124;=

執行位元或在指定的值和預存的值**\*這**。 僅供整數特製化使用。

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

位元的結果或。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業的預存的值取代**\*這**的位元或*值*和目前的值儲存在 **\*這**，條件約束內`memory_order_seq_cst` [memory_order](atomic-enums.md)條件約束。

## <a name="op_xor_eq"></a> atomic:: operator ^ =

執行位元互斥或在指定的值和預存的值**\*這**。 僅供整數特製化使用。

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

位元排除的結果或。

### <a name="remarks"></a>備註

此運算子會執行的讀取-修改-寫入作業的預存的值取代**\*這**或與位元互斥*值*和目前的值儲存在**\*這**，條件約束內`memory_order_seq_cst` [memory_order](atomic-enums.md)條件約束。

## <a name="compare_exchange_strong"></a> atomic::compare_exchange_strong

執行不可部分完成比較和交換作業**\*這**。

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
第一個`memory_order`引數。

*Order2*<br/>
第二個 `memory_order` 引數。

### <a name="return-value"></a>傳回值

A **bool** ，表示要做數值比較的結果。

### <a name="remarks"></a>備註

此不可部分完成比較和交換作業將會儲存在值進行比較**\*這**具有*Exp*。如果值相等，作業將會取代所儲存的值**\*這**具有*值*使用讀取-修改-寫入作業，並套用所的記憶體順序條件約束所指定*diffgr:id="order1*。 如果值不相等，作業所使用的值會儲存在**\*這**來取代*Exp* ，並套用所指定的記憶體順序條件約束*Order2*.

沒有第二個多載`memory_order`使用隱含*Order2*的值為基礎*diffgr:id="order1*。 如果*diffgr:id="order1*是`memory_order_acq_rel`， *Order2*是`memory_order_acquire`。 如果*diffgr:id="order1*是`memory_order_release`， *Order2*是`memory_order_relaxed`。 在其他情況下， *Order2*等於*diffgr:id="order1*。

採用兩個的多載`memory_order`參數、 值*Order2*不能`memory_order_release`或`memory_order_acq_rel`，而且不能高於值*diffgr:id="order1*。

## <a name="compare_exchange_weak"></a> atomic:: compare_exchange_weak

對弱式不可部分完成比較和交換作業**\*這**。

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
第一個`memory_order`引數。

*Order2*<br/>
第二個 `memory_order` 引數。

### <a name="return-value"></a>傳回值

A **bool** ，表示要做數值比較的結果。

### <a name="remarks"></a>備註

此不可部分完成比較和交換作業將會儲存在值進行比較**\*這**具有*Exp*。如果值相等，作業將會取代所儲存的值**\*這**具有*值*使用讀取-修改-寫入作業，並套用所的記憶體順序條件約束所指定*diffgr:id="order1*。 如果值不相等，作業所使用的值會儲存在**\*這**來取代*Exp* ，並套用所指定的記憶體順序條件約束*Order2*.

弱式不可部分完成比較和交換作業會執行交換，比較的值是否相等。 如果值不相等，作業不會保證執行交換。

沒有第二個多載`memory_order`使用隱含*Order2*的值為基礎*diffgr:id="order1*。 如果*diffgr:id="order1*是`memory_order_acq_rel`， *Order2*是`memory_order_acquire`。 如果*diffgr:id="order1*是`memory_order_release`， *Order2*是`memory_order_relaxed`。 在其他情況下， *Order2*等於*diffgr:id="order1*。

採用兩個的多載`memory_order`參數、 值*Order2*不能`memory_order_release`或`memory_order_acq_rel`，而且不能高於值*diffgr:id="order1*。

## <a name="exchange"></a> atomic::exchange

使用指定的值來取代預存的值**\*這**。

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

預存的值**\*這**交換之前。

### <a name="remarks"></a>備註

這項作業執行的讀取-修改-寫入作業，使用*值*若要將值儲存在**\*這**，所指定的記憶體條件約束內*順序*。

## <a name="fetch_add"></a> atomic::fetch_add

擷取中儲存的值**\*這**，然後將指定的值加入至預存值。

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

A *Ty*物件，其中包含的值儲存在**\*這**新增之前。

### <a name="remarks"></a>備註

`fetch_add`方法會執行自動新增的讀取-修改-寫入作業*值*中的預存值**\*這**，並套用所指定的記憶體條件約束*順序*。

## <a name="fetch_and"></a> atomic::fetch_and

執行位元和對某個值和現有的值會儲存在**\*這**。

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

A *Ty*包含結果的位元的物件和。

### <a name="remarks"></a>備註

`fetch_and`方法會執行的讀取-修改-寫入作業的預存的值取代**\*這**的位元及的*值*和目前的值儲存在**\*這**，在所指定的記憶體條件約束內*順序*。

## <a name="fetch_or"></a> atomic:: fetch_or

執行位元或對某個值和現有的值會儲存在**\*這**。

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

A *Ty*包含結果的位元的物件或。

### <a name="remarks"></a>備註

`fetch_or`方法會執行的讀取-修改-寫入作業的預存的值取代**\*這**的位元或是*值*和目前的值儲存在**\*這**，在所指定的記憶體條件約束內*順序*。

## <a name="fetch_sub"></a> atomic::fetch_sub

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

A *Ty*物件，包含減法運算的結果。

### <a name="remarks"></a>備註

`fetch_sub`方法會執行的讀取-修改-寫入作業，以*值*中的預存值**\*這**，內所指定的記憶體條件約束*順序*。

## <a name="fetch_xor"></a> atomic:: fetch_xor

執行位元互斥或對某個值和現有的值會儲存在**\*這**。

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

*Order*<br/>
`memory_order`。

### <a name="return-value"></a>傳回值

A *Ty*包含結果的位元互斥的物件或。

### <a name="remarks"></a>備註

`fetch_xor`方法會執行的讀取-修改-寫入作業的預存的值取代**\*這**或使用位元互斥*值*和儲存在目前的值**\*這**，並套用所指定的記憶體條件約束*順序*。

## <a name="is_lock_free"></a> atomic:: is_lock_free

指定是否在不可部分完成的作業**\*這**是無鎖定。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>傳回值

如果不可部分完成，則為 true 的作業**\*這**會鎖定可用，否則為 false。

### <a name="remarks"></a>備註

如果該類型上的沒有不可部分完成作業使用鎖定，則不可部分完成的類型會是無鎖定。

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

*Order*<br/>
`memory_order`。 *順序*不得`memory_order_release`或`memory_order_acq_rel`。

### <a name="return-value"></a>傳回值

擷取的值，會儲存在**\*這**。

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

*Order*<br/>
A`memory_order`條件約束。

### <a name="remarks"></a>備註

此成員函式以不可分割方式儲存*值*中`*this`，在所指定的記憶體條件約束內*順序*。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)<br/>
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
