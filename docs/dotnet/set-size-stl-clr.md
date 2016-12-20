---
title: "set::size (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成員 [STL/CLR]"
ms.assetid: f231c515-b07e-4e18-90fd-535b13c2db70
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計數項目的數目。  
  
## 語法  
  
```  
size_type size();  
```  
  
## 備註  
 成員函式傳回受控制序列的長度。  您會用它來決定目前項目數目超過受控制序列。  如果您想要的是序列是否具有非零的大小，請參閱 [set::empty](../dotnet/set-empty-stl-clr.md)`()`。  
  
## 範例  
  
```  
// cliext_set_size.cpp   
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
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**大小 \(\) \= 3 開始的 3**  
**大小 \(\) \= 0 在清除之後**  
**大小 \(\) \= 2 加 2 之後。**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::empty](../dotnet/set-empty-stl-clr.md)