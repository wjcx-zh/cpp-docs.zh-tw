---
title: "list::sort (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort 成員 [STL/CLR]"
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# list::sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

排序受控制序列。  
  
## 語法  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### 參數  
 pred  
 對項目的比較子。  
  
## 備註  
 第 10% 成員函式重新整理超過受控制序列的項目，讓它們之間的 `operator<` 排序\-\-然後，當您逐一查看序列，進度項目不減少值。  您可以使用這個成員函式來排序序列以遞增順序。  
  
 第二 \+ 成成員函式一般作業的第一個相同，但是有一點例外，就是 `pred` 序列排序\-\- `pred``(X, Y)` 為遵循結果序列的項目 `Y` 的所有項目的 `X` 是錯誤的。  您會用它來排序序列會以所述詞函式或委派中所指定的順序。  
  
 兩個函式執行穩定的排序\-\-對原始受控制序列的項目在結果序列中沒有反轉。  
  
## 範例  
  
```  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **c b。**  
 **a b c**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)   
 [list::reverse](../dotnet/list-reverse-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)   
 [list::unique](../dotnet/list-unique-stl-clr.md)