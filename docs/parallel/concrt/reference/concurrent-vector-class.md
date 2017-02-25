---
title: "concurrent_vector 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_vector/Concurrency::concurrent_vector"
  - "concurrent_vector/concurrency::concurrent_vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_vector 類別"
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# concurrent_vector 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_vector` 類別序列容器類別，允許以隨機方式存取任何項目。  它可讓並行存取之附加項目存取、 iterator 存取，以及 iterator 周遊作業。  
  
## 語法  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_vector: protected details::_Allocator_base<_Ty, _Ax>, private details::_Concurrent_vector_base_v4;  
```  
  
#### 參數  
 `_Ty`  
 要儲存在向量中的資料類型。  
  
 `_Ax`  
 代表預存配置器物件 \(此物件會封裝有關配置和解除配置並行向量之記憶體的詳細資訊\) 的型別。  此引數是選擇性的，而且預設值是 `allocator<``_Ty``>`。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`allocator_type`|型別，代表並行向量的配置器類別。|  
|`const_iterator`|型別，提供隨機存取 Iterator，可以讀取並行向量中的 `const` 項目。|  
|`const_pointer`|型別，提供並行向量中的 `const` 項目的指標。|  
|`const_reference`|型別，針對存放在並行向量中的 `const` 項目提供參考，以讀取及執行 `const` 作業。|  
|`const_reverse_iterator`|型別，提供隨機存取 Iterator，可以讀取並行向量中任何 `const` 項目。|  
|`difference_type`|型別，針對並行向量中兩個項目之間提供帶正負號的距離。|  
|`iterator`|型別，提供隨機存取 Iterator，可以讀取並行向量中的任何項目。  使用 Iterator 修改項目不具並行安全。|  
|`pointer`|型別，提供並行向量中項目的指標。|  
|`reference`|型別，針對存放在並行向量中的項目提供參考。|  
|`reverse_iterator`|型別，提供隨機存取 Iterator，可以讀取反向並行向量中的任何項目。  使用 Iterator 修改項目不具並行安全。|  
|`size_type`|型別，會計算並行向量中的項目數量。|  
|`value_type`|型別，代表存放在並行向量中的資料類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_vector::concurrent\_vector 建構函式](../Topic/concurrent_vector::concurrent_vector%20Constructor.md)|多載。  建構並行的向量。|  
|[concurrent\_vector::~concurrent\_vector 解構函式](../Topic/concurrent_vector::~concurrent_vector%20Destructor.md)|會清除所有項目並終結這個並行向量。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_vector::assign 方法](../Topic/concurrent_vector::assign%20Method.md)|多載。  會清除並行向量的項目，並指派 `_Item` 的 `_N` 複本，或是由 Iterator 範圍 \[`_Begin`、`_End` \) 指定的值。  這個方法不是並行安全的。|  
|[concurrent\_vector::at 方法](../Topic/concurrent_vector::at%20Method.md)|多載。  提供存取並行向量中指定索引處的項目。  對讀取作業以及在擴充向量時，這個方法具備並行安全，只要能確保 `_Index` 值小於並行向量的大小。|  
|[concurrent\_vector::back 方法](../Topic/concurrent_vector::back%20Method.md)|多載。  傳回並行向量中最後一個項目的參考或 `const` 參考。  如果並行向量是空的，傳回值會是未定義的。  這個方法是並行安全的。|  
|[concurrent\_vector::begin 方法](../Topic/concurrent_vector::begin%20Method.md)|多載。  將 `iterator` 或 `const_iterator` 型別的 Iterator 傳回並行向量的開頭。  這個方法是並行安全的。|  
|[concurrent\_vector::capacity 方法](../Topic/concurrent_vector::capacity%20Method.md)|傳回並行向量不需配置更多記憶體即可成長的大小上限。  這個方法是並行安全的。|  
|[concurrent\_vector::cbegin 方法](../Topic/concurrent_vector::cbegin%20Method.md)|將 `const_iterator` 型別的 Iterator 傳回並行向量的開頭。  這個方法是並行安全的。|  
|[concurrent\_vector::cend 方法](../Topic/concurrent_vector::cend%20Method.md)|將 `const_iterator` 型別的 Iterator 傳回並行向量的結尾。  這個方法是並行安全的。|  
|[concurrent\_vector::clear 方法](../Topic/concurrent_vector::clear%20Method.md)|會清除並行向量中的所有項目。  這個方法不是並行安全的。|  
|[concurrent\_vector::crbegin 方法](../Topic/concurrent_vector::crbegin%20Method.md)|將 `const_reverse_iterator` 型別的 Iterator 傳回並行向量的開頭。  這個方法是並行安全的。|  
|[concurrent\_vector::crend 方法](../Topic/concurrent_vector::crend%20Method.md)|將 `const_reverse_iterator` 型別的 Iterator 傳回並行向量的結尾。  這個方法是並行安全的。|  
|[concurrent\_vector::empty 方法](../Topic/concurrent_vector::empty%20Method.md)|測試呼叫此方法時並行向量是否是空的。  這個方法是並行安全的。|  
|[concurrent\_vector::end 方法](../Topic/concurrent_vector::end%20Method.md)|多載。  將 `iterator` 或 `const_iterator`型別的 Iterator 傳回並行向量的結尾。  這個方法是並行安全的。|  
|[concurrent\_vector::front 方法](../Topic/concurrent_vector::front%20Method.md)|多載。  傳回並行向量中第一個項目的參考或 `const` 參考。  如果並行向量是空的，傳回值會是未定義的。  這個方法是並行安全的。|  
|[concurrent\_vector::get\_allocator 方法](../Topic/concurrent_vector::get_allocator%20Method.md)|傳回用來建構並行向量配置器的複本。  這個方法是並行安全的。|  
|[concurrent\_vector::grow\_by 方法](../Topic/concurrent_vector::grow_by%20Method.md)|多載。  以 `_Delta` 項目成長這個並行向量。  這個方法是並行安全的。|  
|[concurrent\_vector::grow\_to\_at\_least 方法](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|成長這個並行的向量，直到它至少有 `_N` 項目。  這個方法是並行安全的。|  
|[concurrent\_vector::max\_size 方法](../Topic/concurrent_vector::max_size%20Method.md)|傳回並行向量可保存的項目數量上限。  這個方法是並行安全的。|  
|[concurrent\_vector::push\_back 方法](../Topic/concurrent_vector::push_back%20Method.md)|多載。  將指定的項目附加至並行向量的結尾。  這個方法是並行安全的。|  
|[concurrent\_vector::rbegin 方法](../Topic/concurrent_vector::rbegin%20Method.md)|多載。  將 `reverse_iterator` 或 `const_reverse_iterator`型別的 Iterator 傳回並行向量的開頭。  這個方法是並行安全的。|  
|[concurrent\_vector::rend 方法](../Topic/concurrent_vector::rend%20Method.md)|多載。  將 `reverse_iterator` 或 `const_reverse_iterator`型別的 Iterator 傳回並行向量的結尾。  這個方法是並行安全的。|  
|[concurrent\_vector::reserve 方法](../Topic/concurrent_vector::reserve%20Method.md)|配置足夠的空間，讓並行向量的大小可以增長到 `_N`，稍後不需再配置更多的記憶體。  這個方法不是並行安全的。|  
|[concurrent\_vector::resize 方法](../Topic/concurrent_vector::resize%20Method.md)|多載。  視需要刪除或加入項目，將並行向量的大小變更為要求的大小。  這個方法不是並行安全的。|  
|[concurrent\_vector::shrink\_to\_fit 方法](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|壓縮並行向量的內部表示，以減少分散並最佳化記憶體使用量。  這個方法不是並行安全的。|  
|[concurrent\_vector::size 方法](../Topic/concurrent_vector::size%20Method.md)|傳回並行向量中的項目數目。  這個方法是並行安全的。|  
|[concurrent\_vector::swap 方法](../Topic/concurrent_vector::swap%20Method.md)|交換兩個並行向量的內容。  這個方法不是並行安全的。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_vector::operatorOperator](../Topic/concurrent_vector::operatorOperator.md)|多載。  提供存取並行向量中指定索引處的項目。  對讀取作業以及在擴充向量時，這個方法具備並行安全，只要能確保 `_Index` 值小於並行向量的大小。|  
|[concurrent\_vector::operator\= 運算子](../Topic/concurrent_vector::operator=%20Operator.md)|多載。  將另一個 `concurrent_vector` 物件的內容指派給這一個。  這個方法不是並行安全的。|  
  
## 備註  
 如需關於 `concurrent_vector` 類別的詳細資訊，請參閱 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 繼承階層架構  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## 需求  
 **標頭：** concurrent\_vector.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)