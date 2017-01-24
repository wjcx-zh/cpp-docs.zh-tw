---
title: "list::unique (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::unique"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique 成員 [STL/CLR]"
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::unique (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除通過指定測試的相鄰項目。  
  
## 語法  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### 參數  
 pred  
 對項目的比較子。  
  
## 備註  
 第 10% 成員函式從受控制序列 \(清除\) 移除比較等於它前面的項目的每個項目\-\-如果 `X` 項目在項目的 `Y` 和 `X == Y`之前，成員函式中移除 `Y`。  您會用它來移除所有多餘的相鄰項目的每 subsequence 重複比較相等。  請注意，如果受控制序列的順序，例如藉由呼叫 [list::sort](../dotnet/list-sort-stl-clr.md)`()`，成員函式保留項目本身的唯一值。\(因此名稱\)。  
  
 第二 \+ 成成員函式一般作業的第一個相同，不過，它的每個項目後面項目 `pred``(X, Y)`的 `X` 的 `Y` 。  您會用它來移除所有多餘的相鄰項目的每 subsequence 複本滿足述詞函式或委派所指定。  請注意，如果受控制序列的順序，例如藉由呼叫 `sort(``pred``)`，成員函式將不會與任何其他項目的相等排序的項目。  
  
## 範例  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b c**  
 **a b c**  
 **。**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::remove](../dotnet/list-remove-stl-clr.md)   
 [list::remove\_if](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)