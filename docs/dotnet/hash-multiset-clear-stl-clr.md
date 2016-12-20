---
title: "hash_multiset::clear (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear 成員 [STL/CLR]"
ms.assetid: 2253d5e3-38e6-4ad4-aff4-b546fe95830f
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除所有項目。  
  
## 語法  
  
```  
void clear();  
```  
  
## 備註  
 成員函式有效地呼叫 [hash\_multiset::erase](../dotnet/hash-multiset-erase-stl-clr.md)`(` [hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`。  您會用它來確保受控制序列是空的。  
  
## 範例  
  
```  
// cliext_hash_multiset_clear.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 0**  
 **a b**  
**size\(\) \= 0**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::erase](../dotnet/hash-multiset-erase-stl-clr.md)