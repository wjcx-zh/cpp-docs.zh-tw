---
title: "operator&lt;= (multimap) (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator<= 成員 [STL/CLR]"
ms.assetid: f23cdacd-fb1b-4e87-8e32-497226841871
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt;= (multimap) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

清單小於或等於比較。  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<=(multimap<Key, Mapped>% left,  
        multimap<Key, Mapped>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的正確的容器。  
  
## 備註  
 運算子函式會傳回 `!(``right``<``left``)`。  您會用它來測試 `left` 沒有在 `right` 之後已排序，當兩個多重對應是比較項目由項目時。  
  
## 範例  
  
```  
// cliext_multimap_operator_le.cpp   
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
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
 **\[1\] \[2\] \[bd 4\]**  
**\[b c\] \<\[\= b c\] 為 true**  
**\[b d \[\] \<\= b c\] 為 false**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [operator\=\= \(multimap\)](../dotnet/operator-equality-multimap-stl-lr.md)   
 [operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)   
 [operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)   
 [operator\>\= \(multimap\)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)   
 [operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)