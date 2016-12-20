---
title: "map::lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 成員 [STL/CLR]"
ms.assetid: 959651a0-f949-4cc1-859b-248b6930f16c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找符合指定索引鍵的項目範圍的開頭。  
  
## 語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引值。  
  
## 備註  
 成員函式來判斷在相同 Bucket 的項目為 `key`之受控制序列的第一個項目的 `X` 。  如果沒有此類項目存在，便會傳回 [map::end](../dotnet/map-end-stl-clr.md)`()`;否則會指定 `X`的會傳回迭代器。  您可以使用它目前所在項目的開頭符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_map_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**lower\_bound \(L'x\) \=\=end \(\) \= true**  
**\*lower\_bound \(L'a\) \= \[a 1\]**  
**\*lower\_bound \(L'b\) \= \[b 2\]**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::count](../dotnet/map-count-stl-clr.md)   
 [map::equal\_range](../dotnet/map-equal-range-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)