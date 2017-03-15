---
title: "hash_multiset::size (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成員 [STL/CLR]"
ms.assetid: 45f1f35e-35c4-4e39-8485-0786c1de22e3
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# hash_multiset::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計數項目的數目。  
  
## 語法  
  
```  
size_type size();  
```  
  
## 備註  
 成員函式傳回受控制序列的長度。  您可用它來決定受控制序列中目前的項目數目。  如果您只想知道序列的大小是否非零，請參閱 [hash\_multiset::empty](../dotnet/hash-multiset-empty-stl-clr.md)`()`。  
  
## 範例  
  
```  
// cliext_hash_multiset_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 3 starting with 3**  
**size\(\) \= 0 after clearing**  
**size\(\) \= 2 after adding 2**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::empty](../dotnet/hash-multiset-empty-stl-clr.md)