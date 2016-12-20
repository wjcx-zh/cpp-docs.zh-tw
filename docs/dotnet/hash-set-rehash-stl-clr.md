---
title: "hash_set::rehash (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::rehash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rehash 成員 [STL/CLR]"
ms.assetid: f62bae81-4321-44e1-97d0-77174a13e0de
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::rehash (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重新建置雜湊資料表。  
  
## 語法  
  
```  
void rehash();  
```  
  
## 備註  
 成員函式重建雜湊表，確保 [hash\_set::load\_factor](../dotnet/hash-set-load-factor-stl-clr.md)`() <=`[hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md)。  否則，雜湊資料表大小增加只需要在插入後。\(它的大小會自動縮小\)。您會用它來調整雜湊資料表的大小。  
  
## 範例  
  
```  
// cliext_hash_set_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**bucket\_count \(\) \= 16**  
**load\_factor \(\) \= 0.1875**  
**max\_load\_factor \(\) \= 4**  
**bucket\_count \(\) \= 16**  
**load\_factor \(\) \= 0.1875**  
**max\_load\_factor \(\) \= 0.25**  
**bucket\_count \(\) \= 128**  
**load\_factor \(\) \= 0.0234375**  
**max\_load\_factor \(\) \= 0.25**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::bucket\_count](../dotnet/hash-set-bucket-count-stl-clr.md)   
 [hash\_set::load\_factor](../dotnet/hash-set-load-factor-stl-clr.md)   
 [hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md)