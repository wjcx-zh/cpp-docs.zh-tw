---
title: "basic_string 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_string"
  - "std::basic_string"
  - "basic_string"
  - "xstring/std::basic_string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_string 類別"
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# basic_string 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由範本類別 `basic_string` 的物件控制的序列為標準 C\+\+ 字串類別，且通常稱為字串，但它們不應該和標準 C\+\+ 程式庫中所使用之以 Null 結束的 C 樣式字串混淆。  標準 C\+\+ 字串是一個容器，讓字串用做為標準類型，例如比較和串連運算、迭代器、STL 演算法，以及使用類別配置器 Managed 記憶體進行複製和指派。  如果您需要將標準 C\+\+ 字串轉換成以 Null 結束的 C 樣式字串，請使用 [basic\_string::c\_str](../Topic/basic_string::c_str.md) 成員。  
  
## 語法  
  
```  
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>> class basic_string;  
```  
  
#### 參數  
 `CharType`  
 若要儲存在字串中之單一字元的資料類型。  標準 C\+\+ 程式庫提供此範本類別的特製化，以及 `char` 類型元素的類型定義 [string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md)，例如 `wchar_t` 的 [wstring](../Topic/wstring.md)、`char16_t` 的 [u16string](../Topic/u16string.md)，以及 `char32_t` 的 [u32string](../Topic/u32string.md)。  
  
 `Traits`  
 basic\_string 特製化中，**CharType** 元素的各種重要屬性均描述於 **Traits** 類別中。  預設值是 `char_traits`\<`CharType`\>。  
  
 `Allocator`  
 代表預存配置器物件的類型，封裝有關字串之記憶體配置和解除配置的詳細資訊。  預設值是 **allocator**\<`CharType`\>。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_string](../Topic/basic_string::basic_string.md)|建構空的或由特定字元初始化的字串，或為其他字串物件的所有或部分複本的字串，或 C 字串。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_string::allocator_type.md)|類型，表示字串物件的 `allocator` 類別。|  
|[const\_iterator](../Topic/basic_string::const_iterator.md)|類型，提供可以存取和讀取字串中 `const` 元素的隨機存取迭代器。|  
|[const\_pointer](../Topic/basic_string::const_pointer.md)|類型，提供字串中 `const` 元素的指標。|  
|[const\_reference](../Topic/basic_string::const_reference.md)|類型，提供儲存在字串中供讀取和執行 `const` 作業之 `const` 元素的參考。|  
|[const\_reverse\_iterator](../Topic/basic_string::const_reverse_iterator.md)|類型，提供可以讀取字串中任何 `const` 元素的隨機存取迭代器。|  
|[difference\_type](../Topic/basic_string::difference_type.md)|類型，提供兩個指出相同字串內之元素的迭代器間的差異。|  
|[迭代器](../Topic/basic_string::iterator.md)|類型，提供可以讀取或修改字串中之任何元素的隨機存取迭代器。|  
|[npos](../Topic/basic_string::npos.md)|搜尋函式失敗時不帶正負號整數值初始化為 –1，表示「找不到」或「所有剩餘字元」。|  
|[指標](../Topic/basic_string::pointer.md)|類型，提供字串或字元陣列中之字元元素的指標。|  
|[參考](../Topic/basic_string::reference.md)|類型，提供儲存在字串中之元素的參考。|  
|[reverse\_iterator](../Topic/basic_string::reverse_iterator.md)|類型，提供可以讀取或修改反轉字串中的元素的隨機存取迭代器。|  
|[size\_type](../Topic/basic_string::size_type.md)|字串中元素數的不帶正負號整數類型。|  
|[traits\_type](../Topic/basic_string::traits_type.md)|儲存在字串中之元素的字元特性的類型。|  
|[value\_type](../Topic/basic_string::value_type.md)|類型，代表儲存在字串中的字元類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[append](../Topic/basic_string::append.md)|將字元加入至字串的結尾。|  
|[assign](../Topic/basic_string::assign.md)|將新的字元值指派給字串的內容。|  
|[at](../Topic/basic_string::at.md)|傳回位於字串中指定位置的元素參考。|  
|[back](../Topic/basic_string::back.md)||  
|[begin](../Topic/basic_string::begin.md)|傳回定址字串中第一個元素的迭代器。|  
|[c\_str](../Topic/basic_string::c_str.md)|將字串的內容轉換為 C 樣式且以 Null 結尾的字串。|  
|[capacity](../Topic/basic_string::capacity.md)|傳回可儲存在字串中且不增加字串的記憶體配置的最大元素數目。|  
|[cbegin](../Topic/basic_string::cbegin.md)|傳回定址字串中的第一個元素的 const 迭代器。|  
|[cend](../Topic/basic_string::cend.md)|傳回定址字串中最後一個元素的下一個位置的 const 迭代器。|  
|[clear](../Topic/basic_string::clear.md)|清除字串的所有元素。|  
|[compare](../Topic/basic_string::compare.md)|將某個字串與指定的字串比較，以判斷兩個字串是否相等，或其中一個字串的字數小於另一個字串。|  
|[copy](../Topic/basic_string::copy.md)|從來源字串中的索引位置，最多複製指定的字元數到目標字元陣列。  已取代。  請改用 [basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md)。|  
|[crbegin](../Topic/basic_string::crbegin.md)|傳回定址反轉字串中的第一個元素的 const 迭代器。|  
|[crend](../Topic/basic_string::crend.md)|傳回定址反轉字串中最後一個元素的下一個位置的 const 迭代器。|  
|[\_Copy\_s](../Topic/basic_string::_Copy_s.md)|從來源字串中的索引位置，最多複製指定的字元數到目標字元陣列。|  
|[data](../Topic/basic_string::data.md)|將字串的內容轉換成字元的陣列。|  
|[空的](../Topic/basic_string::empty.md)|測試字串是否包含字元。|  
|[end](../Topic/basic_string::end.md)|傳回定址字串中最後一個元素的下一個位置的迭代器。|  
|[erase](../Topic/basic_string::erase.md)|從指定位置移除字串中的某個元素或某個元素範圍。|  
|[find](../Topic/basic_string::find.md)|以正向方向搜尋字串中，第一個符合指定之字元序列的子字串。|  
|[find\_first\_not\_of](../Topic/basic_string::find_first_not_of.md)|搜尋字串中，不是指定字串之任何元素的第一個字元。|  
|[find\_first\_of](../Topic/basic_string::find_first_of.md)|搜尋字串中，符合指定字串之任何元素的第一個字元。|  
|[find\_last\_not\_of](../Topic/basic_string::find_last_not_of.md)|搜尋字串中，不是指定字串之任何元素的最後一個字元。|  
|[find\_last\_of](../Topic/basic_string::find_last_of.md)|搜尋字串中，是指定字串之元素的最後一個字元。|  
|[front](../Topic/basic_string::front.md)|傳回字串中第一個元素的參考。|  
|[get\_allocator](../Topic/basic_string::get_allocator.md)|傳回用來建構字串的 `allocator` 物件複本。|  
|[insert](../Topic/basic_string::insert.md)|將某個元素或一些元素或某個元素範圍，插入字串的指定位置。|  
|[長度](../Topic/basic_string::length.md)|傳回字串中目前的元素數目。|  
|[max\_size](../Topic/basic_string::max_size.md)|傳回字串中可能包含的字元數上限。|  
|[pop\_back](../Topic/basic_string::pop_back.md)|清除字串的最後一個元素。|  
|[push\_back](../Topic/basic_string::push_back.md)|將元素加入至字串結尾。|  
|[rbegin](../Topic/basic_string::rbegin.md)|傳回指向反轉字串中第一個元素的迭代器。|  
|[rend](../Topic/basic_string::rend.md)|傳回指向反轉字串中最後一個元素後方的迭代器。|  
|[replace](../Topic/basic_string::replace.md)|使用指定的字元，或從其他範圍或字串或 C 字串複製的字元，取代位於字串中指定位置的元素。|  
|[reserve](../Topic/basic_string::reserve.md)|將字串的容量數字，設定為至少和指定的數字一樣大。|  
|[resize](../Topic/basic_string::resize.md)|指定字串的新大小，視需要附加或清除元素。|  
|[rfind](../Topic/basic_string::rfind.md)|以向後方向搜尋字串中，第一個符合指定之字元序列的子字串。|  
|[shrink\_to\_fit](../Topic/basic_string::shrink_to_fit.md)|丟棄多餘的字串容量。|  
|[大小](../Topic/basic_string::size.md)|傳回字串中目前的元素數目。|  
|[substr](../Topic/basic_string::substr.md)|從開始於指定位置的字串，複製最多一定字元數量的子字串。|  
|[交換](../Topic/basic_string::swap.md)|交換兩個字串的內容。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\+\=](../Topic/basic_string::operator+=.md)|將字元附加至字串。|  
|[operator\=](../Topic/basic_string::operator=.md)|將新的字元值指派給字串的內容。|  
|[operator&#91;&#93;](../Topic/basic_string::operator.md)|使用字串中的指定索引，提供字元的參考。|  
  
## 備註  
 如果函式被要求產生長於 [max\_size](../Topic/basic_string::max_size.md) 元素的序列，則此函式會藉由擲回 [length\_error](../standard-library/length-error-class.md) 類型的物件，報告長度錯誤。  
  
 指定受控制序列之元素的參考、指標和迭代器，在呼叫更改受控制序列的函式之後，或是第一次呼叫非 **const** 成員的函式之後，可能會變得無效。  
  
## 需求  
 **標頭：**\<string\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<string\>](../standard-library/string.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)