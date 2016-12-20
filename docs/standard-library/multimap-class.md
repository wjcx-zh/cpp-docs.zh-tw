---
title: "multimap 類別 | Microsoft Docs"
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
  - "multimap"
  - "std.multimap"
  - "map/std::multimap"
  - "std::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap 類別"
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# multimap 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標準範本庫 multimap 類別是用來從每個項目都是資料值與排序鍵組的集合中儲存和擷取資料。  索引鍵的值不需要是唯一的，用於自動排序資料。  多重對應中項目的值可以直接變更，但其關聯的索引鍵值不可以直接變更。  相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。  
  
## 語法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class multimap;  
```  
  
#### 參數  
 `Key`  
 要存放在多重對應中的索引鍵資料類型。  
  
 `Type`  
 要存放在多重對應中的項目資料類型。  
  
 `Traits`  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在多重對應中的相對順序。  二元述詞 `less<Key>` 是預設值。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關對應之記憶體配置和解除配置的詳細資訊。  這個引數是選擇性的，而且預設值是 `allocator<pair <const Key, Type> >`。  
  
## 備註  
 STL multimap 類別為  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。  
  
-   多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目資料值。  
  
-   一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。  
  
-   樣板類別，因為它提供的功能是泛型，因此與做為項目或索引鍵包含的特定資料類型是獨立的。  用於項目或索引鍵的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 map 類別提供的迭代器是雙向的迭代器，不過類別成員函式 [insert](../Topic/multimap::insert.md) 和 [multimap](../Topic/multimap::multimap.md) 擁有以較弱的輸入迭代器做為樣板參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而形成關聯的系列。  每個迭代器概念有自己的一組需求，因此，使用它們的演算法必須將其假設限制為該迭代器類型的需求。  可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通有關迭代器範圍 `[First, Last)`。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  關聯的容器已針對查閱、插入和移除作業最佳化。  明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，多重對應應該是首選的關聯容器。  這種結構的模型是已排序的關鍵字清單，其關聯的字串値 \(例如\) 提供定義，但不一定唯一定義文字。  如果關鍵字是唯一定義，因此索引鍵是唯一的，則對應是首選容器。  另一方面，如果只儲存文字清單，則集合是正確的容器。  如果允許文字的多個項目，則集合是適當的容器結構。  
  
 多重對應會藉由呼叫 [key\_compare](../Topic/multimap::key_compare.md) 類型的預存函式物件，排序它所控制的序列。  這個預存物件是可藉由呼叫成員函式 [key\_comp](../Topic/multimap::key_comp.md) 存取的比較函式。  通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致非對等元件之間的排序。  一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 `f(x,y)` 是有兩個引數物件 `x` 和 `y` 以及傳回值 true 或 false 的函式物件。  如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 `x` 和 `y` 在 `f(x,y)` 和 `f(y,x)` 為 false 時定義為相等，則施加於集合的順序是嚴格弱式順序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[multimap](../Topic/multimap::multimap.md)|建構一個空的 `multimap`，或是其他 `multimap` 的全部或部分複本。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multimap::allocator_type.md)|類型，表示 `allocator` 物件的 `multimap` 類別。|  
|[const\_iterator](../Topic/multimap::const_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的 `multimap` 項目。|  
|[const\_pointer](../Topic/multimap::const_pointer.md)|類型，提供 `const` 中 `multimap` 項目之指標。|  
|[const\_reference](../Topic/multimap::const_reference.md)|類型，提供儲存在 `const` 中供讀取和執行 `multimap` 作業之 `const` 項目的參考。|  
|[const\_reverse\_iterator](../Topic/multimap::const_reverse_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的任何 `multimap` 項目。|  
|[difference\_type](../Topic/multimap::difference_type.md)|帶正負號的整數類型，可以用來表示範圍 \(介於迭代器所指的項目\) 中 `multimap` 的項目數。|  
|[迭代器](../Topic/multimap::iterator.md)|類型，提供兩個參考相同 `multimap` 內項目的迭代器之間的差異。|  
|[key\_compare](../Topic/multimap::key_compare.md)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `multimap` 中的相對順序。|  
|[key\_type](../Topic/multimap::key_type.md)|類型，描述構成 `multimap` 每個元素的排序鍵物件。|  
|[mapped\_type](../Topic/multimap::mapped_type.md)|類型，表示儲存在 `multimap` 中的資料類型。|  
|[指標](../Topic/multimap::pointer.md)|類型，提供 `const` 中 `multimap` 項目之指標。|  
|[參考](../Topic/multimap::reference.md)|類型，提供儲存在 `multimap` 中之項目的參考。|  
|[reverse\_iterator](../Topic/multimap::reverse_iterator.md)|類型，提供可以讀取或修改反轉 `multimap` 中之項目的雙向迭代器。|  
|[size\_type](../Topic/multimap::size_type.md)|不帶正負號的整數類型，提供 `const` 中 `multimap` 項目之指標。|  
|[value\_type](../Topic/multimap::value_type.md)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `multimap` 中的相對順序。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/multimap::begin.md)|傳回迭代器，為 `multimap` 中的第一個項目定址。|  
|[cbegin](../Topic/multimap::cbegin.md)|傳回常數迭代器，為 `multimap` 中的第一個項目定址。|  
|[cend](../Topic/multimap::cend.md)|傳回常數迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|  
|[清除](../Topic/multimap::clear.md)|清除 `multimap` 的所有項目。|  
|[count](../Topic/multimap::count.md)|傳回 `multimap` 中索引鍵符合參數指定之索引鍵的項目數目。|  
|[crbegin](../Topic/multimap::crbegin.md)|傳回常數迭代器，為反轉 `multimap` 中的第一個項目定址。|  
|[crend](../Topic/multimap::crend.md)|傳回常數迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|  
|[emplace](../Topic/multimap::emplace.md)|將就地建構的項目插入 `multimap` 中。|  
|[emplace\_hint](../Topic/multimap::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入 `multimap` 中。|  
|[空白](../Topic/multimap::empty.md)|測試 `multimap` 是否為空白。|  
|[end](../Topic/multimap::end.md)|傳回迭代器，為 `multimap` 中最後一個項目的下一個位置定址。|  
|[equal\_range](../Topic/multimap::equal_range.md)|尋找項目索引鍵符合指定值的項目範圍。|  
|[erase](../Topic/multimap::erase.md)|從指定的位置移除 `multimap` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](../Topic/multimap::find.md)|傳回迭代器，定址 `multimap` 中索引鍵等於指定索引鍵之項目的第一個位置。|  
|[get\_allocator](../Topic/multimap::get_allocator.md)|傳回用來建構 `allocator` 的 `multimap` 物件複本。|  
|[插入](../Topic/multimap::insert.md)|將項目或項目範圍插入至 `multimap`。|  
|[key\_comp](../Topic/multimap::key_comp.md)|擷取 `multimap` 中用來排序索引鍵的比較物件之複本。|  
|[lower\_bound](../Topic/multimap::lower_bound.md)|傳回迭代器，指向 `multimap` 中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max\_size](../Topic/multimap::max_size.md)|傳回 `multimap` 的最大長度。|  
|[rbegin](../Topic/multimap::rbegin.md)|傳回迭代器，為反轉 `multimap` 中的第一個項目定址。|  
|[rend](../Topic/multimap::rend.md)|傳回迭代器，為反轉 `multimap` 中最後一個項目的下一個位置定址。|  
|[大小](../Topic/multimap::size.md)|傳回 `multimap` 中項目的數目。|  
|[交換](../Topic/multimap::swap.md)|交換兩個 `multimap` 的項目。|  
|[upper\_bound](../Topic/multimap::upper_bound.md)|傳回迭代器，指向 `multimap` 中索引鍵大於特定索引鍵的第一個項目。|  
|[value\_comp](../Topic/multimap::value_comp.md)|成員函式傳回函式物件，可藉由比較其索引鍵值判斷 `multimap` 中項目的順序。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/multimap::operator=.md)|用另一個 `multimap` 的複本取代 `multimap` 的項目。|  
  
## 需求  
 **標頭：**\<map\>  
  
 **命名空間:** std  
  
 \(**key**, **value**\) 配對組儲存在多重對應中做為 `pair` 類型的物件。  pair 類別需要標頭 \<utility\>，而這個標頭由 \<map\> 自動包含。  
  
## 請參閱  
 [\<map\> Members](http://msdn.microsoft.com/zh-tw/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)