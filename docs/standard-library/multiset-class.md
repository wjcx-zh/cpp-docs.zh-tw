---
title: "multiset 類別 | Microsoft Docs"
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
  - "std::multiset"
  - "set/std::multiset"
  - "std.multiset"
  - "multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiset 類別"
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 21
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# multiset 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標準範本庫 multiset 類別用於在集合中儲存和擷取資料，集合中包含的項目值不需要是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。  多重集中項目的索引鍵值不能直接變更。  相反地，必須刪除舊值，並插入具有新值的項目。  
  
## 語法  
  
```  
  
        template <  
   class Key,   
   class Compare=less<Key>,   
   class Allocator=allocator<Key>   
>  
class multiset  
```  
  
#### 參數  
 *Key*  
 要存放在多重集中的項目資料類型。  
  
 *Compare*  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在多重集中的相對順序。  二元述詞 **less**\<Key\> 是預設值。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關多重集之記憶體配置和解除配置的詳細資訊。  預設值為 **allocator***\<Key\>。*  
  
## 備註  
 STL multiset 類別為：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。  
  
-   多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目值。  
  
-   簡單關聯的容器，因為其項目值是其索引鍵值的。  
  
-   樣板類別，因為它提供的功能是泛型，因此與做為項目包含的特定資料類型是獨立的。  使用的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 multiset 類別提供的迭代器是雙向的迭代器，不過類別成員函式 [insert](../Topic/multiset::insert.md) 和 [multiset](../Topic/multiset::multiset.md) 擁有以較弱的輸入迭代器做為樣板參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而形成關聯的系列。  每個迭代器概念有自己的一組需求，因此，使用它們的演算法必須將其假設限制為該迭代器類型的需求。  可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通有關迭代器範圍 \[`First`, `Last`\)。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  關聯的容器已針對查閱、插入和移除作業最佳化。  明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，多重集應該是首選的關聯容器。  多重集的項目可以是多重，並當做自己的排序鍵，因此索引鍵不是唯一的。  例如，這種結構的模型是文字的已排序清單，其中文字可以出現多次。  如果不允許文字的多個項目，則集合是適當的容器結構。  如果唯一定義做為值附加至唯一關鍵字清單，則對應是包含這個資料的適當結構。  如果定義不是唯一的，則多重對應是首選容器。  
  
 多重集是藉由呼叫 `Compare` 類型的預存函式物件，排序它所控制的序列。  這個預存物件是可藉由呼叫成員函式 [key\_comp](../Topic/multiset::key_comp.md) 存取的比較函式。  通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致非對等元件之間的排序。  一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 *f*\(*x*,*y*\) 是有兩個引數物件 *x* 和 *y* 以及傳回值 **true** 或 **false** 的函式物件。  如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 x 和 y 在 *f*\(*x,y*\) 和 *f*\(*y,x*\) 為 false 時定義為相等，則施加於集合的順序是嚴格弱式順序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
### 建構函式  
  
|||  
|-|-|  
|[multiset](../Topic/multiset::multiset.md)|建構一個空的 `multiset`，或是指定之 `multiset` 的全部或部分複本。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multiset::allocator_type.md)|`allocator` 物件之 `multiset` 類別的 typedef。|  
|[const\_iterator](../Topic/multiset::const_iterator.md)|可以在 `const` 中讀取 `multiset` 項目的雙向迭代器的 typedef。|  
|[const\_pointer](../Topic/multiset::const_pointer.md)|在 `const` 中指向 `multiset` 項目的指標之 typedef。|  
|[const\_reference](../Topic/multiset::const_reference.md)|指向儲存在 `const` 中的 `multiset` 項目的參考之 typedef，用以讀取和執行 `const` 作業。|  
|[const\_reverse\_iterator](../Topic/multiset::const_reverse_iterator.md)|可以在 `const` 中讀取任何 `multiset` 項目的雙向迭代器的 typedef。|  
|[difference\_type](../Topic/multiset::difference_type.md)|範圍 \(介於迭代器所指的項目\) 中 `multiset` 的項目數量的帶正負號整數 typedef。|  
|[迭代器](../Topic/multiset::iterator.md)|雙向迭代器的 typedef，可以讀取或修改 `multiset` 中的任何項目。|  
|[key\_compare](../Topic/multiset::key_compare.md)|函式物件之 typedef，可比較兩個索引鍵以判斷兩個項目在 `multiset` 中的相對順序。|  
|[key\_type](../Topic/multiset::key_type.md)|函式物件之 typedef，可比較兩個排序鍵以判斷兩個項目在 `multiset` 中的相對順序。|  
|[指標](../Topic/multiset::pointer.md)|在 `multiset` 中指向項目的指標之 typedef。|  
|[參考](../Topic/multiset::reference.md)|`multiset` 中預存項目的參考之 typedef。|  
|[reverse\_iterator](../Topic/multiset::reverse_iterator.md)|雙向迭代器的 typedef，可以讀取或修改反轉 `multiset` 中的項目。|  
|[size\_type](../Topic/multiset::size_type.md)|不帶正負號的整數類型，可以表示 `multiset` 中的項目數。|  
|[value\_compare](../Topic/multiset::value_compare.md)|可將兩個項目做為排序鍵進行比較之函式物件的 typedef，以判斷項目在 `multiset` 中的相對順序。|  
|[value\_type](../Topic/multiset::value_type.md)|typedef，在做為值的產能上，描述做為 `multiset` 的項目儲存的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/multiset::begin.md)|傳回指向 `multiset` 中的第一個項目的迭代器。|  
|[cbegin](../Topic/multiset::cbegin.md)|傳回常數迭代器，為 `multiset` 中的第一個項目定址。|  
|[cend](../Topic/multiset::cend.md)|傳回常數迭代器，為 `multiset` 中最後一個項目的下一個位置定址。|  
|[清除](../Topic/multiset::clear.md)|清除 `multiset` 的所有項目。|  
|[count](../Topic/multiset::count.md)|傳回 `multiset` 中索引鍵符合指定為參數之索引鍵的項目數目。|  
|[crbegin](../Topic/multiset::crbegin.md)|傳回常數迭代器，為反轉集合中的第一個項目定址。|  
|[crend](../Topic/multiset::crend.md)|傳回常數迭代器，為反轉集合中最後一個項目的下一個位置定址。|  
|[emplace](../Topic/multiset::emplace.md)|將就地建構的項目插入 `multiset` 中。|  
|[emplace\_hint](../Topic/multiset::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入 `multiset` 中。|  
|[空白](../Topic/multiset::empty.md)|測試 `multiset` 是否為空白。|  
|[end](../Topic/multiset::end.md)|傳回 `multiset` 中，指向最後一個項目後面的位置之迭代器。|  
|[equal\_range](../Topic/multiset::equal_range.md)|傳回一對迭代器。  配對中第一個迭代器指向 `multiset` 中索引鍵大於指定索引鍵的第一個項目。  配對中第二個迭代器指向 `multiset` 中索引鍵等於或大於指定索引鍵的第一個項目。|  
|[erase](../Topic/multiset::erase.md)|從指定的位置移除 `multiset` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](../Topic/multiset::find.md)|傳回迭代器，指向 `multiset` 中索引鍵等於指定索引鍵的第一個項目的位置。|  
|[get\_allocator](../Topic/multiset::get_allocator.md)|傳回用來建構 `allocator` 的 `multiset` 物件複本。|  
|[插入](../Topic/multiset::insert.md)|將項目或項目範圍插入至 `multiset`。|  
|[key\_comp](../Topic/multiset::key_comp.md)|提供可比較兩個排序鍵的函式物件，以判斷兩個項目在 `multiset` 中的相對順序。|  
|[lower\_bound](../Topic/multiset::lower_bound.md)|傳回迭代器，指向 `multiset` 中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max\_size](../Topic/multiset::max_size.md)|傳回 `multiset` 的最大長度。|  
|[rbegin](../Topic/multiset::rbegin.md)|傳回指向反轉 `multiset` 中的第一個項目的迭代器。|  
|[rend](../Topic/multiset::rend.md)|傳回反轉 `multiset` 中，指向最後一個項目的下一個位置之迭代器。|  
|[大小](../Topic/multiset::size.md)|傳回 `multiset` 中的項目數目。|  
|[交換](../Topic/multiset::swap.md)|交換兩個 `multiset` 的項目。|  
|[upper\_bound](../Topic/multiset::upper_bound.md)|傳回迭代器，指向 `multiset` 中索引鍵大於特定索引鍵的第一個項目。|  
|[value\_comp](../Topic/multiset::value_comp.md)|擷取 `multiset` 中用於排序項目值的比較物件之複本。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/multiset::operator=.md)|用另一個 `multiset` 的複本取代 `multiset` 的項目。|  
  
## 需求  
 **標頭：**\<set\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<set\> Members](http://msdn.microsoft.com/zh-tw/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)