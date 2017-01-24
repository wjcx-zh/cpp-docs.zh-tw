---
title: "operator== (multimap) (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator== 成員 [STL/CLR]"
ms.assetid: 19f22238-7acf-47dc-b95e-310b39f554ad
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator== (multimap) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出相等比較。  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator==(multimap<Key, Mapped>% left,  
        multimap<Key, Mapped>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 只有當順序是由 `left` 和 `right` 具有相同的長度，而且對於每個位置的 `i`來說，`left``[i] ==` `right``[i]`時，運算子函式才會傳回 true。  您會用它來測試在這兩個複數對應是項目對項目的比較時， `left` 是否與 `right` 排序相同。  
  
## 範例  
  
```  
// cliext_multimap_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultimap c2;   
    c2.insert(Mymultimap::make_value(L'a', 1));   
    c2.insert(Mymultimap::make_value(L'b', 2));   
    c2.insert(Mymultimap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[d 4\]**  
**\[a b c\] \=\= \[a b c\] is True**  
**\[a b c\] \=\= \[a b d\] is False**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)   
 [operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)   
 [operator\>\= \(multimap\)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)   
 [operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)   
 [operator\<\= \(multimap\)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)