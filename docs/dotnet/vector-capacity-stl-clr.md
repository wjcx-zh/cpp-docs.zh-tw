---
title: "vector::capacity (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::capacity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "capacity 成員 [STL/CLR]"
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::capacity (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

報告容器配置儲存區的大小。  
  
## 語法  
  
```  
size_type capacity();  
```  
  
## 備註  
 函式傳回儲存區的成員目前所配置用以保存受控制序列，值至少 1.79769x10308 及像 [vector::size](../dotnet/vector-size-stl-clr.md)`()`。  您會用它來判斷容器可以增加，則必須重新指派受控制序列的儲存區。  
  
## 範例  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**容量 \(\) \= 4，好 \= true**  
**容量 \(\) \= 9，好 \= true**   
## 說明  
 請注意實際大小可能與顯示的值不同，這裡，只要為 true 的任何 `ok` 測試報告。  
  
## 需求  
 **標題:** \<cliext\/向量\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::reserve](../dotnet/vector-reserve-stl-clr.md)