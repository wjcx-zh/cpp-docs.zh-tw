---
title: "vector::erase (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成員 [STL/CLR]"
ms.assetid: 624905eb-83c0-499b-a07a-c10aebd7acc3
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置的項目。  
  
## 語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### 參數  
 first  
 要清除之範圍的開頭。  
  
 last  
 要清除之範圍的結尾。  
  
 where  
 要清除的項目。  
  
## 備註  
 第一成員函式中受控制序列中所指向的 `where`。  您可用它來移除單一項目。  
  
 第二 \+ 成成員函式中受控制序列的項目介於 `[``first``,` `last``)`。  您可用它來移除零或多個連續的項目。  
  
 兩個成員函式都傳回迭代器，其指定在所有項目外的第一個項目中移除，或如果沒有此類項目存在，則為 [vector::end](../dotnet/vector-end-stl-clr.md)`()`。  
  
 當清除項目時，項目的複本數目是線性項目數目在清除結尾和序列的存取結尾之間。\(當清除一個或多個項目序列中的任一端時，項目複本不會發生\)。  
  
## 範例  
  
```  
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
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
 **標頭：** \<cliext\/vector\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::clear](../dotnet/vector-clear-stl-clr.md)