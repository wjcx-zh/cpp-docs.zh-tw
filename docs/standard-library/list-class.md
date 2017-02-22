---
title: "list 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.list"
  - "list"
  - "std::list"
  - "list/std::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "list 類別"
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# list 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL list 類別是序列容器的範本類別，其以線性排列方式維護其元素，並允許在序列內的任何位置進行有效率的插入與刪除。  此序列會儲存為雙向連結的元素清單，每一個都會包含某種 *Type* 類型的成員。  
  
## 語法  
  
```cpp  
  
template <    class Type,     class Allocator=allocator<Type>  > class list  
```  
  
#### 參數  
 *類型*  
 要存放在清單中的元素資料類型。  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關清單之記憶體配置和解除配置的詳細資訊。  這個引數是選擇性的，而且預設值是 **allocator**\<*Type*\>*。*  
  
## 備註  
 選擇容器類型時，通常應根據應用程式所需的搜尋和插入類型。  當需要隨機存取任何元素，且只要在序列結尾處插入或刪除元素，則向量應該是管理序列的慣用容器。  當需要隨機存取，且需要在序列的開頭和結尾進行插入和刪除時，類別 deque 容器的效能是很好的。  
  
 list 成員函式 [merge](../Topic/list::merge.md)、[reverse](../Topic/list::reverse.md)、[unique](../Topic/list::unique.md)、[remove](../Topic/list::remove.md) 和 [remove\_if](../Topic/list::remove_if.md) 已針對 list 物件上的運算進行最佳化，並為它們的泛型對應項提供高效能的替代選項。  
  
 當成員函式必須插入或清除清單的元素時，就會發生清單重新配置。  在所有這種情況下，只有指向受控制序列的清除部份的迭代器或參考會變成無效。  
  
 包括 STL 標準標頭 \<list\> 以定義[容器](../standard-library/stl-containers.md)範本類別清單和幾個支援範本。  
  
### 建構函式  
  
|||  
|-|-|  
|[list](../Topic/list::list.md)|建構特定大小的清單，或具有特定值之元素的清單，或具有特定 `allocator` 的清單，或是做為其他清單的複本。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/list::allocator_type.md)|類型，表示清單物件的 `allocator` 類別。|  
|[const\_iterator](../Topic/list::const_iterator.md)|類型，提供可讀取 list 中 `const` 元素的雙向迭代器。|  
|[const\_pointer](../Topic/list::const_pointer.md)|類型，提供清單中 `const` 元素的指標。|  
|[const\_reference](../Topic/list::const_reference.md)|類型，提供儲存在清單中供讀取和執行 `const` 作業之 `const` 元素的參考。|  
|[const\_reverse\_iterator](../Topic/list::const_reverse_iterator.md)|類型，提供可讀取 list 中任何 `const` 元素的雙向迭代器。|  
|[difference\_type](../Topic/list::difference_type.md)|類型，提供兩個指出相同清單內之元素的迭代器間的差異。|  
|[迭代器](../Topic/list::iterator.md)|類型，提供可以讀取或修改清單中之任何元素的雙向迭代器。|  
|[指標](../Topic/list::pointer.md)|類型，提供清單中的元素指標。|  
|[參考](../Topic/list::reference.md)|類型，提供儲存在清單中供讀取和執行 `const` 作業之 `const` 元素的參考。|  
|[reverse\_iterator](../Topic/list::reverse_iterator.md)|類型，提供可以讀取或修改反轉清單中之元素的雙向迭代器。|  
|[size\_type](../Topic/list::size_type.md)|計算清單中元素數目的類型。|  
|[value\_type](../Topic/list::value_type.md)|類型，表示儲存在清單中的資料類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[assign](../Topic/list::assign.md)|清除清單中的元素，並複製一組新的元素至目標 list。|  
|[back](../Topic/list::back.md)|傳回清單的最後一個元素的參考。|  
|[begin](../Topic/list::begin.md)|傳回迭代器，其定址清單中的第一個元素。|  
|[list::cbegin](../Topic/list::cbegin.md)|傳回 const 迭代器，其定址清單中的第一個元素。|  
|[list::cend](../Topic/list::cend.md)|傳回 const 迭代器，其定址清單中最後一個元素的下一個位置。|  
|[list::clear](../Topic/list::clear.md)|清除清單的所有元素。|  
|[list::crbegin](../Topic/list::crbegin.md)|傳回 const 迭代器，其定址反轉清單中的第一個元素。|  
|[list::crend](../Topic/list::crend.md)|傳回 const 迭代器，其定址反轉清單中最後一個元素的下一個位置。|  
|[list::emplace](../Topic/list::emplace.md)|將就地建構的元素插入清單的指定位置。|  
|[list::emplace\_back](../Topic/list::emplace_back.md)|將就地建構的元素加入至清單的結尾。|  
|[list::emplace\_front](../Topic/list::emplace_front.md)|將就地建構的元素加入至清單的開頭。|  
|[空的](../Topic/list::empty.md)|測試清單是否為空的。|  
|[end](../Topic/list::end.md)|傳回迭代器，其定址清單中最後一個元素的後接位置。|  
|[erase](../Topic/list::erase.md)|從清單中的指定位置移除元素或某個元素範圍。|  
|[front](../Topic/list::front.md)|傳回清單中第一個元素的參考。|  
|[get\_allocator](../Topic/list::get_allocator.md)|傳回用來建構清單的 `allocator` 物件複本。|  
|[insert](../Topic/list::insert.md)|將某個元素或一些元素或某個元素範圍，插入清單的指定位置。|  
|[max\_size](../Topic/list::max_size.md)|傳回清單的最大長度。|  
|[merge](../Topic/list::merge.md)|從引數清單中移除元素，並將其插入目標清單中，然後以遞增順序或其他指定的順序，排序新合併的元素集合。|  
|[pop\_back](../Topic/list::pop_back.md)|刪除清單結尾的項目。|  
|[pop\_front](../Topic/list::pop_front.md)|刪除清單開頭的元素。|  
|[push\_back](../Topic/list::push_back.md)|將元素加入至清單的結尾。|  
|[push\_front](../Topic/list::push_front.md)|將元素加入至清單的開頭。|  
|[rbegin](../Topic/list::rbegin.md)|傳回迭代器，其定址反轉清單中的第一個元素。|  
|[remove](../Topic/list::remove.md)|清除清單中符合指定之值的項目。|  
|[remove\_if](../Topic/list::remove_if.md)|從清單中清除符合指定述詞的元素。|  
|[rend](../Topic/list::rend.md)|傳回迭代器，其定址反轉清單中最後一個元素的後接位置。|  
|[resize](../Topic/list::resize.md)|指定清單的新大小。|  
|[reverse](../Topic/list::reverse.md)|反轉項目在清單中出現的順序。|  
|[大小](../Topic/list::size.md)|傳回清單中項目的數目。|  
|[sort](../Topic/list::sort.md)|將清單的元素以遞增順序或以其他順序關聯進行排序。|  
|[splice](../Topic/list::splice.md)|從引數清單中移除元素，並將它們插入目標清單。|  
|[交換](../Topic/list::swap.md)|交換兩個清單的項目。|  
|[unique](../Topic/list::unique.md)|從清單移除相鄰的重複元素，或移除符合其他某些二元述詞的相鄰元素。|  
  
### 運算子  
  
|||  
|-|-|  
|[list::operator\=](../Topic/list::operator=.md)|用另一個清單複本取代清單的元素。|  
  
## 需求  
 **標頭：**\<list\>  
  
## 請參閱  
 [\<list\>](../standard-library/list.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)