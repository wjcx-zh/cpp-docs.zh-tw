---
title: "list::splice (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::splice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "splice 成員 [STL/CLR]"
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::splice (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

節點之間的 Restitch 連結。  
  
## 語法  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### 參數  
 首先  
 不規則範圍開頭。  
  
 last  
 不規則範圍結尾。  
  
 right  
 不規則從容器。  
  
 where  
 只要在先前的容器。  
  
## 備註  
 第 10% 成員函式在 `where`上的對受控制序列的順序由 `right` 在這個項目之前。  從 `right`中移除所有項目。\(`%``right` 必須不等於 `this`\)。您會用它來接合任何一個清單到另一個。  
  
 第二 \+ 成成員函式移除項目指向 `first` 位在順序由 `right` 並將這個項目之前在受控制序列中所指向的 `where`。如果 \( `where``==``first``||``where``== ++``first`，不會發生變更\)。您會用它來接合一份清單中的單一項目到另一個。  
  
 第三 \+ 成成員函式在 `where`上的對受控制序列插入 `[`指定的子`first``,`的`last`從`)` 順序由 `right` 在這個項目之前。  它也會從原始的子範圍順序由 `right`。\(如果 `right`為`==`則為`this`，範圍為 `[``first``,``last``)` 不能包含項目指向 `where`\)。您會用它來接合零個或多個項目 subsequence 從一個清單的到另一個中。  
  
## 範例  
  
```  
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**c1.size \(\) \= 0**  
 **a b c**  
 **a**  
 **b c**  
 **b "。**  
**c2.size \(\) \= 0**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::insert](../dotnet/list-insert-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)