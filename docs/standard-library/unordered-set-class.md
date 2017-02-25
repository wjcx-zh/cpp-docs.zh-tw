---
title: "unordered_set 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.unordered_set"
  - "std::tr1::unordered_set"
  - "unordered_set/std::tr1::unordered_set"
  - "tr1::unordered_set"
  - "unordered_set"
  - "tr1.unordered_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_set 類別"
  - "unordered_set 類別 [TR1]"
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# unordered_set 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述控制不同長度的 `const Key` 類型項目序列的物件。  序列由雜湊函式弱式排序，將序列分割為子序列的已排序集合，稱為 Bucket。  在每個 Bucket 中，比較函式判斷是否有任何一對項目具有對等順序。  每個項目同時做為排序鍵和值。  序列表示允許以一些作業查閱、插入和移除任意項目，這些作業可以獨立於序列中的項目數目 \(常數時間\)，至少當所有 Bucket 長度大約相等時。  在最壞的情況下，當所有項目都在一個 Bucket 時，作業數目與序列中的項目數目成正比 \(線性時間\)。  此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
## 語法  
  
```  
template<class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key> >  
    class unordered_set;  
```  
  
#### 參數  
  
|||  
|-|-|  
|參數|描述|  
|`Key`|索引鍵類型。|  
|`Hash`|雜湊函式物件類型。|  
|`Pred`|相等比較函式物件類型。|  
|`Alloc`|配置器類別。|  
  
## 成員  
  
|||  
|-|-|  
|類型定義|描述|  
|[unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md)|管理儲存體的配置器類型。|  
|[unordered\_set::const\_iterator](../Topic/unordered_set::const_iterator.md)|用於受控制序列的常數迭代器類型。|  
|[unordered\_set::const\_local\_iterator](../Topic/unordered_set::const_local_iterator.md)|用於受控制序列的常數 Bucket 迭代器類型。|  
|[unordered\_set::const\_pointer](../Topic/unordered_set::const_pointer.md)|項目的常數指標類型。|  
|[unordered\_set::const\_reference](../Topic/unordered_set::const_reference.md)|項目的常數參考類型。|  
|[unordered\_set::difference\_type](../Topic/unordered_set::difference_type.md)|兩個項目之間的帶正負號距離的類型。|  
|[unordered\_set::hasher](../Topic/unordered_set::hasher.md)|雜湊函式的類型。|  
|[unordered\_set::iterator](../Topic/unordered_set::iterator.md)|受控制序列之迭代器的類型。|  
|[unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md)|比較函式的類型。|  
|[unordered\_set::key\_type](../Topic/unordered_set::key_type.md)|排序索引鍵的類型。|  
|[unordered\_set::local\_iterator](../Topic/unordered_set::local_iterator.md)|用於受控制序列的 Bucket 迭代器類型。|  
|[unordered\_set::pointer](../Topic/unordered_set::pointer.md)|項目的指標類型。|  
|[unordered\_set::reference](../Topic/unordered_set::reference.md)|項目的參考類型。|  
|[unordered\_set::size\_type](../Topic/unordered_set::size_type.md)|兩個項目之間的不帶正負號距離的類型。|  
|[unordered\_set::value\_type](../Topic/unordered_set::value_type.md)|項目的類型。|  
  
|||  
|-|-|  
|成員函式|描述|  
|[unordered\_set::begin](../Topic/unordered_set::begin.md)|指定受控制序列的開頭。|  
|[unordered\_set::bucket](../Topic/unordered_set::bucket.md)|取得索引鍵值的 Bucket 值。|  
|[unordered\_set::bucket\_count](../Topic/unordered_set::bucket_count.md)|取得 Bucket 的數目。|  
|[unordered\_set::bucket\_size](../Topic/unordered_set::bucket_size.md)|取得 Bucket 大小。|  
|[unordered\_set::cbegin](../Topic/unordered_set::cbegin.md)|指定受控制序列的開頭。|  
|[unordered\_set::cend](../Topic/unordered_set::cend.md)|指定受控制序列的結尾。|  
|[unordered\_set::clear](../Topic/unordered_set::clear.md)|移除所有項目。|  
|[unordered\_set::count](../Topic/unordered_set::count.md)|尋找符合指定索引鍵的項目數目。|  
|[unordered\_set::emplace](../Topic/unordered_set::emplace.md)|加入就地建構的項目。|  
|[unordered\_set::emplace\_hint](../Topic/unordered_set::emplace_hint.md)|加入就地建構的項目，含提示。|  
|[unordered\_set::empty](../Topic/unordered_set::empty.md)|測試項目是否不存在。|  
|[unordered\_set::end](../Topic/unordered_set::end.md)|指定受控制序列的結尾。|  
|[unordered\_set::equal\_range](../Topic/unordered_set::equal_range.md)|尋找符合指定之索引鍵的範圍。|  
|[unordered\_set::erase](../Topic/unordered_set::erase.md)|移除位於指定位置的項目。|  
|[unordered\_set::find](../Topic/unordered_set::find.md)|尋找符合指定之索引鍵的項目。|  
|[unordered\_set::get\_allocator](../Topic/unordered_set::get_allocator.md)|取得已儲存的配置器物件。|  
|[unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)|取得儲存的雜湊函式物件。|  
|[unordered\_set::insert](../Topic/unordered_set::insert.md)|加入項目。|  
|[unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)|取得儲存的比較函式物件。|  
|[unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)|計算每個 Bucket 平均項目。|  
|[unordered\_set::max\_bucket\_count](../Topic/unordered_set::max_bucket_count.md)|取得 Bucket 最大數目。|  
|[unordered\_set::max\_load\_factor](../Topic/unordered_set::max_load_factor.md)|取得或設定每個 Bucket 最大項目數。|  
|[unordered\_set::max\_size](../Topic/unordered_set::max_size.md)|取得受控制序列的大小上限。|  
|[unordered\_set::rehash](../Topic/unordered_set::rehash.md)|重建雜湊資料表。|  
|[unordered\_set::size](../Topic/unordered_set::size.md)|計算項目的數目。|  
|[unordered\_set::swap](../Topic/unordered_set::swap.md)|交換兩個容器的內容。|  
|[unordered\_set::unordered\_set](../Topic/unordered_set::unordered_set.md)|建構容器物件。|  
  
|||  
|-|-|  
|運算子|描述|  
|[unordered\_set::operator\=](../Topic/unordered_set::operator=.md)|複製雜湊資料表。|  
  
## 備註  
 物件是藉由呼叫下列兩個預存物件，排序它所控制的序列：[unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md) 類型的比較函式物件和 [unordered\_set::hasher](../Topic/unordered_set::hasher.md) 類型的雜湊函式物件。  您可以呼叫成員函式 [unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)`()` 存取第一個儲存的物件，以及呼叫成員函式 [unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)`()` 存取第二個儲存的物件。  具體來說，只有在兩個引數值具有對等順序，對於 `Key` 類型的所有值 `X` 和 `Y`，呼叫 `key_eq()(X, Y)` 才會傳回 true，呼叫 `hash_function()(keyval)` 會產生 `size_t` 類型值的分佈。  不同於樣板類別 [unordered\_multiset 類別](../standard-library/unordered-multiset-class.md)，樣板類別 `unordered_set` 的物件可保證 `key_eq()(X, Y)` 針對受控制序列的任何兩個項目永遠是 false \(索引鍵是唯一的\)。  
  
 物件也會儲存最大載入因數，指定每個 Bucket 所需的項目平均數目上限。  如果插入項目會使 [unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)`()` 超出最大的載入因數，容器會增加 Bucket 的數目並視需要重建雜湊資料表。  
  
 受控制序列中實際的項目順序取決於雜湊函式、比較函式、插入順序、最大載入因數和 Bucket 目前數目。  一般來說，您無法預測受控制序列中的項目順序。  不過，您永遠可以確保，有對等順序的任何項目子集在受控制序列中為相鄰。  
  
 物件透過 [unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md) 類型的預存配置器物件，為它所控制的序列配置和釋放儲存體。  這種配置器物件必須具有和 `allocator` 樣板類別物件相同的外部介面。  請注意，如果已指定容器物件，儲存的配置器物件不會複製。  
  
## 需求  
 **標頭：**\<unordered\_set\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<unordered\_set\>](../standard-library/unordered-set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)