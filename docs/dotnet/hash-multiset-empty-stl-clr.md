---
title: "hash_multiset::empty (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::empty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "empty 成員 [STL/CLR]"
ms.assetid: e1c738eb-9ac9-426b-88b0-2997c9476001
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::empty (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試項目是否不存在。  
  
## 語法  
  
```  
bool empty();  
```  
  
## 備註  
 成員函式傳回 true 表示一個空的控制順序。  它與 [hash\_multiset::size](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`。  您會用它來測試 hash\_multiset 是否是空的。  
  
## 範例  
  
```  
// cliext_hash_multiset_empty.cpp   
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
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**大小 \(\) \= 3**  
**空白 \(\) \= false**  
**大小 \(\) \= 0**  
**空白 \(\) \= true**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::size](../dotnet/hash-multiset-size-stl-clr.md)