---
title: "operator== (list) (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator== 成員 [STL/CLR]"
ms.assetid: b290f7df-1bcd-44a5-a89e-925a0fcb8c65
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator== (list) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出相等比較。  
  
## 語法  
  
```  
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 只有當順序是由 `left` 和 `right` 具有相同的長度，而且對於每個位置的 `i`來說，`left``[i] ==` `right``[i]`時，運算子函式才會傳回 true。  您會用它來測試在這兩個清單是項目對項目的比較時， `left` 是否與 `right` 排序相同。  
  
## 範例  
  
```  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \=\= \[a b c\] is True**  
**\[a b c\] \=\= \[a b d\] is False**   
## 需求  
 **標頭 ：** \<cliext\/list\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)   
 [operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)