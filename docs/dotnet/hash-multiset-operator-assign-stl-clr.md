---
title: "hash_multiset::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成員 [STL/CLR]"
ms.assetid: 1b4d5b0a-f10f-42f8-b67b-76af51c66baf
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取代受控制序列。  
  
## 語法  
  
```  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### 參數  
 right  
 要複製的容器。  
  
## 備註  
 成員運算子複製 `right` 到物件後，再傳回 `*this`。  您會用它將受控制序列取代為它在 `right`的副本。  
  
## 範例  
  
```  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)