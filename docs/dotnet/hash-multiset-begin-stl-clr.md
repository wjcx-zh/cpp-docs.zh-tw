---
title: "hash_multiset::begin (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 成員 [STL/CLR]"
ms.assetid: f03fc205-cbc9-4054-ac6d-41ad526edfea
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控制序列的開頭。  
  
## 語法  
  
```  
iterator begin();  
```  
  
## 備註  
 指定受控制序列的第一個項目的成員函式傳回雙向 Iterator，或只是超出空序列的結尾。  您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。  
  
## 範例  
  
```  
// cliext_hash_multiset_begin.cpp   
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
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*begin \(\=\)。**  
**\*\+\+begin \(\) \= b**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)