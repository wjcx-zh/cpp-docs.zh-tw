---
title: "set 類別 | Microsoft Docs"
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
  - "std::set"
  - "set"
  - "set/std::set"
  - "std.set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set 類別"
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL 容器類別 set 用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。  集合中項目的索引鍵值不能直接變更。  相反地，必須刪除舊值，並插入具有新值的項目。  
  
## 語法  
  
```  
template <  
    class Key,   
    class Traits=less<Key>,   
    class Allocator=allocator<Key>   
>  
class set  
```  
  
#### 參數  
 `Key`  
 要存放在集合中的項目資料類型。  
  
 `Traits`  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在集合中的相對順序。  這是選擇性引數，而且二元述詞 **less***\<Key\>* 是預設值。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關集合之記憶體配置和解除配置的詳細資訊。  這個引數是選擇性的，而且預設值是 **allocator***\<Key\>。*  
  
## 備註  
 STL 集合是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  此外，它是簡單關聯的容器，因為其項目值是其索引鍵值的。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由容器內的索引鍵值排序。  
  
-   唯一，因為它的每個項目都必須具有唯一索引鍵。  因為集合也是簡單的關聯容器，所以其元素也是唯一的。  
  
 集合也描述成樣板類別，因為它提供的功能是泛型，因此與做為項目包含的特定資料類型是獨立的。  使用的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  關聯的容器已針對查閱、插入和移除作業最佳化。  明確支援這些作業的成員函式很有效率，以與容器中的項目數目之對數成正比的平均時間執行它們。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，集合應該是首選的關聯容器。  集合的項目是唯一的，並當做自己的排序鍵。  例如，這種結構的模型是文字的已排序清單，其中文字只可以出現一次。  如果允許文字的多個項目，則集合是適當的容器結構。  如果值必須附加至唯一關鍵字清單，則對應是包含這個資料的適當結構。  如果索引鍵不是唯一的，則多重對應是首選容器。  
  
 集合會藉由呼叫 [key\_compare](../Topic/set::key_compare.md) 類型的預存函式物件，排序它所控制的序列。  這個預存物件是可藉由呼叫成員函式 [key\_comp](../Topic/set::key_comp.md) 存取的比較函式。  通常，項目必須是小於比較才能建立此順序，因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致非對等元件之間的排序。  一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 *f*\(*x,y*\) 是有兩個引數物件 *x* 和 *y* 以及傳回值 **true** 或 **false** 的函式物件。  如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 *x* 和 *y* 在 *f*\(*x,y*\) 和 *f*\(*y,x*\) 為 false 時定義為相等，則施加於集合的順序是嚴格弱式順序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
  
 在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 set 類別提供的迭代器是雙向的迭代器，不過類別成員函式 [insert](../Topic/set::insert.md) 和 [set](../Topic/set::set.md) 擁有以較弱的輸入迭代器做為樣板參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而形成關聯的系列。  每個迭代器概念有自己的一組需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。  可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  這是最小的一組功能，不過，已足以在類別成員函式的內容中有意義地溝通有關迭代器範圍 \[`First`, `Last`\)。  
  
### 建構函式  
  
|||  
|-|-|  
|[設定](../Topic/set::set.md)|建構一個空的集合，或者建構其他集合的全部或部分複本。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/set::allocator_type.md)|類型，表示 set 物件的 `allocator` 類別。|  
|[const\_iterator](../Topic/set::const_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取集合中的 `const` 項目。|  
|[const\_pointer](../Topic/set::const_pointer.md)|類型，提供集合中 `const` 項目之指標。|  
|[const\_reference](../Topic/set::const_reference.md)|類型，提供儲存在集合中供讀取和執行 `const` 作業之 `const` 項目的參考。|  
|[const\_reverse\_iterator](../Topic/set::const_reverse_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取集合中的任何 `const` 項目。|  
|[difference\_type](../Topic/set::difference_type.md)|帶正負號的整數類型，可以用來表示範圍 \(介於迭代器所指的項目\) 中集合的項目數。|  
|[迭代器](../Topic/set::iterator.md)|類型，提供可以讀取或修改集合中之任何項目的雙向迭代器。|  
|[key\_compare](../Topic/set::key_compare.md)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在集合中的相對順序。|  
|[key\_type](../Topic/set::key_type.md)|此類型描述在做為排序鍵的產能上，做為集合的項目儲存的物件。|  
|[指標](../Topic/set::pointer.md)|類型，提供集合中的項目之指標。|  
|[參考](../Topic/set::reference.md)|類型，提供儲存在集合中之項目的參考。|  
|[reverse\_iterator](../Topic/set::reverse_iterator.md)|類型，提供可以讀取或修改反轉集合中之項目的雙向迭代器。|  
|[size\_type](../Topic/set::size_type.md)|不帶正負號的整數類型，可以表示集合中的項目數。|  
|[value\_compare](../Topic/set::value_compare.md)|類型，提供可比較兩個項目之函式物件，以判斷項目在集合中的相對順序。|  
|[value\_type](../Topic/set::value_type.md)|此類型描述在做為值的產能上，做為集合的項目儲存的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/set::begin.md)|傳回迭代器，為集合中的第一個項目定址。|  
|[cbegin](../Topic/set::cbegin.md)|傳回常數迭代器，為集合中的第一個項目定址。|  
|[cend](../Topic/set::cend.md)|傳回常數迭代器，為集合中最後一個項目的下一個位置定址。|  
|[清除](../Topic/set::clear.md)|清除集合的所有項目。|  
|[count](../Topic/set::count.md)|傳回集合中索引鍵符合參數指定之索引鍵的項目數目。|  
|[crbegin](../Topic/set::rbegin.md)|傳回常數迭代器，為反轉集合中的第一個項目定址。|  
|[crend](../Topic/set::rend.md)|傳回常數迭代器，為反轉集合中最後一個項目的下一個位置定址。|  
|[emplace](../Topic/set::emplace.md)|將就地建構的項目插入集合中。|  
|[emplace\_hint](../Topic/set::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入集合中。|  
|[空白](../Topic/set::empty.md)|測試集合是否為空白。|  
|[end](../Topic/set::end.md)|傳回迭代器，為集合中最後一個項目的下一個位置定址。|  
|[equal\_range](../Topic/set::equal_range.md)|傳回一組迭代器，分別指向集合中索引鍵大於特定索引鍵的第一個項目，以及指向集合中索引鍵等於或大於該索引鍵的第一個項目。|  
|[erase](../Topic/set::erase.md)|從指定的位置移除集合中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](../Topic/set::find.md)|傳回迭代器，定址集合中索引鍵等於指定索引鍵之項目的位置。|  
|[get\_allocator](../Topic/set::get_allocator.md)|傳回用來建構集合的 `allocator` 物件複本。|  
|[插入](../Topic/set::insert.md)|將項目或某個項目範圍插入集合中。|  
|[key\_comp](../Topic/set::key_comp.md)|擷取集合中用來排序索引鍵的比較物件之複本。|  
|[lower\_bound](../Topic/set::lower_bound.md)|傳回迭代器，指向集合中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max\_size](../Topic/set::max_size.md)|傳回集合的最大長度。|  
|[rbegin](../Topic/set::rbegin.md)|傳回迭代器，為反轉集合中的第一個項目定址。|  
|[rend](../Topic/set::rend.md)|傳回迭代器，為反轉集合中最後一個項目的下一個位置定址。|  
|[大小](../Topic/set::size.md)|傳回集合中項目的數目。|  
|[交換](../Topic/set::swap.md)|交換兩個集合的項目。|  
|[upper\_bound](../Topic/set::upper_bound.md)|傳回迭代器，指向集合中索引鍵大於特定索引鍵的第一個項目。|  
|[value\_comp](../Topic/set::value_comp.md)|擷取集合中用於排序項目值的比較物件之複本。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/set::operator=.md)|用另一個集合複本取代集合的項目。|  
  
## 需求  
 **標頭：**\<set\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<set\>](../standard-library/set.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)