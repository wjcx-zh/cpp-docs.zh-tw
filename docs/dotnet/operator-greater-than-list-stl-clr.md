---
title: "operator&gt; (list) (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator> 成員 [STL/CLR]"
ms.assetid: 58584708-1fa6-4908-84f6-790d53f46d9a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt; (list) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出大於比較。  
  
## 語法  
  
```  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 運算子函式會傳回 `right` `<` `left`。  您會用它來測試在兩個清單在逐一項目比較後，`left` 是否在 `right` 之後已排序。  
  
## 範例  
  
```  
// cliext_list_operator_gt.cpp   
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
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \> \[a b c\] is False**  
**\[a b d\] \> \[a b c\] is True**   
## 需求  
 **標頭 ：** \<cliext\/list\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)   
 [operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)   
 [operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)