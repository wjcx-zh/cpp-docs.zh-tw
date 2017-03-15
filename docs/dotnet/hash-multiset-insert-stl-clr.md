---
title: "hash_multiset::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: e7254f30-a514-4ddc-bf53-38aafbe9e8eb
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# hash_multiset::insert (STL/CLR)
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
 首先  
 要插入的範圍開頭。  
  
 last  
 插入範圍結尾。  
  
 right  
 要插入的列舉型別。  
  
 val  
 插入的索引值。  
  
 where  
 只要在插入的容器 \(僅限提示\)。  
  
## 備註  
 每一個成員函式序列由其他運算元指定的外掛程式。  
  
 第 10% 成員函式插入具有會指定新插入的項目的值為 `val`的元素，並傳回 Iterator。  您會用它來插入單一項目。  
  
 第二 \+ 成成員函式插入具有值 `val`的項目，請使用 `where` 做為會指定新插入的項目的提示 \(改善效能\) 並傳回 Iterator。  您會用它來插入可能是在項目周圍您知道的單一項目。  
  
 第三 \+ 成成員函式插入序列 `[``first``,``last``)`。  您會用它來插入另一個序列複製的零個或多個項目。  
  
 第四個成員函式插入 `right`指定的序列。  您會用它來插入列舉值所描述的序列。  
  
 每個項目插入所花費的時間比例與項目數目的對數超過受控制序列的。  插入在被轉換舊的常數時間中發生，但是將插入點來指定項目的提示。  
  
## 範例  
  
```  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**插入 \(L'x\) \= x**  
**插入 \(L'b \= b\)**  
 **b b c x**  
**插入 \(啟動 \(\)， L'y\) \= y**  
 **x\-y b b c**  
 **b b c x**  
 **x\-y b b c**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)