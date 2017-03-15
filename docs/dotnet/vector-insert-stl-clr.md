---
title: "vector::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# vector::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將項目在指定的位置。  
  
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
 插入的項目數目。  
  
 首先  
 要插入的範圍開頭。  
  
 last  
 插入範圍結尾。  
  
 right  
 要插入的列舉型別。  
  
 val  
 要插入的元素值。  
  
 where  
 只要在先前插入的容器。  
  
## 備註  
 每一個成員在項目之前函式插入，指向 `where` 在受控制序列的長度，剩餘的運算元指定的序列。  
  
 第 10% 成員函式插入具有會指定新插入的項目的 `val` 值的項目並傳回 Iterator。  您將它用於 Iterator 的位置插入一個項目。  
  
 第二個成員函式插入值 `val` 的 `count` 項目之複本。  您會用它來插入零或相同值的所有重複的更連續的項目。  
  
 如果 `InIt` 是整數型別，第三 \+ 成成員函式一般作業的 `insert(``where``, (size_type)``first``, (value_type)``last``)`。  否則，它會插入序列 `[``first``,``last``)`。  您會用它來插入零或另一個序列複製的更連續的項目。  
  
 第四個成員函式插入 `right`指定的序列。  您會用它來插入列舉值所描述的序列。  
  
 當插入單一項目時，項目的複本數目是線性項目數目在插入點和序列的存取結尾之間。\(當插入一個或多個項目序列中的任一端時，項目複本不會發生\)。如果 `InIt` 是輸入 Iterator，第三 \+ 成成員函式在序列有效地執行每個項目的唯一插入。  否則，當 `N` ，插入項目時，項目的複本數目是線性在 `N` 加上項目數插入點和序列的存取結尾之間。  
  
## 範例  
  
```  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
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
**插入 \(開始 \(\+1\)， L'x\) \= x**  
 **x b c**  
 **y y**  
 **Y 座標 x b**  
 **x b c y y x b**   
## 需求  
 **標題:** \<cliext\/向量\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::assign](../dotnet/vector-assign-stl-clr.md)