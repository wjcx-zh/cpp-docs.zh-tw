---
title: "list::merge (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::merge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "merge 成員 [STL/CLR]"
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::merge (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

合併兩個已排序的受控制序列。  
  
## 語法  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### 參數  
 pred  
 對項目的比較子。  
  
 right  
 合併的容器。  
  
## 備註  
 第 10% 成員函式在受控制序列的所有項目順序由 `right` 並將它們插入。  必須由 `operator<` 之前訂購兩個序列。\-\-，當您將序列，進度項目不能減少值。  產生的序列會由 `operator<`來排序。  您可以使用這個成員函式來合併兩個序列的加入至的順序加入。  
  
 第二 \+ 成成員函式一般作業的第一個相同，但是有一點例外，就是 `pred` 序列排序\-\- `pred``(X, Y)` 必須為 false 為遵循序列中的所有 `Y` 項目的 `X` 。  您會用它來合併述詞函式排序兩個序列或委派所指定。  
  
 兩個函式執行穩定組合\-\-中項目的原始順序顯示在結果序列中沒有反轉。  此外，如果有，會在產生的受控制序列的項目 `X` 與 `Y` 相同 Bucket 的項目\-\- `!(X < Y) && !(X < Y)` \-\-從原始的受控制序列的項目上的一個項目之前出現順序由 `right`。  
  
## 範例  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **C\+\+. e**  
 **b d f**  
 **a b c d e f**  
**c2.size \(\) \= 0**  
 **e.c。**  
 **f\-e 的 d c b。**  
 **f\-e 的 e d c c b。**  
**c1.size \(\) \= 0**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)