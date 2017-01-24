---
title: "stack::top_item (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::top_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top_item 成員 [STL/CLR]"
ms.assetid: 01571acf-4880-44c4-80c4-bd91408a032d
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::top_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取最後一個項目。  
  
## 語法  
  
```  
property value_type top_item;  
```  
  
## 備註  
 屬性存取受控制序列的最後一個項目，此序列不能為空序列。  當您知道它存在時，您可用它來讀取或寫入最後一個項目。  
  
## 範例  
  
```  
// cliext_stack_top_item.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**top\_item \= c**  
 **a b x**   
## 需求  
 **標頭：** \<cliext\/stack\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [stack::top](../dotnet/stack-top-stl-clr.md)