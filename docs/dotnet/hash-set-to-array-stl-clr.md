---
title: "hash_set::to_array (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::to_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "to_array 成員 [STL/CLR]"
ms.assetid: 2aa61f13-85b8-4aa4-91b4-69ddcc5064dc
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::to_array (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製受控制序列至新陣列。  
  
## 語法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## 備註  
 成員函式會傳回包含受控制序列的任何陣列。  您可用它來取得控制序列的複本 \(陣列形式\)。  
  
## 範例  
  
```  
// cliext_hash_set_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c d**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_set](../dotnet/hash-set-stl-clr.md)