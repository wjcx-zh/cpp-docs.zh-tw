---
title: "hash_set 類別 | Microsoft Docs"
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
  - "hash_set/stdext::hash_set"
  - "std::hash_set"
  - "std.hash_set"
  - "stdext::hash_set"
  - "hash_set"
  - "stdext.hash_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set 類別"
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_set 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  這個 API 已過時。  替代方案是 [unordered\_set 類別](../standard-library/unordered-set-class.md)。  
  
 容器類別 hash\_set 是標準範本程式庫 \(STL\) 的擴充功能，可用以在集合中儲存及快速擷取資料，而該集合中包含的項目值不能重複且會用做為索引鍵值。  
  
## 語法  
  
```  
template <  
   class Key,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<Key>   
>  
class hash_set  
```  
  
#### 參數  
 `Key`  
 要存放在 hash\_set 中的項目資料類型。  
  
 `Traits`  
 包含兩個函式物件的類型：一個是 compare 類別 \(此為二元述詞，可將兩個項目值以排序索引鍵加以比較，以決定其相對順序\)；一個是雜湊函式 \(此為一元述詞，可將項目的索引鍵值對應到 **size\_t** 類型且不帶正負號的整數。  這個引數是選用引數，且預設值為 `hash_compare`*\<Key,* **less***\<Key\> \>* 。  
  
 `Allocator`  
 代表預存配置器物件的類型，其會封裝有關 hash\_set 之記憶體配置與解除配置的詳細資訊。  這個引數是選擇性的，而且預設值是 **allocator***\<Key\>。*  
  
## 備註  
 hash\_set 是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  此外，它是簡單關聯的容器，因為其項目值是其索引鍵值的。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已經過雜湊處理，因為其項目會依據套用至該項目索引鍵值之雜湊函式的值，分組到不同值區。  
  
-   唯一，因為它的每個項目都必須具有唯一索引鍵。  因為 hash\_set 也是簡式的相關聯容器，所以其項目也不會重複。  
  
-   範本類別，因為它提供的功能是泛型，因此與作為項目或索引鍵包含的特定資料類型是獨立的。  用於項目或索引鍵的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 透過排序進行雜湊的主要優點是效率更佳；成功的雜湊能執行插入、刪除，相較於和排序技術容器中項目數目對數值成比例的時間，它會以常數平均時間進行搜尋。  集合中項目的索引鍵值不能直接變更。  相反地，必須刪除舊值，並插入具有新值的項目。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  經過雜湊處理的相關聯容器，已針對查閱、插入及移除作業進行過最佳化。  搭配設計良好的雜湊函式使用時，明確支援這些作業的成員函式，效率相當良好，其會以平均而言為常數的時間執行作業，而與此容器中的項目數目無關。  設計良好的雜湊函式會產生雜湊值的均勻分佈，並盡可能減少衝突發生，當相異索引鍵值對應到相同的雜湊值時，就會發生所謂的衝突。  使用最糟的雜湊函式的最壞情況下，作業數目與序列中的項目數目成正比 \(線性時間\)。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，hash\_set 應該要當成首選的相關聯容器。  hash\_set 的項目不會重複，且會做為本身的排序鍵。  例如，這種結構的模型是文字的已排序清單，其中文字只可以出現一次。  如果允許出現多次文字，則 hash\_multiset 即是適當的容器結構。  如果值必須附加至不重複的關鍵字清單，則 hash\_map 會是包含此資料的適當結構。  如果索引鍵重複，則 hash\_multimap 是首選容器。  
  
 hash\_set 會藉由呼叫 [value\_compare](../Topic/hash_set::value_compare.md) 類型的預存雜湊 **Traits** 物件，排序它所控制的序列。  這個預存物件可藉由呼叫成員函式 [key\_comp](../Topic/hash_set::key_comp.md) 加以存取。  這類函式物件的行為必須要與 *hash\_compare\<Key, less\<Key\> \> 類別物件相同。尤其是針對 Key 類型的所有*  `_Key` 值，呼叫 Trait\(`_Key` \) 會產生 size\_t 類型值的分佈。  
  
 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致非對等項目之間的排序。  一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 *f*\(*x*,*y*\) 是有兩個引數物件 x 和 y 以及傳回 true 或 false 的函式物件。  如果二元述詞並非其反身、非對稱且可轉移，而且如果同等項目可以轉移，其中兩個物件 *x* 和 *y* 在 *f*\(*x*,*y*\) 和 *f*\(*y*,*x*\) 為 false 時定義為同等項目，則施加於 hash\_set 的順序是嚴格弱式排序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
  
 受控制序列中實際的項目順序取決於雜湊函式、排序函式以及儲存於此容器物件中雜湊資料表目前的大小。  您無法判斷目前雜湊資料表的大小，因此一般而言，無法預測受控制序列中項目的順序。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 hash\_set 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](../Topic/hash_set::insert.md) 和 [hash\_set](../Topic/hash_set::hash_set.md) 擁有以較弱的輸入迭代器做為範本參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而形成關聯的系列。  每個迭代器概念有自己的一組需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。  可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  這是最基本的一組功能，但足以在類別成員函式的內容中，有意義地溝通迭代器 \[`_First`, `_Last`\) 的範圍。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間。  如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### 建構函式  
  
|||  
|-|-|  
|[hash\_set](../Topic/hash_set::hash_set.md)|建構一個空的 `hash_set`，或是其他 `hash_set` 的全部或部分複本。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_set::allocator_type.md)|類型，表示 `allocator` 物件的 `hash_set` 類別。|  
|[const\_iterator](../Topic/hash_set::const_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的 `hash_set` 項目。|  
|[const\_pointer](../Topic/hash_set::const_pointer.md)|類型，提供 `const` 中 `hash_set` 項目之指標。|  
|[const\_reference](../Topic/hash_set::const_reference.md)|類型，提供儲存在 `const` 中供讀取和執行 `hash_set` 作業之 `const` 項目的參考。|  
|[const\_reverse\_iterator](../Topic/hash_set::const_reverse_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的任何 `hash_set` 項目。|  
|[difference\_type](../Topic/hash_set::difference_type.md)|帶正負號的整數類型，可以用來表示範圍 \(介於迭代器所指的項目\) 中 `hash_set` 的項目數。|  
|[迭代器](../Topic/hash_set::iterator.md)|類型，其提供可讀取或修改 `hash_set` 中任何項目的雙向迭代器。|  
|[key\_compare](../Topic/hash_set::key_compare.md)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `hash_set` 中的相對順序。|  
|[key\_type](../Topic/hash_set::key_type.md)|類型，其描述在做為排序鍵的功能上，儲存為 `hash_set` 項目的物件。|  
|[指標](../Topic/hash_set::pointer.md)|類型，其提供 `hash_set` 中項目的指標。|  
|[參考](../Topic/hash_set::reference.md)|類型，提供儲存在 `hash_set` 中之項目的參考。|  
|[reverse\_iterator](../Topic/hash_set::reverse_iterator.md)|類型，提供可以讀取或修改反轉 `hash_set` 中之項目的雙向迭代器。|  
|[size\_type](../Topic/hash_set::size_type.md)|不帶正負號的整數類型，可以表示 `hash_set` 中的項目數。|  
|[value\_compare](../Topic/hash_set::value_compare.md)|類型，其提供兩個函式物件，一個是可以比較 `hash_set` 兩個項目值的 compare 類別以決定其相對順序的二元述詞，以及會將項目進行雜湊處理的一元述詞。|  
|[value\_type](../Topic/hash_set::value_type.md)|類型，其描述在做為值的功能上，儲存為 `hash_set` 項目的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/hash_set::begin.md)|傳回迭代器，會定址到`hash_set` 中的第一個項目。|  
|[hash\_set::cbegin](../Topic/hash_set::cbegin.md)|傳回常數迭代器，為 `hash_set` 中的第一個項目定址。|  
|[hash\_set::cend](../Topic/hash_set::cend.md)|傳回常數迭代器，為 `hash_set` 中最後一個項目的下一個位置定址。|  
|[清除](../Topic/hash_set::clear.md)|清除 `hash_set` 的所有項目。|  
|[count](../Topic/hash_set::count.md)|傳回 `hash_set` 中索引鍵符合參數指定之索引鍵的項目數目。|  
|[hash\_set::crbegin](../Topic/hash_set::crbegin.md)|傳回常數迭代器，為反轉 `hash_set` 中的第一個項目定址。|  
|[hash\_set::crend](../Topic/hash_set::crend.md)|傳回常數迭代器，為反轉 `hash_set` 中最後一個項目的下一個位置定址。|  
|[hash\_set::emplace](../Topic/hash_set::emplace.md)|將就地建構的項目插入 `hash_set` 中。|  
|[hash\_set::emplace\_hint](../Topic/hash_set::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入 `hash_set` 中。|  
|[空白](../Topic/hash_set::empty.md)|測試 `hash_set` 是否為空白。|  
|[end](../Topic/hash_set::end.md)|傳回迭代器，為 `hash_set` 中最後一個項目的下一個位置定址。|  
|[equal\_range](../Topic/hash_set::equal_range.md)|傳回成對的迭代器，分別指向 `hash_set` 中索引鍵大於特定索引鍵的第一個項目，以及指向 `hash_set` 中索引鍵等於或大於該索引鍵的第一個項目。|  
|[erase](../Topic/hash_set::erase.md)|從指定的位置移除 `hash_set` 中的項目或項目範圍，或移除符合指定之索引鍵的項目。|  
|[find](../Topic/hash_set::find.md)|傳回迭代器，為 `hash_set` 中索引鍵等於指定索引鍵之項目位置定址。|  
|[get\_allocator](../Topic/hash_set::get_allocator.md)|傳回用來建構 `allocator` 的 `hash_set` 物件複本。|  
|[插入](../Topic/hash_set::insert.md)|將項目或項目範圍插入至 `hash_set`。|  
|[key\_comp](../Topic/hash_set::key_comp.md)|擷取 `hash_set` 中用來排序索引鍵的比較物件之複本。|  
|[lower\_bound](../Topic/hash_set::lower_bound.md)|傳回迭代器，指向 `hash_set` 中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[max\_size](../Topic/hash_set::max_size.md)|傳回 `hash_set` 的最大長度。|  
|[rbegin](../Topic/hash_set::rbegin.md)|傳回迭代器，為反轉 `hash_set` 中的第一個項目定址。|  
|[rend](../Topic/hash_set::rend.md)|傳回迭代器，為反轉 `hash_set` 中最後一個項目的下一個位置定址。|  
|[大小](../Topic/hash_set::size.md)|傳回 `hash_set` 中項目的數目。|  
|[交換](../Topic/hash_set::swap.md)|交換兩個 `hash_set` 的項目。|  
|[upper\_bound](../Topic/hash_set::upper_bound.md)|傳回迭代器，指向 `hash_set` 中索引鍵等於或大於特定索引鍵的第一個項目。|  
|[value\_comp](../Topic/hash_set::value_comp.md)|擷取一份用以進行雜湊及排序 `hash_set` 中項目索引鍵值的雜湊特性物件複本。|  
  
### 運算子  
  
|||  
|-|-|  
|[hash\_set::operator\=](../Topic/hash_set::operator=.md)|用另一個 `hash_set` 的複本取代 `hash_set` 的項目。|  
  
## 需求  
 **標頭：**\<hash\_set\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)