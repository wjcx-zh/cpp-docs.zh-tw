---
title: "map::upper_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成員 [STL/CLR]"
ms.assetid: d772b4a8-d0dc-439a-8b5b-3c91836d9256
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

符合指定之索引鍵的範圍中尋找結尾。  
  
## 語法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引鍵值。  
  
## 備註  
 成員函式來判斷在相同 Bucket 的項目為 `key`之受控制序列的最後一個項目的 `X` 。  如果沒有這類項目，則為，如果 `X` 是在受控制序列的最後一個項目，則會傳回 [map::end](../dotnet/map-end-stl-clr.md)`()`;否則會指定在 `X`之外的第一個項目的 Iterator 傳回它。  您可以使用它目前所在項目的結尾符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
**upper\_bound \(L'x\) \=\=end \(\) \= true**  
**\*upper\_bound \(L'a\) \= \[b 2\]**  
**\*upper\_bound \(L'b\) \= \[c 3\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::count](../dotnet/map-count-stl-clr.md)   
 [map::equal\_range](../dotnet/map-equal-range-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)