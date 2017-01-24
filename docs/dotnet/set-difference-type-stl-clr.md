---
title: "set::difference_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::difference_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "difference_type 成員 [STL/CLR]"
ms.assetid: db8121f0-ca2f-4024-996a-0b8513f03079
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::difference_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

帶正負號的距離的型別有兩個項目之間的間距。  
  
## 語法  
  
```  
typedef int difference_type;  
```  
  
## 備註  
 型別描述的可能負數項目計數。  
  
## 範例  
  
```  
// cliext_set_difference_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**結束 \(\) \-啟動 \(\) \= 3**  
**啟動 \(\) 結束 \(\) \= \-3**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::size\_type](../dotnet/set-size-type-stl-clr.md)