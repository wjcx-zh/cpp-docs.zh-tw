---
title: "hash_map::key_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_comp 成員 [STL/CLR]"
ms.assetid: 08bd31cc-3a7c-49a3-ac48-089262b3bd44
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::key_comp (STL/CLR)
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
// cliext_hash_map_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_map c2 = cliext::greater<wchar_t>();   
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
  
  **compare\(L'a', L'a'\) \= True**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**  
**compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= False**  
**compare\(L'b', L'a'\) \= True**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::key\_compare](../dotnet/hash-map-key-compare-stl-clr.md)   
 [hash\_map::key\_type](../dotnet/hash-map-key-type-stl-clr.md)