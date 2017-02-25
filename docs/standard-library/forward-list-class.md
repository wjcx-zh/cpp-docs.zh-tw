---
title: "forward_list 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::forward_list"
  - "forward_list"
  - "forward_list/std::forward_list"
  - "std.forward_list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "forward_list 類別"
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# forward_list 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個控制不同長度項目序列的物件。  這個序列會儲存為節點的單一連結清單，每個清單都包含一個 `Type` 類型的成員。  
  
## 語法  
  
```  
template<  
    class Type,   
    class Allocator = allocator<Type>   
>  
class forward_list   
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Type`|要儲存在 forward\_list 中的項目資料類型。|  
|`Allocator`|預存配置器物件，可封裝有關 forward\_list 之記憶體配置和解除配置的詳細資料。  這是選擇性參數。  預設值為 allocator\<`Type`\>。|  
  
## 備註  
 `forward_list` 物件可配置及釋放序列的儲存體，該序列是透過依據[allocator 類別](../standard-library/allocator-class.md) \(通常稱為 `std::allocator)`\) 之 `Allocator` 類別的預存物件來控制。  如需詳細資訊，請參閱[配置器](../standard-library/allocators.md)。  配置器物件必須具有和樣板類別 `allocator` 之物件相同的外部介面。  
  
> [!NOTE]
>  如果已指派容器物件，就不會複製預存配置器物件。  
  
 當透過 `forward_list` 清除受控制序列的項目時，迭代器、指標和參考可能會變成無效。  透過 `forward_list` 在受控制的序列上執行插入和接合不會使迭代器無效。  
  
 呼叫 [forward\_list::insert\_after](../Topic/forward_list::insert_after.md) \(這是呼叫建構函式 `Type(const _Type&)` 的唯一成員函式\) 時，可能會發生受控制序列的加入作業。  `forward_list` 也可能會呼叫移動建構函式。  如果這類運算式擲回例外狀況，容器物件不會插入任何新項目，而且會重新擲回例外狀況。  因此，當發生這類例外狀況時，樣板類別 `forward_list` 的物件會處於已知狀態。  
  
### 建構函式  
  
|||  
|-|-|  
|[forward\_list](../Topic/forward_list::forward_list.md)|建構 `forward_list` 類型的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/forward_list::allocator_type.md)|此類型代表轉送清單物件的配置器類別。|  
|[const\_iterator](../Topic/forward_list::const_iterator.md)|此類型提供轉送清單的常數迭代器。|  
|[const\_pointer](../Topic/forward_list::const_pointer.md)|此類型提供轉送清單中 `const` 的項目指標。|  
|[const\_reference](../Topic/forward_list::const_reference.md)|此類型提供轉送清單中項目的常數參考。|  
|[difference\_type](../Topic/forward_list::difference_type.md)|帶正負號的整數類型，可用來代表迭代器所指向的項目間之範圍中的轉送清單項目數。|  
|[迭代器](../Topic/forward_list::iterator.md)|提供轉送清單之迭代器的類型。|  
|[指標](../Topic/forward_list::pointer.md)|此類型提供轉送清單中的項目指標。|  
|[參考](../Topic/forward_list::reference.md)|此類型提供轉送清單中的項目參考。|  
|[size\_type](../Topic/forward_list::size_type.md)|此類型代表兩個項目間不帶正負號的間距。|  
|[value\_type](../Topic/forward_list::value_type.md)|此類型代表儲存在轉送清單中的項目類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[assign](../Topic/forward_list::assign.md)|從轉送清單中清除項目，並將一組新的項目複製到目標轉送清單。|  
|[before\_begin](../Topic/forward_list::before_begin.md)|傳回迭代器，其定址轉送清單中第一個項目之前的位置。|  
|[begin](../Topic/forward_list::begin.md)|傳回迭代器，其定址轉送清單中的第一個項目。|  
|[cbefore\_begin](../Topic/forward_list::cbefore_begin.md)|傳回常數迭代器，其定址轉送清單中第一個項目之前的位置。|  
|[cbegin](../Topic/forward_list::cbegin.md)|傳回常數迭代器，其定址轉送清單中的第一個項目。|  
|[cend](../Topic/forward_list::cend.md)|傳回常數迭代器，其定址轉送清單中最後一個項目之後的位置。|  
|[清除](../Topic/forward_list::clear.md)|清除轉送清單的所有項目。|  
|[emplace\_after](../Topic/forward_list::emplace_after.md)|在指定位置之後移動建構新項目。|  
|[emplace\_front](../Topic/forward_list::emplace_front.md)|將就地建構的項目加入清單的開頭。|  
|[空白](../Topic/forward_list::empty.md)|測試轉送清單是否空白。|  
|[end](../Topic/forward_list::end.md)|傳回迭代器，其定址轉送清單中最後一個項目之後的位置。|  
|[erase\_after](../Topic/forward_list::erase_after.md)|從轉送清單中移除指定位置之後的項目。|  
|[front](../Topic/forward_list::front.md)|傳回轉送清單中第一個項目的參考。|  
|[get\_allocator](../Topic/forward_list::get_allocator.md)|傳回用來建構轉送清單的配置器物件複本。|  
|[insert\_after](../Topic/forward_list::insert_after.md)|將項目加入轉送清單中的指定位置之後。|  
|[max\_size](../Topic/forward_list::max_size.md)|傳回轉送清單的最大長度。|  
|[合併](../Topic/forward_list::merge.md)|從引數清單中移除項目，並將其插入目標轉送清單中，然後以遞增順序或其他指定的順序，排序新合併的項目集合。|  
|[pop\_front](../Topic/forward_list::pop_front.md)|刪除轉送清單開頭的項目。|  
|[push\_front](../Topic/forward_list::push_front.md)|將項目加入轉送清單的開頭。|  
|[移除](../Topic/forward_list::remove.md)|清除轉送清單中符合指定值的項目。|  
|[remove\_if](../Topic/forward_list::remove_if.md)|從轉送清單中清除符合指定述詞的項目。|  
|[調整大小](../Topic/forward_list::resize.md)|指定轉送清單的新大小。|  
|[reverse](../Topic/forward_list::reverse.md)|反轉項目在轉送清單中出現的順序。|  
|[sort](../Topic/forward_list::sort.md)|以遞增順序或述詞指定的順序排列項目。|  
|[splice\_after](../Topic/forward_list::splice_after.md)|重新拼接節點之間的連結。|  
|[交換](../Topic/forward_list::swap.md)|交換兩個轉送清單的項目。|  
|[unique](../Topic/forward_list::unique.md)|移除通過指定測試的相鄰項目。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/forward_list::operator=.md)|以另一個轉送清單複本取代轉送清單的項目。|  
  
## 需求  
 **標頭：**\<forward\_list\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<forward\_list\>](../standard-library/forward-list.md)