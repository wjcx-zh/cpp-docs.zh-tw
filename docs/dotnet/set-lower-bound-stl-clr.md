---
title: "set::lower_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 成員 [STL/CLR]"
ms.assetid: d4da5b8b-ddf2-4d36-8092-f1be81b42348
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找符合指定索引鍵的項目範圍的開頭。  
  
## 語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引鍵值。  
  
## 備註  
 成員函式來判斷在相同 Bucket 的項目為 `key`之受控制序列的第一個項目的 `X` 。  如果沒有此類項目存在，便會傳回 [set::end](../dotnet/set-end-stl-clr.md)`()`;否則會指定 `X`的會傳回 Iterator。  您可以使用它目前所在項目的開頭符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_set_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**lower\_bound \(L'x\) \=\=end \(\) \= true**  
**\*lower\_bound \(L'a\) \=。**  
**\*lower\_bound \(L'b \= b\)**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::count](../dotnet/set-count-stl-clr.md)   
 [set::equal\_range](../dotnet/set-equal-range-stl-clr.md)   
 [set::find](../dotnet/set-find-stl-clr.md)   
 [set::upper\_bound](../dotnet/set-upper-bound-stl-clr.md)