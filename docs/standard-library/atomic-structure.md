---
title: "atomic 結構 | Microsoft Docs"
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
  - "atomic/std::atomic"
dev_langs: 
  - "C++"
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atomic 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述物件在型別 `Ty`儲存值的元素不可部分完成的作業。  
  
## 語法  
  
```  
template <class Ty>  
struct atomic;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[atomic::atomic 建構函式](../Topic/atomic::atomic%20Constructor.md)|建構一個不可部分完成的物件。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[atomic::operator Ty 運算子](../Topic/atomic::operator%20Ty%20Operator.md)|讀取並回傳已儲存的值。\([atomic::load 方法](../Topic/atomic::load%20Method.md)\)|  
|[atomic::operator\= 運算子](../Topic/atomic::operator=%20Operator.md)|使用指定的值取代所儲存的值。\([atomic::store 方法](../Topic/atomic::store%20Method.md)\)|  
|||  
|[atomic::operator\+\+ 運算子](../Topic/atomic::operator++%20Operator.md)|增加儲存的值。  只能由整數和指標特製化。|  
|[atomic::operator\+\= 運算子](../Topic/atomic::operator+=%20Operator.md)|增加指定值加至儲存的值。  只能由整數和指標特製化。|  
|[atomic::operator\-\- 運算子](../Topic/atomic::operator--%20Operator.md)|減少儲存的值。  只能由整數和指標特製化。|  
|[atomic::operator\-\= 運算子](../Topic/atomic::operator-=%20Operator.md)|從儲存的值減去某個值。  只能由整數和指標特製化。|  
|[atomic::operator&\= 運算子](../Topic/atomic::operator&=%20Operator.md)|對指定值與儲存值執行位元 `and` 。  為整數限定使用。|  
|[atomic::operator&#124;\= 運算子](../Topic/atomic::operator%7C=%20Operator.md)|對指定值與儲存值執行位元 `or`。  為整數限定使用。|  
|[atomic::operator^\= 運算子](../Topic/atomic::operator%5E=%20Operator.md)|對指定值與儲存值執行位元 `exclusive or` 。  為整數限定使用。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[atomic::compare\_exchange\_strong 方法](../Topic/atomic::compare_exchange_strong%20Method.md)|會在 `this` 上的 `atomic_compare_and_exchange` 作業並傳回結果。|  
|[atomic::compare\_exchange\_weak 方法](../Topic/atomic::compare_exchange_weak%20Method.md)|會在 `this` 上的 `weak_atomic_compare_and_exchange` 作業並傳回結果。|  
|[atomic::fetch\_add 方法](../Topic/atomic::fetch_add%20Method.md)|增加指定值加至儲存的值。|  
|[atomic::fetch\_and 方法](../Topic/atomic::fetch_and%20Method.md)|對指定值與儲存值執行位元 `and` 。|  
|[atomic::fetch\_or 方法](../Topic/atomic::fetch_or%20Method.md)|對指定值與儲存值執行位元 `or`。|  
|[atomic::fetch\_sub 方法](../Topic/atomic::fetch_sub%20Method.md)|從儲存的值減去某個值。|  
|[atomic::fetch\_xor 方法](../Topic/atomic::fetch_xor%20Method.md)|對指定值與儲存值執行位元 `exclusive or` 。|  
|[atomic::is\_lock\_free 方法](../Topic/atomic::is_lock_free%20Method.md)|指定 `this` 的不可部分完成的作業是否已 *無鎖定*。  如果該型別使用的不可部分完成的作業不會鎖定，原子型別是 *無鎖定* 。|  
|[atomic::load 方法](../Topic/atomic::load%20Method.md)|讀取並回傳已儲存的值。|  
|[atomic::store 方法](../Topic/atomic::store%20Method.md)|使用指定的值取代所儲存的值。|  
  
## 備註  
 `Ty` 型別 *一般來說可複製*。  也就是使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 複製的位元組必須產生有效的 `Ty` 物件，其相比較等於原始物件。  `compare_exchange_weak` 和 `compare_exchange_strong` 成員函式使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 來判斷兩個 `Ty` 值是否相等。  這些函式不會使用 `Ty` 中定義的 `operator==`。  `atomic` 的成員函式使用 `memcpy` 複製 `Ty`型別的值。  
  
 部分特製化，則為 `atomic<Ty *>`，存在於任何指標型別。  特製化啟用位移加入 Managed 指標值或減去其指定的位移。  算術運算接受一個型別 `ptrdiff_t` 之引數和根據 `Ty` 大小調整至該引數一致與泛型位址算術。  
  
 特製化存在於除了 `bool`的每個整數型別。  每個特製化為不可部分完成的算術和邏輯作業提供相當豐富的方法。  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 整數特製化從對應的 `atomic_``integral` 型別衍生。  例如，`atomic<unsigned int>` 是從 `atomic_uint` 衍生而來。  
  
## 需求  
 **標頭：**atomic  
  
 **命名空間:** std  
  
## 請參閱  
 [\<atomic\>](../standard-library/atomic.md)   
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)