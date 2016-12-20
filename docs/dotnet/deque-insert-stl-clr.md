---
title: "deque::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: a3b86c46-e6a8-42d0-b642-5a8f05ddd68c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將項目加至指定的位置。  
  
## 語法  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 參數  
 count  
 要插入的元素數目。  
  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 right  
 要插入的列舉。  
  
 val  
 要插入的元素值。  
  
 where  
 在容器中要於何處的先前插入。  
  
## 備註  
 每成員函式插入，就在受控制序列中 `where` 指向的項目之前，至其餘運算元指定的序列中。  
  
 第一個成員函式插入具有 `val` 值的項目，並傳回會指定新插入項目的迭代器。  您將它用於在迭代器的位置前插入一個項目。  
  
 第二個成員函式插入值 `val` 的 `count` 項目之複本。  您將它用於插入零或相同值的所有重複的連續項目。  
  
 如果 `InIt` 是整數型別，第三個成員函式行為與 `insert(``where``, (size_type)``first``, (value_type)``last``)` 相同。  否則，它會插入序列 `[``first``,` `last``)`。  您可用它插入從另一個序列複製的零或多個連續項目。  
  
 第四個成員函式插入 `right` 指定的序列。  您可用它來插入列舉程式描述的序列。  
  
 當插入單一項目時，項目的複本數目在插入點和序列的存取結尾之間的項目數目是線性的。\(當插入一個或多個項目序列中的任一端時，項目複本不會發生\)。如果 `InIt` 是輸入迭代器，第三個成員函式在序列有效地執行每個項目的唯一插入。  否則，當插入 `N` 個項目時，項目的複本數目在插入點和序列的存取結尾之間的項目數目加上 `N` 是線性的。  
  
## 範例  
  
```  
// cliext_deque_insert.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(begin\(\)\+1, L'x'\) \= x**  
 **a x b c**  
 **y y**  
 **y y a x b**  
 **a x b c y y a x b**   
## 需求  
 **標頭：** \<cliext\/deque\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)