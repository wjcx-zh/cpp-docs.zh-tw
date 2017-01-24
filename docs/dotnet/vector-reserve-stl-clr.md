---
title: "vector::reserve (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::reserve"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reserve 成員 [STL/CLR]"
ms.assetid: d1d5ede9-9628-4b55-95ec-f087a57205f2
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::reserve (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

確保容器的最小成長容量。  
  
## 語法  
  
```  
void reserve(size_type count);  
```  
  
#### 參數  
 count  
 容器中建立新的最小大小。  
  
## 備註  
 成員函式可確保 `capacity()` 從這至少傳回 `count`。  您會用它來確保不需要重新指派受控制序列的儲存區，直到放大以指定的大小。  
  
## 範例  
  
```  
// cliext_vector_reserve.cpp   
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
 [vector::capacity](../dotnet/vector-capacity-stl-clr.md)   
 [vector::resize](../dotnet/vector-resize-stl-clr.md)