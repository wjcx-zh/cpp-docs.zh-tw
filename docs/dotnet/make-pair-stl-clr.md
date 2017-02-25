---
title: "make_pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::make_pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_pair 函式 [STL/CLR]"
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# make_pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由一組值執行 `pair` 。  
  
## 語法  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### 參數  
 Value1  
 第一個包裝值的型別。  
  
 Value2  
 第二個包裝值的型別。  
  
 first  
 包裝的第一個值。  
  
 第二  
 包裝的第二個值。  
  
## 備註  
 樣板函式會傳回 `pair<``Value1``,` `Value2``>(``first``,` `second``)`。  您可以使用它從一組的 `pair``<``Value1`, `Value2``>` 物件。  
  
## 範例  
  
```  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**  
**\[y, 4\]**   
## 需求  
 **標頭 ：** \<cliext\/utility\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)