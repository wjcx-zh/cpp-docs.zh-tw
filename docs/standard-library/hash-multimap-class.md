---
title: "hash_multimap 類別 | Microsoft Docs"
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
  - "stdext::hash_multimap"
  - "stdext.hash_multimap"
  - "hash_map/stdext::hash_multimap"
  - "hash_multimap"
  - "std::hash_multimap"
  - "std.hash_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multimap 類別"
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_multimap 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  這個 API 已過時。  替代方案是 [unordered\_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 容器類別 hash\_multimap 是標準範本程式庫的擴充功能，用以儲存及快速擷取集合的資料，而該集合中的每個項目皆成對且具有排序鍵 \(其值可重複\) 以及相關聯的資料值。  
  
## 語法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<pair <const Key, Type> >   
>  
class hash_multimap  
```  
  
#### 參數  
 `Key`  
 要存放在 hash\_multimap 中的索引鍵資料類型。  
  
 `Type`  
 要存放在 hash\_multimap 中的項目資料類型。  
  
 `Traits`  
 包含兩個函式物件的類型：一個類別 `Traits` 可以將兩個項目值做為排序索引鍵加以比較，以決定其相對順序；一個是一元述詞的雜湊函式，可將項目的索引鍵值對應到 **size\_t** 類型之不帶正負號的整數。  這個引數是選用引數，且預設值為 `hash_compare``<Key, less<Key> >`。  
  
 `Allocator`  
 代表預存配置器物件的類型，其可封裝有關 hash\_multimap 之記憶體配置與解除配置的詳細資訊。  這個引數是選用引數，且預設值是 `allocator<pair <const Key, Type> >`。  
  
## 備註  
 hash\_multimap 是：  
  
-   關聯的容器，為可變大小容器，支援項目值以關聯的索引鍵值為基礎、有效率的擷取。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已經過雜湊處理，因為其項目會依據套用至該項目索引鍵值之雜湊函式的值，分組到不同值區。  
  
-   多重，因為它的項目不需要有唯一索引鍵，因此一個索引值可以有多個相關的項目資料值。  
  
-   成對且相關聯的容器，因為其項目值與其索引鍵值不同。  
  
-   樣板類別，因為它提供的功能是泛型，因此與做為項目或索引鍵包含的特定資料類型是獨立的。  用於項目或索引鍵的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 透過排序進行雜湊的主要優點是效率更佳；成功的雜湊能執行插入、刪除，相較於和排序技術容器中項目數目對數值成比例的時間，它會以常數平均時間進行搜尋。  hash\_multimap 中項目的值可以直接變更，但相關聯的索引鍵值不可以直接變更。  相反地，與舊項目相關聯的索引鍵值必須刪除，然後插入與新項目相關聯的新索引鍵值。  
  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  經過雜湊處理的相關聯容器，已針對查閱、插入及移除作業進行過最佳化。  搭配設計良好的雜湊函式使用時，明確支援這些作業的成員函式，效率相當良好，其會以平均而言為常數的時間執行作業，而與此容器中的項目數目無關。  設計良好的雜湊函式會產生雜湊值的均勻分佈，並盡可能減少衝突發生，當相異索引鍵值對應到相同的雜湊值時，就會發生所謂的衝突。  使用最糟的雜湊函式的最壞情況下，作業數目與序列中的項目數目成正比 \(線性時間\)。  
  
 當關聯值與其索引鍵的條件由應用程式滿足時，hash\_multimap 應該要當成首選的相關聯容器。  這種結構的模型是已排序的關鍵字清單，其關聯的字串値 \(例如\) 提供定義，但不一定唯一定義文字。  如果以不重複的方式定義了關鍵字，而讓索引鍵沒有重複，則 hash\_map 會是首選容器。  另一方面，如果只儲存了文字清單，則 hash\_set 會是正確的容器。  如果允許出現多次文字，則 hash\_multiset 即是適當的容器結構。  
  
 hash\_multimap 會藉由呼叫 [value\_compare](../standard-library/value-compare-class.md) 類型的預存雜湊 `Traits` 物件，對它所控制的序列排序。  這個預存物件可藉由呼叫成員函式 [key\_comp](../Topic/hash_map::key_comp.md) 加以存取。  這類函式物件的行為必須要與 [hash\_compare](../standard-library/hash-compare-class.md)`<Key,  less<Key> >` 類別物件相同。  尤其是針對 `Key` 類型的所有 `Key` 值，呼叫 `Traits (Key)` 會產生 `size_t` 類型值的分佈。  
  
 通常，項目必須是小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致非對等項目之間的排序。  一個技術提示，比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 f\(x, y\) 是有兩個引數物件 `x` 和 `y` 以及傳回值 `true` 或 `false` 的函式物件。  如果二元述詞並非其反身、非對稱且可轉移，而且如果同等項目可以轉移，其中兩個物件 `x` 和 `y` 在 f\(x, y\) 和 f\(y, x\) 為 `false` 時定義為同等項目等，則施加於 hash\_multimap 的順序是嚴格弱式排序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
  
 受控制序列中實際的項目順序取決於雜湊函式、排序函式以及儲存於此容器物件中雜湊資料表目前的大小。  您無法判斷目前雜湊資料表的大小，因此一般而言，無法預測受控制序列中項目的順序。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 hash\_multimap 類別提供的迭代器是雙向迭代器，但類別成員函式 [insert](../Topic/hash_multimap::insert.md) 和 [hash\_multimap](../Topic/hash_multimap::hash_multimap.md) 擁有以較弱的輸入迭代器做為範本參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而形成關聯的系列。  每個迭代器概念有自己的 hash\_multimap 需求，因此使用它們的演算法必須將其假設限制為該迭代器類型的需求。  可假設輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  這是最基本的 hash\_multimap 功能，但足以在成員函式的內容中，有意義地溝通有關迭代器 `[First, Last)` 的範圍。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間。  如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
### 建構函式  
  
|||  
|-|-|  
|[hash\_multimap](../Topic/hash_multimap::hash_multimap.md)|建構特定大小的清單，或具有特定值之項目的清單，或具有特定 `allocator` 的清單，或是做為一些其他 `hash_multimap` 的複本。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_multimap::allocator_type.md)|類型，表示 `allocator` 物件的 `hash_multimap` 類別。|  
|[const\_iterator](../Topic/hash_multimap::const_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的 `hash_multimap` 項目。|  
|[const\_pointer](../Topic/hash_multimap::const_pointer.md)|類型，提供 `const` 中 `hash_multimap` 項目之指標。|  
|[const\_reference](../Topic/hash_multimap::const_reference.md)|類型，提供儲存在 `const` 中供讀取和執行 `hash_multimap` 作業之 `const` 項目的參考。|  
|[const\_reverse\_iterator](../Topic/hash_multimap::const_reverse_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取 `const` 中的任何 `hash_multimap` 項目。|  
|[difference\_type](../Topic/hash_multimap::difference_type.md)|帶正負號的整數類型，可以用來表示範圍 \(介於迭代器所指的項目\) 中 `hash_multimap` 的項目數。|  
|[迭代器](../Topic/hash_multimap::iterator.md)|類型，其提供可讀取或修改 `hash_multimap` 中任何項目的雙向迭代器。|  
|[key\_compare](../Topic/hash_multimap::key_compare.md)|類型，提供可以比較兩個排序鍵的函式物件，以判斷兩個項目在 `hash_multimap` 中的相對順序。|  
|[key\_type](../Topic/hash_multimap::key_type.md)|類型，描述構成 `hash_multimap` 每個元素的排序鍵物件。|  
|[mapped\_type](../Topic/hash_multimap::mapped_type.md)|類型，表示儲存在 `hash_multimap` 中的資料類型。|  
|[指標](../Topic/hash_multimap::pointer.md)|類型，其提供 `hash_multimap` 中項目的指標。|  
|[參考](../Topic/hash_multimap::reference.md)|類型，提供儲存在 `hash_multimap` 中之項目的參考。|  
|[reverse\_iterator](../Topic/hash_multimap::reverse_iterator.md)|類型，提供可以讀取或修改反轉 `hash_multimap` 中之項目的雙向迭代器。|  
|[size\_type](../Topic/hash_multimap::size_type.md)|不帶正負號的整數類型，可以表示 `hash_multimap` 中的項目數。|  
|[value\_type](../Topic/hash_multimap::value_type.md)|類型，提供可將兩個項目做為排序鍵進行比較之函式物件，以判斷項目在 `hash_multimap` 中的相對順序。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/hash_multimap::begin.md)|傳回迭代器，為 `hash_multimap` 中的第一個項目定址。|  
|[hash\_multimap::cbegin](../Topic/hash_multimap::cbegin.md)|傳回常數迭代器，為 `hash_multimap` 中的第一個項目定址。|  
|[hash\_multimap::cend](../Topic/hash_multimap::cend.md)|傳回常數迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[清除](../Topic/hash_multimap::clear.md)|清除 `hash_multimap` 的所有項目。|  
|[count](../Topic/hash_multimap::count.md)|傳回 `hash_multimap` 中索引鍵符合參數指定之索引鍵的項目數目。|  
|[hash\_multimap::crbegin](../Topic/hash_multimap::crbegin.md)|傳回常數迭代器，為反轉 `hash_multimap` 中的第一個項目定址。|  
|[hash\_multimap::crend](../Topic/hash_multimap::crend.md)|傳回常數迭代器，為反轉 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[hash\_multimap::emplace](../Topic/hash_multimap::emplace.md)|將就地建構的項目插入 `hash_multimap` 中。|  
|[hash\_multimap::emplace\_hint](../Topic/hash_multimap::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入 `hash_multimap` 中。|  
|[空白](../Topic/hash_multimap::empty.md)|測試 `hash_multimap` 是否為空白。|  
|[end](../Topic/hash_multimap::end.md)|傳回迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[equal\_range](../Topic/hash_multimap::equal_range.md)|傳回迭代器，為 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[erase](../Topic/hash_multimap::erase.md)|從指定位置移除在 `hash_multimap` 中的項目或某個範圍的項目。|  
|[find](../Topic/hash_multimap::find.md)|傳回迭代器，為 `hash_multimap` 中索引鍵等於指定索引鍵項目位置定址。|  
|[get\_allocator](../Topic/hash_multimap::get_allocator.md)|傳回用來建構 `allocator` 的 `hash_multimap` 物件複本。|  
|[插入](../Topic/hash_multimap::insert.md)|在 `hash_multimap` 中的指定位置插入項目或某個範圍的項目。|  
|[key\_comp](../Topic/hash_multimap::key_comp.md)|擷取 `hash_multimap` 中用來排序索引鍵的比較物件之複本。|  
|[lower\_bound](../Topic/hash_multimap::lower_bound.md)|傳回迭代器，其指向 `hash_multimap` 中索引鍵值等於或大於特定索引鍵值的第一個項目。|  
|[max\_size](../Topic/hash_multimap::max_size.md)|傳回 `hash_multimap` 的最大長度。|  
|[rbegin](../Topic/hash_multimap::rbegin.md)|傳回迭代器，為反轉 `hash_multimap` 中的第一個項目定址。|  
|[rend](../Topic/hash_multimap::rend.md)|傳回迭代器，為反轉 `hash_multimap` 中最後一個項目的下一個位置定址。|  
|[大小](../Topic/hash_multimap::size.md)|指定 `hash_multimap` 的新大小。|  
|[交換](../Topic/hash_multimap::swap.md)|交換兩個 `hash_multimap` 的項目。|  
|[upper\_bound](../Topic/hash_multimap::upper_bound.md)|傳回迭代器，其會指向 `hash_multimap` 中索引鍵值大於特定索引鍵值的第一個項目。|  
|[value\_comp](../Topic/hash_multimap::value_comp.md)|擷取 `hash_multimap` 中用於排序項目值之比較物件的複本。|  
  
### 運算子  
  
|||  
|-|-|  
|[hash\_multimap::operator\=](../Topic/hash_multimap::operator=.md)|用另一個 `hash_multimap` 的複本取代 `hash_multimap` 的項目。|  
  
## 需求  
 **標頭：**\<hash\_map\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)