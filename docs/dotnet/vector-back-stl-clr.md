---
title: "vector::back (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::back"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back 成員 [STL/CLR]"
ms.assetid: 5edb3fcc-74c5-4f04-b8dd-edab49ba45a0
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::back (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取最後一個項目。  
  
## 語法  
  
```  
reference back();  
```  
  
## 備註  
 成員函式傳回參考給受控制序列的最後一個項目，此序列不能為空序列。  您會用它來存取，最後一個項目，當您知道它存在。  
  
## 範例  
  
```  
// cliext_vector_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**back\(\) \= c**  
 **a b x**   
## 需求  
 **標頭：** \<cliext\/vector\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::back\_item](../dotnet/vector-back-item-stl-clr.md)   
 [vector::front](../dotnet/vector-front-stl-clr.md)   
 [vector::front\_item](../dotnet/vector-front-item-stl-clr.md)