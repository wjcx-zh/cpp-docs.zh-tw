---
title: "&lt;atomic&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<atomic>"
  - "atomic/std::atomic_int_least32_t"
  - "atomic/std::atomic_ullong"
  - "atomic/std::atomic_ptrdiff_t"
  - "atomic/std::atomic_char16_t"
  - "atomic/std::atomic_schar"
  - "atomic/std::atomic_ulong"
  - "atomic/std::atomic_uint_fast32_t"
  - "atomic/std::atomic_uint8_t"
  - "atomic/std::atomic_int32_t"
  - "atomic/std::atomic_uint_fast64_t"
  - "atomic/std::atomic_uint32_t"
  - "atomic/std::atomic_int16_t"
  - "atomic/std::atomic_uintmax_t"
  - "atomic/std::atomic_intmax_t"
  - "atomic/std::atomic_long"
  - "atomic/std::atomic_int"
  - "atomic/std::atomic_uint_least8_t"
  - "atomic/std::atomic_size_t"
  - "atomic/std::atomic_uint_fast16_t"
  - "atomic/std::atomic_wchar_t"
  - "atomic/std::atomic_int_fast64_t"
  - "atomic/std::atomic_uint_fast8_t"
  - "atomic/std::atomic_int_fast8_t"
  - "atomic/std::atomic_intptr_t"
  - "atomic/std::atomic_uint"
  - "atomic/std::atomic_uint16_t"
  - "atomic/std::atomic_char32_t"
  - "atomic/std::atomic_uint64_t"
  - "atomic/std::atomic_ushort"
  - "atomic/std::atomic_int_least16_t"
  - "atomic/std::atomic_char"
  - "atomic/std::atomic_uint_least32_t"
  - "atomic/std::atomic_uintptr_t"
  - "atomic/std::atomic_short"
  - "atomic/std::atomic_llong"
  - "atomic/std::atomic_uint_least16_t"
  - "atomic/std::atomic_int_fast16_t"
  - "atomic/std::atomic_int_least8_t"
  - "atomic/std::atomic_int_least64_t"
  - "atomic/std::atomic_int_fast32_t"
  - "atomic/std::atomic_uchar"
  - "atomic/std::atomic_int8_t"
  - "atomic/std::atomic_int64_t"
  - "atomic/std::atomic_uint_least64_t"
dev_langs: 
  - "C++"
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 22
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;atomic&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義類別和使用的樣板類別建立支援不可部分完成的作業的類型。  
  
## 語法  
  
```cpp  
#include <atomic>  
```  
  
## 備註  
  
> [!NOTE]
>  使用 **\/clr** 或 **\/clr:pure**，以編譯的程式碼，這個標題會封鎖。  
  
 不可部分完成的作業可以協助您使用多執行緒正確操作物件，而不需要使用 Mutex 鎖定的兩個主要屬性。  
  
-   由於不可部分完成的作業不能的，相同物件的第二個原子作業從不同的執行緒可能在第一個不可部分完成的作業前後只取得物件的狀態。  
  
-   根據其 [memory\_order](../Topic/memory_order%20Enum.md) 引數，不可部分完成的作業在相同執行緒上建立其他不可部分完成的作業效果的可視性的定序需求。  因此，它禁止違反定序需求的編譯器最佳化。  
  
 在某些平台上，有效率地實作某些型別不可部分完成的作業可能是不可能的，而不使用 `mutex` 鎖定。  如果該型別使用的不可部分完成的作業不會鎖定，原子型別是 *無鎖定* 。  
  
 [atomic\_flag](../standard-library/atomic-flag-structure.md) 類別提供保留 `bool` 旗標的較小的原子型別。  它的作業永遠是無鎖定。  
  
 樣板類別 `atomic<Ty>` 儲存其引數型別 `Ty` 物件與提供之不可部分完成存取儲存的值。  您可以執行個體化就可以使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)，可以複製使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 和相等的所測試的任何型別。  特別是，您可以將它與符合這些需求和，在許多情況下，使用浮點型別的使用者定義型別。  
  
 範本也有一組整數型別的特製化和指標的部分特製化。  這些特製化的無法透過主要樣板的其他作業。  
  
## 指標特製化  
 對任何指標型別的 `atomic<Ty *>` 部分特製化應用程式。  它們為指標算術提供方法。  
  
## 整數特製化  
 `atomic<integral>` 特製化適用於所有整數型別。  它們提供無法透過主要樣板的其他作業。  
  
 每個 `atomic<integral>` 型別具有您在 `if directive` 可以用來判斷在編譯時期的對應巨集在該型別的作業是否已鎖定。  如果巨集的值為零，在型別的作業不是無鎖定。  如果值為 1，作業可能是無鎖定，因此，需要執行階段檢查。  如果值為 2，表示作業已鎖定。  您可以使用 `atomic_is_lock_free` 函式來判斷在執行階段在型別的作業是否已鎖定。  
  
 對於每一個整數型別，則處理該整數型別物件的對應的具名原子型別。  每個 `atomic_integral` 型別具有相同的一組成員函式與 `atomic<Ty>` 對應的執行個體化，而且可以傳遞至任何原子非成員函式。  
  
|`atomic_integral` 型別|整數類資料型別|`atomic_is_lock_free` 巨集|  
|--------------------------|-------------|------------------------------|  
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|  
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|  
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|  
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|  
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|  
  
 Typedef 名稱為不可部分完成的樣板之特製化在標題 \<inttypes.h 定義的某些存在的型別。\>  
  
|原子型別|Typedef 名稱|  
|----------|----------------|  
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
  
## Structs  
  
|Name|說明|  
|----------|--------|  
|[atomic 結構](../standard-library/atomic-structure.md)|描述物件儲存於中的值執行不可部分完成的作業。|  
|[atomic\_flag 結構](../standard-library/atomic-flag-structure.md)|描述原子集合和清除 `bool` 旗標的物件。|  
  
## 列舉  
  
|Name|說明|  
|----------|--------|  
|[memory\_order 列舉](../Topic/memory_order%20Enum.md)|提供在記憶體位置對於同步作業處理的符號名稱。  這些作業會影響執行緒的工作方式變成也可在其他執行緒看見。|  
  
## 函式  
 下列清單中， `_explicit` 不結束函式有對應的 `_explicit`的語意，不過，它們會隱含 [memory\_order](../Topic/memory_order%20Enum.md)`memory_order_seq_cst`的引數。  
  
|Name|說明|  
|----------|--------|  
|[atomic\_compare\_exchange\_strong 函式](../Topic/atomic_compare_exchange_strong%20Function.md)|執行 *不可部分完成的比較和交換* 作業。|  
|[atomic\_compare\_exchange\_strong\_explicit 函式](../Topic/atomic_compare_exchange_strong_explicit%20Function.md)|執行 *不可部分完成的比較和交換* 作業。|  
|[atomic\_compare\_exchange\_weak 函式](../Topic/atomic_compare_exchange_weak%20Function.md)|執行 *弱式不可部分完成比較和交換* 作業。|  
|[atomic\_compare\_exchange\_weak\_explicit 函式](../Topic/atomic_compare_exchange_weak_explicit%20Function.md)|執行 *弱式不可部分完成比較和交換* 作業。|  
|[atomic\_exchange 函式](../Topic/atomic_exchange%20Function.md)|取代所儲存的值。|  
|[atomic\_exchange\_explicit 函式](../Topic/atomic_exchange_explicit%20Function.md)|取代所儲存的值。|  
|[atomic\_fetch\_add 函式](../Topic/atomic_fetch_add%20Function.md)|將值加入至現有的儲存值。|  
|[atomic\_fetch\_add\_explicit 函式](../Topic/atomic_fetch_add_explicit%20Function.md)|將值加入至現有的儲存值。|  
|[atomic\_fetch\_and 函式](../Topic/atomic_fetch_and%20Function.md)|執行指定的值和現有的儲存值執行位元 `and` 。|  
|[atomic\_fetch\_and\_explicit 函式](../Topic/atomic_fetch_and_explicit%20Function.md)|執行指定的值和現有的儲存值執行位元 `and` 。|  
|[atomic\_fetch\_or 函式](../Topic/atomic_fetch_or%20Function.md)|執行指定的值和現有的儲存值執行位元 `or` 。|  
|[atomic\_fetch\_or\_explicit 函式](../Topic/atomic_fetch_or_explicit%20Function.md)|執行指定的值和現有的儲存值執行位元 `or` 。|  
|[atomic\_fetch\_sub 函式](../Topic/atomic_fetch_sub%20Function.md)|從現有的儲存值減去某個值。|  
|[atomic\_fetch\_sub\_explicit 函式](../Topic/atomic_fetch_sub_explicit%20Function.md)|從現有的儲存值減去某個值。|  
|[atomic\_fetch\_xor 函式](../Topic/atomic_fetch_xor%20Function.md)|執行指定的值和現有的儲存值執行位元 `exclusive or` 。|  
|[atomic\_fetch\_xor\_explicit 函式](../Topic/atomic_fetch_xor_explicit%20Function.md)|執行指定的值和現有的儲存值執行位元 `exclusive or` 。|  
|[atomic\_flag\_clear 函式](../Topic/atomic_flag_clear%20Function.md)|設定在 `atomic_flag` 物件中的旗標設為 `false`。|  
|[atomic\_flag\_clear\_explicit 函式](../Topic/atomic_flag_clear_explicit%20Function.md)|設定在 `atomic_flag` 物件中的旗標設為 `false`。|  
|[atomic\_flag\_test\_and\_set 函式](../Topic/atomic_flag_test_and_set%20Function.md)|設定在 `atomic_flag` 物件中的旗標設為 `true`。|  
|[atomic\_flag\_test\_and\_set\_explicit 函式](../Topic/atomic_flag_test_and_set_explicit%20Function.md)|設定在 `atomic_flag` 物件中的旗標設為 `true`。|  
|[atomic\_init 函式](../Topic/atomic_init%20Function.md)|設定 `atomic` 物件中儲存的值。|  
|[atomic\_is\_lock\_free 函式](../Topic/atomic_is_lock_free%20Function.md)|指定在指定物件的不可部分完成的作業是否已鎖定。|  
|[atomic\_load 函式](../Topic/atomic_load%20Function.md)|元素擷取值。|  
|[atomic\_load\_explicit 函式](../Topic/atomic_load_explicit%20Function.md)|元素擷取值。|  
|[atomic\_signal\_fence 函式](../Topic/atomic_signal_fence%20Function.md)|為在呼叫的執行緒建立記憶體在柵欄之間的定序需求有訊號處理常式會執行在相同執行緒上 *柵欄* 。|  
|[atomic\_store 函式](../Topic/atomic_store%20Function.md)|儲存原子值。|  
|[atomic\_store\_explicit 函式](../Topic/atomic_store_explicit%20Function.md)|儲存原子值。|  
|[atomic\_thread\_fence 函式](../Topic/atomic_thread_fence%20Function.md)|為建立記憶體定序需求。如需其他柵欄的 *柵欄* 。|  
|[kill\_dependency 函式](../Topic/kill_dependency%20Function.md)|中斷一種可能的相依性鏈結中。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)