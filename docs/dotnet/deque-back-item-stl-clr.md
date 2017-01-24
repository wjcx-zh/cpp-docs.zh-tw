---
title: "deque::back_item (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::back_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back_item 成員 [STL/CLR]"
ms.assetid: b112636a-2f18-4eb0-abd6-076acdabeff7
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::back_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取最後一個項目。  
  
## 語法  
  
```  
property value_type back_item;  
```  
  
## 備註  
 屬性存取受控制序列的最後一個項目，此序列不能為空序列。  當您知道它存在時，您可用它來讀取或寫入最後一個項目。  
  
## 範例  
  
```  
// cliext_deque_back_item.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**back\_item \= c**  
 **a b x**   
## 需求  
 **標頭：** \<cliext\/deque\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::back](../dotnet/deque-back-stl-clr.md)   
 [deque::front](../dotnet/deque-front-stl-clr.md)   
 [deque::front\_item](../dotnet/deque-front-item-stl-clr.md)