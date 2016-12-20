---
title: "map 類別 | Microsoft Docs"
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
  - "std::map"
  - "map/std::map"
  - "map"
  - "std.map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 類別"
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: 27
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# map 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從每個項目都是資料值與排序鍵組的集合，用於資料儲存和擷取。  索引鍵的值是唯一的，用於自動排序資料。  
  
 對應中的項目值可以直接變更。  索引鍵值是常數，無法變更。  相反地，與舊項目相關聯的索引鍵值必須刪除，並插入新項目的新索引鍵值。  
  
## 語法  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits = less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class map;  
```  
  
#### 參數  
 `Key`  
 要存放在對應中的索引鍵資料類型。  
  
 `Type`  
 要存放在對應中的項目資料類型。  
  
 `Traits`  
 類型，提供可以將兩個項目值做為排序鍵進行比較的函式物件，以判斷項目在對應中的相對順序。  這個引數是選擇性的，而且二元述詞 `less<``Key``>` 是預設值。  
  
 在 C\+\+14 中，指定沒有類型參數的 std::less\<\> 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關對應之記憶體配置和解除配置的詳細資訊。  這個引數是選擇性的，而且預設值是 `allocator<pair` `<const``Key`*、*`Type``> >`  
  
## 備註  
 標準範本庫 \(STL\) map 類別是：  
  
-   可變大小的容器，根據關聯的索引鍵值，有效率地擷取項目值。  
  
-   可逆轉的，因為它提供雙向的迭代器以存取其項目。  
  
-   已排序，因為其項目是依據指定的比較函式，由索引鍵值排序。  
  
-   唯一。  因為其項目都必須具有唯一索引鍵。  
  
-   一個成對關聯的容器，因為其項目資料值和其索引鍵值是不同的。  
  
-   樣板類別，因為它提供的功能是泛型，且與項目或索引鍵類型無關。  用於項目和索引鍵的資料類型是在類別樣板中指定為參數 \(和比較函式與配置器一起指定\)。  
  
 map 類別提供的迭代器是雙向的迭代器，不過 [insert](../Topic/map::insert.md) 和 [map](../Topic/map::map.md) 類別成員函式擁有以較弱的輸入迭代器做為樣板參數之版本，其功能需求較雙向迭代器的類別少。  不同的迭代器概念因其功能的修改而有關聯性。  每個迭代器概念有自己的一組需求，因此搭配使用的演算法受那些需求所限制。  輸入迭代器可能已取值來參考某個物件，而且可能會遞增為序列中的下一個迭代器。  
  
 建議您根據應用程式所需的搜尋和插入種類，來選擇容器類型。  關聯的容器已針對查閱、插入和移除作業最佳化。  明確支援這些作業的成員函式以最糟狀況時間執行它們 \(此時間與容器中的項目數目之對數成正比\)。  插入項目不會使任何迭代器無效，移除項目則僅會使特別指向被移除項目的迭代器無效。  
  
 當關聯值與索引鍵的條件由應用程式滿足時，我們建議您選擇使用對應做為關聯容器。  這種結構的模型是已排序的唯一關鍵字清單，其中關聯的字串值提供定義。  如果文字具有一個以上的正確定義，並且索引鍵不是唯一的，則多重對應是首選容器。  如果正是要儲存文字清單，則集合將是適當的容器。  如果允許文字的多個項目，則多重集較為適當。  
  
 對應會藉由呼叫 [key\_compare](../Topic/map::key_compare.md) 類型的預存函式物件，排序它所控制的項目。  這個儲存物件是藉由呼叫 [key\_comp](../Topic/map::key_comp.md) 方法存取的比較函式。  一般而言，任何兩個特定項目會進行比較，判斷一個是否小於另一個或兩者是否相等。  當比較所有項目，會建立已排序的非對等項目序列。  
  
> [!NOTE]
>  比較函式是在標準數學概念上產生嚴格弱式順序的二元述詞。  二元述詞 f\(x,y\) 是有兩個引數物件 x 和 y 以及傳回值 `true` 或 `false` 的函式物件。  如果二元述詞為非反身屬性、非對稱、可轉移的，而且如果等價是可轉移的，其中兩個物件 x 和 y 在 f\(x,y\) ``  和 f\(y,x\) 為 `false` 時定義為相等，則施加於集合的順序是嚴格弱式順序。  如果更強的索引鍵相等條件取代等價條件，順序會變成總計 \(也就是所有項目彼此相關的排序\)，因此相符的索引鍵之間將難以辨別。  
>   
>  在 C\+\+14 中，指定沒有類型參數的 `std::less<>` 或 `std::greater<>` 述詞，即可啟用異質查閱。  如需詳細資訊，請參閱[關聯容器中的異質查閱](../standard-library/stl-containers.md#sequence_containers)  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[map](../Topic/map::map.md)|建構特定大小的清單，或具有特定值之項目的清單，或具有特定 `allocator` 的清單，或是做為其他對應的複本。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/map::allocator_type.md)|對應物件之 `allocator` 類別的 typedef。|  
|[const\_iterator](../Topic/map::const_iterator.md)|可以在對應中讀取 `const` 項目的雙向迭代器的 typedef。|  
|[const\_pointer](../Topic/map::const_pointer.md)|在對應中指向 `const` 項目的指標之 typedef。|  
|[const\_reference](../Topic/map::const_reference.md)|指向儲存在對應中的 `const` 項目的參考之 typedef，用以讀取和執行 `const` 作業。|  
|[const\_reverse\_iterator](../Topic/map::const_reverse_iterator.md)|提供雙向迭代器的類型，這個迭代器可以讀取對應中的任何 `const` 項目。|  
|[difference\_type](../Topic/map::difference_type.md)|範圍 \(介於迭代器所指的項目\) 中對應的項目數量的帶正負號整數 typedef。|  
|[迭代器](../Topic/map::iterator.md)|雙向迭代器的 typedef，可以讀取或修改對應中的任何項目。|  
|[key\_compare](../Topic/map::key_compare.md)|函式物件之 typedef，可比較兩個排序鍵以判斷兩個項目在對應中的相對順序。|  
|[key\_type](../Topic/map::key_type.md)|對應中每個項目所儲存之排序鍵的 typedef。|  
|[mapped\_type](../Topic/map::mapped_type.md)|對應中每個項目所儲存之資料的 typedef。|  
|[指標](../Topic/map::pointer.md)|在對應中指向 `const` 項目的指標之 typedef。|  
|[參考](../Topic/map::reference.md)|對應中預存項目的參考之 typedef。|  
|[reverse\_iterator](../Topic/map::reverse_iterator.md)|雙向迭代器的 typedef，可以讀取或修改反轉對應中的項目。|  
|[size\_type](../Topic/map::size_type.md)|不帶正負號的整數 typedef，表示對應中的項目數。|  
|[value\_type](../Topic/map::value_type.md)|typedef，表示對應中儲存為項目的物件類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[於](../Topic/map::at.md)|尋找具有指定之索引鍵值的項目。|  
|[begin](../Topic/map::begin.md)|傳回指向對應中的第一個項目的迭代器。|  
|[cbegin](../Topic/map::cbegin.md)|傳回指向對應中的第一個項目的常數迭代器。|  
|[cend](../Topic/map::cend.md)|傳回常數超出結尾 \(past\-the\-end\) 迭代器。|  
|[清除](../Topic/map::clear.md)|清除對應的所有項目。|  
|[count](../Topic/map::count.md)|傳回對應中索引鍵符合參數所指定之索引鍵的項目數目。|  
|[crbegin](../Topic/map::crbegin.md)|傳回指向反轉對應中的第一個項目的常數迭代器。|  
|[crend](../Topic/map::crend.md)|傳回反轉對應中，指向最後一個項目後面的位置之常數迭代器。|  
|[emplace](../Topic/map::emplace.md)|將就地建構的項目插入對應中。|  
|[emplace\_hint](../Topic/map::emplace_hint.md)|將就地建構的項目 \(含位置提示\) 插入對應中。|  
|[空白](../Topic/map::empty.md)|如果對應是空的，傳回 `true`。|  
|[end](../Topic/map::end.md)|傳回超出結尾 \(past\-the\-end\) 迭代器。|  
|[equal\_range](../Topic/map::equal_range.md)|傳回一對迭代器。  配對中第一個迭代器指向 `map` 中索引鍵大於指定索引鍵的第一個項目。  配對中第二個迭代器指向 `map` 中索引鍵等於或大於指定索引鍵的第一個項目。|  
|[erase](../Topic/map::erase.md)|從對應中的指定位置移除項目或某個項目範圍。|  
|[find](../Topic/map::find.md)|傳回迭代器，指向對應中索引鍵等於指定索引鍵的第一個項目的位置。|  
|[get\_allocator](../Topic/map::get_allocator.md)|傳回用於建構對應的 `allocator` 物件複本。|  
|[插入](../Topic/map::insert.md)|在對應中的指定位置插入項目或某個項目範圍。|  
|[key\_comp](../Topic/map::key_comp.md)|傳回對應中用來排序索引鍵的比較物件之複本。|  
|[lower\_bound](../Topic/map::lower_bound.md)|傳回迭代器，指向對應中索引鍵值等於或大於特定索引鍵值的第一個項目。|  
|[max\_size](../Topic/map::max_size.md)|傳回對應的最大長度。|  
|[rbegin](../Topic/map::rbegin.md)|傳回指向反轉對應中的第一個項目的迭代器。|  
|[rend](../Topic/map::rend.md)|傳回反轉對應中，指向最後一個項目後面的位置之迭代器。|  
|[大小](../Topic/map::size.md)|傳回對應中項目的數目。|  
|[交換](../Topic/map::swap.md)|交換兩個對應的項目。|  
|[upper\_bound](../Topic/map::upper_bound.md)|傳回迭代器，指向對應中索引鍵值大於特定索引鍵值的第一個項目。|  
|[value\_comp](../Topic/map::value_comp.md)|擷取對應中用於排序項目值的比較物件之複本。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator&#91;&#93;](../Topic/map::operator[].md)|將具有特定索引鍵值的項目插入對應中。|  
|[operator\=](../Topic/map::operator=.md)|用另一個對應複本取代對應的項目。|  
  
## 需求  
 **標頭：**\<map\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<map\> Members](http://msdn.microsoft.com/zh-tw/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)