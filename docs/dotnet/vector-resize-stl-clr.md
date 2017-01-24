---
title: "vector::resize (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::resize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resize 成員 [STL/CLR]"
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::resize (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

變更項目的數目。  
  
## 語法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### 參數  
 new\_size  
 受控制序列的新大小。  
  
 val  
 填補項目的值。  
  
## 備註  
 這些成員函式同時確保 [vector::size](../dotnet/vector-size-stl-clr.md)`()` 從此傳回 `new_size`。  如果必須讓受控制序列更長，第一個成員函式以 `value_type()` 值附加至項目，而第二個成成員函式以 `val` 值附加至項目。  若要讓受控制序列較短，兩個成員函式有效地清除最後項目 [vector::size](../dotnet/vector-size-stl-clr.md)`() -` `new_size` 次。  您可以使用它以修減或附加受控制序列的方式確保受控制序列的大小為 `new_size`。  
  
## 範例  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0 0**  
**size\(\) \= 0**  
 **x x x x x**   
## 需求  
 **標頭：** \<cliext\/vector\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::clear](../dotnet/vector-clear-stl-clr.md)   
 [vector::erase](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert](../dotnet/vector-insert-stl-clr.md)