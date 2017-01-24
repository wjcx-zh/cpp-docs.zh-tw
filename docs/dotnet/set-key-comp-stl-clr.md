---
title: "set::key_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_comp 成員 [STL/CLR]"
ms.assetid: 245db5d0-0610-4c68-a708-9bb99e48325c
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::key_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製兩個金鑰的排序委派。  
  
## 語法  
  
```  
key_compare^key_comp();  
```  
  
## 備註  
 成員函式傳回用於排序受控制序列的順序委派。  您會用它來比較兩個索引鍵。  
  
## 範例  
  
```  
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**  
**compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= False**  
**compare\(L'b', L'a'\) \= True**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::key\_compare](../dotnet/set-key-compare-stl-clr.md)   
 [set::key\_type](../dotnet/set-key-type-stl-clr.md)