---
title: "set::erase (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成員 [STL/CLR]"
ms.assetid: 0596514b-d4cd-4d2d-8223-3bee6980261c
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# set::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置的項目。  
  
## 語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### 參數  
 first  
 要清除之範圍的開頭。  
  
 Key \- 索引鍵  
 要清除的索引鍵值。  
  
 last  
 要清除之範圍的結尾。  
  
 where  
 要清除的項目。  
  
## 備註  
 第一個成員函式移除受控制序列中 `where` 指向的項目，並且回傳迭代器，其委派移除的項目之上的第一個剩餘項目，若沒有這樣的項目存在則傳回 [set::end](../dotnet/set-end-stl-clr.md)`()`。  您可用它來移除單一項目。  
  
 第二個成員函式移除受控制序列中範圍 `[``first``,` `last``)` 的項目，並且傳回迭代器，其委派移除的任何項目之上的第一個剩餘項目，若沒有這樣的項目存在則傳回 `end()`。  您可用它來移除零或多個連續的項目。  
  
 第三個成員函式移除受控制序列中擁有和 `key` 相等排序的索引值的任何項目，並且回傳移除的項目數。  您可用它來移除和計數符合指定索引鍵的項目。  
  
 每個項目消除所需花費的時間與受控制序列中的項目數之對數成比例。  
  
## 範例  
  
```  
// cliext_set_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**erase\(begin\(\)\) \= b**  
 **b c d e**  
**erase\(begin\(\), end\(\)\-1\) \= e**  
**size\(\) \= 1**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::clear](../dotnet/set-clear-stl-clr.md)