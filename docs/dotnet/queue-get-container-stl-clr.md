---
title: "queue::get_container (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::get_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_container 成員 [STL/CLR]"
ms.assetid: d87e7433-a352-4bea-8041-1ffc03287436
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::get_container (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取基礎容器。  
  
## 語法  
  
```  
container_type^ get_container();  
```  
  
## 備註  
 成員函式傳回基礎容器。  您會用它來略過由容器包裝函式所加的限制。  
  
## 範例  
  
```  
// cliext_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標題:** \<cliext\/佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::container\_type](../dotnet/queue-container-type-stl-clr.md)