---
title: "multiset::lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 成員 [STL/CLR]"
ms.assetid: 5e3d1ba0-8b03-436e-b502-dbdb764f452b
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找符合指定索引鍵的範圍之開頭。  
  
## 語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引值。  
  
## 備註  
 成員函式來判斷在相同 Bucket 的項目為 `key`之受控制序列的第一個項目的 `X` 。  如果沒有此類項目存在，便會傳回 [multiset::end](../dotnet/multiset-end-stl-clr.md)`()`;否則會指定 `X`的會傳回迭代器。  您可以使用它目前所在項目的開頭符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
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
**lower\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*lower\_bound\(L'a'\) \= a**  
**\*lower\_bound\(L'b'\) \= b**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::count](../dotnet/multiset-count-stl-clr.md)   
 [multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)   
 [multiset::find](../dotnet/multiset-find-stl-clr.md)   
 [multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)