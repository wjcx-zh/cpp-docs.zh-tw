---
title: "hash_multiset::const_reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator 成員 [STL/CLR]"
ms.assetid: 55214d17-94c3-4517-8996-ae28ff37225b
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::const_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於受控制序列的常數反向迭代器類型。  
  
## 語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## 備註  
 此型別描述其可以為此控制序列當做常數反向迭代器之未指定型別 `T4` 的物件。  
  
## 範例  
  
```  
// cliext_hash_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b a**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::reverse\_iterator](../dotnet/hash-multiset-reverse-iterator-stl-clr.md)