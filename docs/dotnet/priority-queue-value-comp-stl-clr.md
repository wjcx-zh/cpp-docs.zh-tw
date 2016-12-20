---
title: "priority_queue::value_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_comp 成員 [STL/CLR]"
ms.assetid: af28e541-087d-4837-9ff0-cd36d4cfc57a
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製兩個項目的排序委派。  
  
## 語法  
  
```  
value_compare^ value_comp();  
```  
  
## 備註  
 成員函式傳回用於排序受控制序列的順序委派。  您會用它來比較兩個值。  
  
## 範例  
  
```  
// cliext_priority_queue_value_comp.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**  
**compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= False**  
**compare\(L'b', L'a'\) \= True**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)   
 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)