---
title: "hash_set::value_compare (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 成員 [STL/CLR]"
ms.assetid: fac89cb4-79de-44be-8ef0-202e278d0401
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::value_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

兩個項目值的排序委派。  
  
## 語法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
## 備註  
 這個型別是用來決定其值引數順序的委派的同義字。  
  
## 範例  
  
```  
// cliext_hash_set_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **比較 \(L'a， L'a\) \= true**  
**比較 \(L'a， L'b\) \= true**  
**比較 \(L'b， L'a\) \= false**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)   
 [hash\_set::value\_comp](../dotnet/hash-set-value-comp-stl-clr.md)   
 [hash\_set::value\_type](../dotnet/hash-set-value-type-stl-clr.md)