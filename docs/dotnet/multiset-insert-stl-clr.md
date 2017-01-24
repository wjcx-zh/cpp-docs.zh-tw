---
title: "multiset::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: 7a3b1cc8-ec60-4ed0-ace5-46cb5872e6e7
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加入項目。  
  
## 語法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### 參數  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 right  
 要插入的列舉。  
  
 val  
 要插入的值。  
  
 where  
 在容器內要插入的位置 \(僅限提示\)。  
  
## 備註  
 每一個成員函式插入由其他運算元指定的序列。  
  
 第一個成員函式插入具有 `val` 值的項目，並傳回會指定新插入項目的迭代器。  您可用它來插入單一項目。  
  
 第二個成員函式插入具有值 `val` 的項目 \(使用 `where` 做為提示，以改善效能\)，並傳回指定新插入項目的迭代器。  您可用它來插入一個已知項目的相鄰項目。  
  
 第三個成員函式插入序列 `[``first``,` `last``)`。  您可用它插入從另一個序列複製的零或多個項目。  
  
 第四個成員函式插入 `right` 指定的序列。  您可用它來插入列舉程式描述的序列。  
  
 每個項目插入所需花費的時間與受控制序列中的項目數之對數成比例。  插入會發生在分期的常數時間中，但是將給定指出相鄰於插入點項目的提示。  
  
## 範例  
  
```  
// cliext_multiset_insert.cpp   
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
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(L'x'\) \= x**  
**insert\(L'b'\) \= b**  
 **a b b c x**  
**insert\(begin\(\), L'y'\) \= y**  
 **a b b c x y**  
 **a b b c x**  
 **a b b c x y**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)