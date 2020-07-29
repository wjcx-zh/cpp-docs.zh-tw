---
title: atomic 結構
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 8701078f8a034d80dae41eee0d842fb15fd8d3a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203931"
---
# <a name="atomic-structure"></a>atomic 結構

描述在*Ty*類型的預存值上執行不可部分完成作業的物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>成員

|成員|說明|
|----------|-----------------|
|**函數**||
|[不可部分完成](#atomic)|建構不可部分完成物件。|
|**運算子**||
|[不可部分完成：： operator Ty](#op_ty)|讀取並傳回預存值。 （不可部分完成[：：載入](#load)）|
|[不可部分完成：： operator =](#op_eq)|使用指定的值來取代預存值。 （不可部分完成[：： store](#store)）|
|[不可部分完成：： operator + +](#op_inc)|遞增預存值。 僅供整數和指標特製化使用。|
|[不可部分完成：： operator + =](#op_add_eq)|將指定的值加入預存值。 僅供整數和指標特製化使用。|
|[不可部分完成：： operator--](#op_dec)|遞減預存值。 僅供整數和指標特製化使用。|
|[不可部分完成：： operator-=](#op_sub_eq)|將預存值減去指定的值。 僅供整數和指標特製化使用。|
|[不可部分完成：： operator&=](#op_and_eq)|針對指定的值和儲存的值執行位 and。 僅供整數特製化使用。|
|[不可部分完成：： operator&#124;=](#op_or_eq)|針對指定的值和儲存的值執行位 or。 僅供整數特製化使用。|
|[不可部分完成：： operator ^ =](#op_xor_eq)|針對指定的值和儲存的值執行位互斥 or。 僅供整數特製化使用。|
|**函式**||
|[compare_exchange_strong](#compare_exchange_strong)|在上執行*atomic_compare_and_exchange*作業 **`this`** ，並傳回結果。|
|[compare_exchange_weak](#compare_exchange_weak)|在上執行*weak_atomic_compare_and_exchange*作業 **`this`** ，並傳回結果。|
|[fetch_add](#fetch_add)|將指定的值加入預存值。|
|[fetch_and](#fetch_and)|針對指定的值和儲存的值執行位 and。|
|[fetch_or](#fetch_or)|針對指定的值和儲存的值執行位 or。|
|[fetch_sub](#fetch_sub)|將預存值減去指定的值。|
|[fetch_xor](#fetch_xor)|針對指定的值和儲存的值執行位互斥 or。|
|[is_lock_free](#is_lock_free)|指定上的不可部分完成作業是否 **`this`** 為*鎖定可用*。 如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」**。|
|[載入](#load)|讀取並傳回預存值。|
|[存放區](#store)|使用指定的值來取代預存值。|

## <a name="remarks"></a>備註

類型*Ty*必須是*完整可複製*。 也就是說，使用[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)來複製其位元組，必須產生與原始物件比較的有效*Ty*物件。 [Compare_exchange_weak](#compare_exchange_weak)和[compare_exchange_strong](#compare_exchange_strong)成員函式會使用[Memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)來判斷兩個*Ty*值是否相等。 這些函數不會使用*Ty*定義的 `operator==` 。 的成員函式 `atomic` 用 `memcpy` 來複製*Ty*類型的值。

所有指標類型都有部分特製**化（ \<Ty \*> 不可部分完成）存在**。 特製化可以將位移加入 Managed 指標值，或從中減去位移。 算數運算接受類型的引數 `ptrdiff_t` ，並根據*Ty*大小調整該引數，使其與一般位址算術一致。

除了以外，每個整數類型都有特製化 **`bool`** 。 每個特製化都會提供一組豐富的方法來進行不可部分完成算術和邏輯作業。

||||
|-|-|-|
|**不可部分完成\<char>**|**不可部分完成\<signed char>**|**不可部分完成\<unsigned char>**|
|**不可部分完成\<char16_t>**|**不可部分完成\<char32_t>**|**不可部分完成\<wchar_t>**|
|**不可部分完成\<short>**|**不可部分完成\<unsigned short>**|**不可部分完成\<int>**|
|**不可部分完成\<unsigned int>**|**不可部分完成\<long>**|**不可部分完成\<unsigned long>**|
|**不可部分完成\<long long>**|**不可部分完成\<unsigned long long>**|

整數特製化衍生自對應的 `atomic_integral` 類型。 例如 **， \<unsigned int> 不可部分完成的衍生**自 `atomic_uint` 。

## <a name="requirements"></a>需求

**標頭：**\<atomic>

**命名空間：** std

## <a name="atomicatomic"></a><a name="atomic"></a>不可部分完成：：不可部分完成

建構不可部分完成物件。

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>參數

*Value*\
初始化值。

### <a name="remarks"></a>備註

不可部分完成的物件無法複製或移動。

屬於不可部分完成實例的物件，只能 \<*Ty*> 由接受*Ty*類型之引數的函式初始化，而不是使用匯總初始化。 不過，只能使用匯總初始化來初始化 atomic_integral 物件。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="atomicoperator-ty"></a><a name="op_ty"></a>不可部分完成：： operator *Ty*

指定給範本之類型的運算子（不可部分完成） \<*Ty*> 。 抓取** \* 這個**中的預存值。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>備註

此運算子會套用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_eq"></a>不可部分完成：： operator =

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

*Value*\
*Ty*物件。

### <a name="return-value"></a>傳回值

傳回*值*。

## <a name="atomicoperator"></a><a name="op_inc"></a>不可部分完成：： operator + +

遞增預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞增的值。最後兩個運算子會傳回增量之前的值。 運算子會使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_add_eq"></a>不可部分完成：： operator + =

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

*Value*\
整數或指標值。

### <a name="return-value"></a>傳回值

包含加法結果的*Ty*物件。

### <a name="remarks"></a>備註

此運算子會使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator--"></a><a name="op_dec"></a>不可部分完成：： operator--

遞減預存值。 僅供整數和指標特製化使用。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>傳回值

前兩個運算子會傳回遞減的值。最後兩個運算子會傳回遞減之前的值。 運算子會使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator-"></a><a name="op_sub_eq"></a>不可部分完成：： operator-=

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

*Value*\
整數或指標值。

### <a name="return-value"></a>傳回值

包含減法結果的*Ty*物件。

### <a name="remarks"></a>備註

此運算子會使用 `memory_order_seq_cst` [memory_order](atomic-enums.md)。

## <a name="atomicoperator"></a><a name="op_and_eq"></a>不可部分完成：： operator&=

針對指定的值和** \* 這個**的儲存值執行位 and。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*Value*\
*Ty*類型的值。

### <a name="return-value"></a>傳回值

位 and 的結果。

### <a name="remarks"></a>備註

這個運算子會執行讀取-修改-寫入作業，以在 memory_order 的條件約束中，將** \* 這個**的儲存值取代為*值*的位 and，以及儲存在** \* 這個**中的目前值 `memory_order_seq_cst` [ ](atomic-enums.md)。

## <a name="atomicoperator124"></a><a name="op_or_eq"></a>不可部分完成：： operator&#124;=

針對指定的值和** \* 這個**的儲存值執行位 or。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*Value*\
*Ty*類型的值。

### <a name="return-value"></a>傳回值

位 or 的結果。

### <a name="remarks"></a>備註

這個運算子會執行讀取-修改-寫入作業，以將** \* 這個**的儲存值取代為*值*的位 or，並在 memory_order 條件約束的條件約束內，以儲存在** \* 這個**中的目前值 `memory_order_seq_cst` [memory_order](atomic-enums.md) 。

## <a name="atomicoperator"></a><a name="op_xor_eq"></a>不可部分完成：： operator ^ =

針對指定的值和** \* 這個**的儲存值執行位互斥 or。 僅供整數特製化使用。

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>參數

*Value*\
*Ty*類型的值。

### <a name="return-value"></a>傳回值

位互斥 or 的結果。

### <a name="remarks"></a>備註

這個運算子會執行讀取-修改-寫入作業，將** \* 這個**的儲存值取代為*值*的位排除** \* or，並**在 `memory_order_seq_cst` [memory_order](atomic-enums.md)條件約束的條件約束中，將這個的目前值替換為。

## <a name="atomiccompare_exchange_strong"></a><a name="compare_exchange_strong"></a>不可部分完成：： compare_exchange_strong

對** \* 這個**執行不可部分完成的比較和交換作業。

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

*Exp*\
*Ty*類型的值。

*Value*\
*Ty*類型的值。

*Order1*\
第一個 `memory_order` 引數。

*Order2*\
第二個 `memory_order` 引數。

### <a name="return-value"></a>傳回值

**`bool`**，表示值比較的結果。

### <a name="remarks"></a>備註

這個不可部分完成的比較和交換作業會將儲存在** \* 此**中的值與*Exp*進行比較。如果值相等，作業會使用讀取-修改-寫入作業，並套用*Order1*所指定的記憶體順序條件約束，將儲存在** \* 這個**中的值取代為*值*。 如果值不相等，作業會使用儲存在** \* 這個**中的值來取代*Exp* ，並套用*Order2*所指定的記憶體順序條件約束。

沒有第二個的多載 `memory_order` 會使用以*Order1*值為基礎的隱含*Order2* 。 如果*Order1*為 `memory_order_acq_rel` ，則*Order2*為 `memory_order_acquire` 。 如果*Order1*為 `memory_order_release` ，則*Order2*為 `memory_order_relaxed` 。 在所有其他情況下， *Order2*等於*Order1*。

對於採用兩個參數的多載 `memory_order` ， *Order2*的值不得為 `memory_order_release` 或 `memory_order_acq_rel` ，而且不得比*Order1*的值更強。

## <a name="atomiccompare_exchange_weak"></a><a name="compare_exchange_weak"></a>不可部分完成：： compare_exchange_weak

執行** \* 這個**的弱式不可部分完成比較和交換作業。

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

*Exp*\
*Ty*類型的值。

*Value*\
*Ty*類型的值。

*Order1*\
第一個 `memory_order` 引數。

*Order2*\
第二個 `memory_order` 引數。

### <a name="return-value"></a>傳回值

**`bool`**，表示值比較的結果。

### <a name="remarks"></a>備註

這個不可部分完成的比較和交換作業會將儲存在** \* 此**中的值與*Exp*進行比較。如果值相等，作業會使用讀取-修改-寫入作業，並套用*Order1*所指定的記憶體順序條件約束，將儲存在** \* 這個**中的值取代為*值*。 如果值不相等，作業會使用儲存在** \* 這個**中的值來取代*Exp* ，並套用*Order2*所指定的記憶體順序條件約束。

如果比較的值相等，則「弱式」不可部分完成比較和交換作業會執行交換。 如果值不相等，則不保證會執行交換。

沒有第二個的多載 `memory_order` 會使用以*Order1*值為基礎的隱含*Order2* 。 如果*Order1*為 `memory_order_acq_rel` ，則*Order2*為 `memory_order_acquire` 。 如果*Order1*為 `memory_order_release` ，則*Order2*為 `memory_order_relaxed` 。 在所有其他情況下， *Order2*等於*Order1*。

對於採用兩個參數的多載 `memory_order` ， *Order2*的值不得為 `memory_order_release` 或 `memory_order_acq_rel` ，而且不得比*Order1*的值更強。

## <a name="atomicexchange"></a><a name="exchange"></a>不可部分完成：： exchange

使用指定的值來取代** \* 這個**的儲存值。

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

** \* 在交換之前的**儲存值。

### <a name="remarks"></a>備註

這項作業會執行「讀取-修改-寫入」作業，以在依*順序*指定的記憶體條件約束內，使用*值*來取代儲存在** \* 這個**中的值。

## <a name="atomicfetch_add"></a><a name="fetch_add"></a>不可部分完成：： fetch_add

提取儲存在** \* 這個**中的值，然後將指定的值加入至預存值。

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

*Ty*物件，其中包含在加入之前儲存在** \* 這個**中的值。

### <a name="remarks"></a>備註

`fetch_add`方法會執行讀取-修改-寫入作業，以將*值*以自動方式加入** \* 此**中的預存值，並套用依*順序*指定的記憶體條件約束。

## <a name="atomicfetch_and"></a><a name="fetch_and"></a>不可部分完成：： fetch_and

對值和儲存在** \* 這個**中的現有值執行位 and。

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

*Ty*物件，其中包含位 and 的結果。

### <a name="remarks"></a>備註

`fetch_and`方法會執行讀取-修改-寫入作業，以依*順序*指定的記憶體條件約束，將** \* 這個**的儲存值取代為*值*的位 and，以及儲存在** \* 這個**中的目前值。

## <a name="atomicfetch_or"></a><a name="fetch_or"></a>不可部分完成：： fetch_or

對值和儲存在** \* 這個**中的現有值執行位 or。

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

包含位 or 結果的*Ty*物件。

### <a name="remarks"></a>備註

`fetch_or`方法會執行讀取-修改-寫入作業，以依*順序*指定的記憶體條件約束，將** \* 這個**的儲存值取代為*值*的位 or，以及儲存在** \* 這個**中的目前值。

## <a name="atomicfetch_sub"></a><a name="fetch_sub"></a>不可部分完成：： fetch_sub

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

包含減法結果的*Ty*物件。

### <a name="remarks"></a>備註

`fetch_sub`方法會執行讀取-修改-寫入作業，以在*順序*指定的記憶體條件約束內，以自動方式減去** \* 這個**中儲存值的*值*。

## <a name="atomicfetch_xor"></a><a name="fetch_xor"></a>不可部分完成：： fetch_xor

執行位排除 or 的值，以及儲存在** \* 這個**中的現有值。

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

*Value*\
*Ty*類型的值。

*即可*\
`memory_order`。

### <a name="return-value"></a>傳回值

包含位排除 or 之結果的*Ty*物件。

### <a name="remarks"></a>備註

`fetch_xor`方法會執行讀取-修改-寫入作業，將** \* 這個**的儲存值取代為*值*的位排除 or，以及儲存在** \* 這個**中的目前值，並套用依*順序*指定的記憶體條件約束。

## <a name="atomicis_lock_free"></a><a name="is_lock_free"></a>不可部分完成：： is_lock_free

指定** \* 此**上的不可部分完成作業是否為無鎖定。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>傳回值

如果** \* 這個**上的不可部分完成的作業是無鎖定，則為 true，否則為 false。

### <a name="remarks"></a>備註

如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」。

## <a name="atomicload"></a><a name="load"></a>不可部分完成：： load

在指定的記憶體條件約束內，抓取** \* 這個**中的預存值。

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>參數

*即可*\
`memory_order`。 *順序*不得為 `memory_order_release` 或 `memory_order_acq_rel` 。

### <a name="return-value"></a>傳回值

儲存在** \* 這個**中的已抓取值。

## <a name="atomicstore"></a><a name="store"></a>不可部分完成：： store

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

*Value*\
*Ty*物件。

*即可*\
`memory_order`條件約束。

### <a name="remarks"></a>備註

此成員函式會*Value*在 **`*this`** 依*順序*指定的記憶體條件約束內，以原子方式儲存的值。

## <a name="see-also"></a>另請參閱

[\<atomic>](../standard-library/atomic.md)\
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
