---
title: "operator&lt; (set) (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< 成員 [STL/CLR]"
ms.assetid: bd6b351d-3f33-4f66-97fa-b7e8f36ce9fd
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (set) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

清單小於比較。  
  
## 語法  
  
```  
template<typename Key>  
    bool operator<(set<Key>% left,  
        set<Key>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的正確的容器。  
  
## 備註  
 運算子函式傳回 true，否則，為最低的位置 `!(``right``[i] <``left``[i])` 也真正 `left``[i] <``right``[i]`的 `i` 。  否則，會傳回 `left``->size() <``right`用來測試`->size()` 的 `left` 是否在 `right` 之前已排序，當兩個集合是比較項目由項目時。  
  
## 範例  
  
```  
// cliext_set_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **b d**  
**\[b c\] \< \[b c\] 為 false**  
**\[b c\] \< \[\!\] 設定為 true**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [operator\=\= \(set\)](../dotnet/operator-equality-set-stl-clr.md)   
 [operator\!\= \(set\)](../dotnet/operator-inequality-set-stl-clr.md)   
 [operator\>\= \(set\)](../dotnet/operator-greater-or-equal-set-stl-clr.md)   
 [operator\> \(set\)](../dotnet/operator-greater-than-set-stl-clr.md)   
 [operator\<\= \(set\)](../dotnet/operator-less-or-equal-set-stl-clr.md)