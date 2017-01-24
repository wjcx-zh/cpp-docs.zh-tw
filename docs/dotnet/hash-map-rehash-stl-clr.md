---
title: "hash_map::rehash (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::rehash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rehash 成員 [STL/CLR]"
ms.assetid: e894157c-4e31-4fbf-8020-b90f236da3e7
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::rehash (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重新建置雜湊資料表。  
  
## 語法  
  
```  
void rehash();  
```  
  
## 備註  
 成員函式重建雜湊表，確保 [hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)`() <=`[hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md)。  否則，雜湊資料表大小增加只需要在插入後。\(它的大小會自動縮小\)。您會用它來調整雜湊資料表的大小。  
  
## 範例  
  
```  
// cliext_hash_map_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
  
  **\[1\] \[2\] \[bc 3\]**  
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
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::bucket\_count](../dotnet/hash-map-bucket-count-stl-clr.md)   
 [hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)   
 [hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md)