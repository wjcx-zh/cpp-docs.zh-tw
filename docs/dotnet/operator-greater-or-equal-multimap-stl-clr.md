---
title: "operator&gt;= (multimap) (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator>= 成員 [STL/CLR]"
ms.assetid: a9e2451b-476f-48ad-a305-50798c2991f2
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt;= (multimap) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出大於或等於比較。  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator>=(multimap<Key, Mapped>% left,  
        multimap<Key, Mapped>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 運算子函式會傳回 `!(``left` `<` `right``)`。  您可用它來測試當這兩個多重對應逐一比較項目時， `left` 是否在 `right` 排序之前。  
  
## 範例  
  
```  
// cliext_multimap_operator_ge.cpp   
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
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[d 4\]**  
**\[a b c\] \>\= \[a b c\] is True**  
**\[a b c\] \>\= \[a b d\] is False**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [operator\=\= \(multimap\)](../dotnet/operator-equality-multimap-stl-lr.md)   
 [operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)   
 [operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)   
 [operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)   
 [operator\<\= \(multimap\)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)