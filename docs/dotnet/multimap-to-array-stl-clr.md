---
title: "multimap::to_array (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::to_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "to_array 成員 [STL/CLR]"
ms.assetid: eb4872dd-5e32-4a82-8ad4-37b533eb6814
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# multimap::to_array (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製受控制序列的新陣列。  
  
## 語法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## 備註  
 成員函式會傳回包含受控制序列的陣列。  您會用它來取得控制序列的陣列形式的複本。  
  
## 範例  
  
```  
// cliext_multimap_to_array.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Mymultimap::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Mymultimap::make_value(L'd', 4));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Mymultimap::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[1\] \[b 2\] \[3\] \[cd 4\]**  
 **\[1\] \[2\] \[bc 3\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)