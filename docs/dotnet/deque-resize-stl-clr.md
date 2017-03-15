---
title: "deque::resize (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::resize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resize 成員 [STL/CLR]"
ms.assetid: c83f3c57-38b3-4706-a124-59bafbf88484
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# deque::resize (STL/CLR)
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
 這個成員函式同時確保 [deque::size](../dotnet/deque-size-stl-clr.md)從這個`()` 傳回 `new_size`。  如果必須啟用受控制序列更長，第 10% 成員函式附加與值的項目，則為 `value_type()`，而第二 \+ 成成員函式附加與 `val`值的項目。  若要讓受控制序列較短，兩個成員函式有效地清除最後項目 [deque::size](../dotnet/deque-size-stl-clr.md)`() -``new_size` 逾時。  您可以使用會修剪或邊框距離確保受控制序列的大小 `new_size`，目前受控制序列。  
  
## 範例  
  
```  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
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
  
  **大小 \(\) \= 0**  
 **0 0 0 0**  
**大小 \(\) \= 0**  
 **x x x x x**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::clear](../dotnet/deque-clear-stl-clr.md)   
 [deque::erase](../dotnet/deque-erase-stl-clr.md)   
 [deque::insert](../dotnet/deque-insert-stl-clr.md)