---
title: '&lt;atomic&gt;'
description: 描述 Standard c + + 程式庫不可部分完成標頭中可用的類型和函式。
ms.date: 12/06/2019
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
ms.openlocfilehash: 3c5f732dbda701eb7744b1b25a9a8e7426f7a3e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203894"
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

定義類別和類別範本，用來建立支援不可部分完成作業的類型。

## <a name="syntax"></a>語法

```cpp
#include <atomic>
```

## <a name="remarks"></a>備註

> [!NOTE]
> 在使用[/clr： pure](../build/reference/clr-common-language-runtime-compilation.md)編譯的程式碼中，此標頭會遭到封鎖。 **/Clr： pure**和 **/clr： safe**都會在 Visual Studio 2017 和更新版本中被取代。

不可部分完成作業有兩個重要屬性，可協助您使用多個執行緒來正確操作物件，而不使用 Mutex 鎖定。

- 因為不可部分完成的作業是不可分割，所以來自不同執行緒的相同物件上的第二個不可部分完成作業，只能在第一個不可部分完成的作業之前或之後取得物件的狀態。

- 根據其 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引數，不可部分完成作業會建立相同執行緒中其他不可部分完成作業影響可見性的順序需求。 因此，它會禁止違反排序需求的編譯器最佳化。

在部分平台上，如果不使用 `mutex` 鎖定，則可能無法有效率地實作某些類型的不可部分完成作業。 如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」**。

**C + + 11**：在信號處理常式中， `obj` 如果 `obj.is_lock_free()` 或為 true，您可以在物件上執行不可部分完成的作業 `atomic_is_lock_free(x)` 。

類別[atomic_flag](../standard-library/atomic-flag-structure.md)會提供包含旗標的最少不可部分完成類型 **`bool`** 。 它的作業永遠是無鎖定。

類別樣板 `atomic<T>` 會儲存其引數類型的物件 `T` ，並提供該預存值的不可部分完成存取權。 您可以將它具現化，方法是使用可使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 進行複製以及使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 測試是否相等的任何類型。 特別的是，您可以將它與符合這些需求的使用者定義類型搭配使用，而且在許多情況下，也可以與浮點類型搭配使用。

範本也會有一組整數類型的特製化以及指標的部分特製化。 這些特製化提供無法透過主要範本使用的其他作業。

## <a name="pointer-specializations"></a>指標特製化

`atomic<T *>` 部分特製化會套用至所有指標類型。 它們提供方法來執行指標算術。

## <a name="integral-specializations"></a>整數特製化

`atomic<integral>` 特製化會套用至所有整數類型。 它們會提供無法透過主要範本提供的其他作業。

每個 `atomic<integral>` 類型都會有對應巨集，可在 `if directive` 中用來判斷該類型上的作業在編譯時期是否無鎖定。 如果宏的值為零，則類型上的作業不會無鎖定。 如果值為 1，作業可能是無鎖定，而且需要執行階段檢查。 如果值為 2，作業是無鎖定。 您可以使用函式 `atomic_is_lock_free`，在執行階段決定類型上的作業是否無鎖定。

針對每個整數類資料類型，有一個對應的命名不可部分完成類型，可管理該整數類型的物件。 每個 `atomic_integral` 類型都會有一組與對應 `atomic<T>` 具現化相同的成員函式，而且可以傳遞給任何非成員不可部分完成函式。

|`atomic_integral` 類型|整數類型|`atomic_is_lock_free` 巨集|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|**`char`**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_schar`|**`signed char`**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_uchar`|**`unsigned char`**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_char16_t`|**`char16_t`**|ATOMIC_CHAR16_T_LOCK_FREE|
|`atomic_char32_t`|**`char32_t`**|ATOMIC_CHAR32_T_LOCK_FREE|
|`atomic_wchar_t`|**`wchar_t`**|ATOMIC_WCHAR_T_LOCK_FREE|
|`atomic_short`|**`short`**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_ushort`|**`unsigned short`**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_int`|**`int`**|ATOMIC_INT_LOCK_FREE|
|`atomic_uint`|**`unsigned int`**|ATOMIC_INT_LOCK_FREE|
|`atomic_long`|**`long`**|ATOMIC_LONG_LOCK_FREE|
|`atomic_ulong`|**`unsigned long`**|ATOMIC_LONG_LOCK_FREE|
|`atomic_llong`|**`long long`**|ATOMIC_LLONG_LOCK_FREE|
|`atomic_ullong`|**`unsigned long long`**|ATOMIC_LLONG_LOCK_FREE|

在標頭中定義的部分類型中，不明確樣板的特製化會有 Typedef 名稱 \<inttypes.h> 。

|不可部分完成類型|typedef 名稱|
|-----------------|------------------|
|`atomic_int8_t`|`atomic<int8_t>`|
|`atomic_uint8_t`|`atomic<uint8_t>`|
|`atomic_int16_t`|`atomic<int16_t>`|
|`atomic_uint16_t`|`atomic<uint16_t>`|
|`atomic_int32_t`|`atomic<int32_t>`|
|`atomic_uint32_t`|`atomic<uint32_t>`|
|`atomic_int64_t`|`atomic<int64_t>`|
|`atomic_uint64_t`|`atomic<uint64_t>`|
|`atomic_int_least8_t`|`atomic<int_least8_t>`|
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|
|`atomic_int_least16_t`|`atomic<int_least16_t>`|
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|
|`atomic_int_least32_t`|`atomic<int_least32_t>`|
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|
|`atomic_int_least64_t`|`atomic<int_least64_t>`|
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|
|`atomic_intptr_t`|`atomic<intptr_t>`|
|`atomic_uintptr_t`|`atomic<uintptr_t>`|
|`atomic_size_t`|`atomic<size_t>`|
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|
|`atomic_intmax_t`|`atomic<intmax_t>`|
|`atomic_uintmax_t`|`atomic<uintmax_t>`|

## <a name="structs"></a>結構

|名稱|說明|
|----------|-----------------|
|[atomic 結構](../standard-library/atomic-structure.md)|描述在預存值上執行不可部分完成作業的物件。|
|[atomic_flag 結構](../standard-library/atomic-flag-structure.md)|描述可自動設定和清除旗標的物件 **`bool`** 。|

## <a name="enums"></a>列舉

|名稱|說明|
|----------|-----------------|
|[memory_order 列舉](../standard-library/atomic-enums.md#memory_order_enum)|為記憶體位置上的同步處理作業提供符號名稱。 這些作業會影響一個執行緒的指派如何在其他執行緒中變成可見。|

## <a name="functions"></a>函式

在下列清單中，不是以結尾的函 `_explicit` 式具有對應的的語義 `_explicit` ，不同之處在于它們具有的隱含[memory_order](../standard-library/atomic-enums.md#memory_order_enum)引數 `memory_order_seq_cst` 。

|名稱|說明|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|執行不可部分完成的*比較和交換*作業。|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|執行不可部分完成的*比較和交換*作業。|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|執行「弱式不可部分完成比較和交換」** 作業。|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|執行「弱式不可部分完成比較和交換」** 作業。|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|取代預存值。|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|取代預存值。|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|將指定的值加入現有預存值。|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|將指定的值加入現有預存值。|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|對指定的值和現有預存值執行位元 `and`。|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|對指定的值和現有預存值執行位元 `and`。|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|對指定的值和現有預存值執行位元 `or`。|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|對指定的值和現有預存值執行位元 `or`。|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|將現有預存值減去指定的值。|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|將現有預存值減去指定的值。|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|對指定的值和現有預存值執行位元 `exclusive or`。|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|對指定的值和現有預存值執行位元 `exclusive or`。|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|將物件中的旗標設定 `atomic_flag` 為 **`false`** 。|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|將物件中的旗標設定 `atomic_flag` 為 **`false`** 。|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|將物件中的旗標設定 `atomic_flag` 為 **`true`** 。|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|將物件中的旗標設定 `atomic_flag` 為 **`true`** 。|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|設定 `atomic` 物件中的預存值。|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|指定所指定物件上的不可部分完成作業是否為「無鎖定」。|
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|以不可部分完成的方式擷取值。|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|以不可部分完成的方式擷取值。|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|作為「範圍」**，可在下列範圍之間建立記憶體順序需求：具有相同執行緒中所執行訊號處理常式之呼叫執行緒中的範圍。|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|以不可部分完成的方式儲存值。|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|以不可部分完成的方式儲存值。|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|作為「範圍」**，可建立與其他範圍有關的記憶體順序需求。|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|中斷可能的相依性鏈結。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
