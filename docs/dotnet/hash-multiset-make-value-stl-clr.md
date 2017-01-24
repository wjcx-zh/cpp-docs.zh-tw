---
title: "hash_multiset::make_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value 成員 [STL/CLR]"
ms.assetid: 33a4df1c-5451-44f2-af2e-a8419f9be3b9
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::make_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個值物件。  
  
## 語法  
  
```  
static value_type make_value(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 使用的索引鍵值。  
  
## 備註  
 成員函式傳回索引鍵為 `key` 的 `value_type` 物件。  您可用它來撰寫適用於與其他數種成員函式一起使用的物件。  
  
## 範例  
  
```  
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::key\_type](../dotnet/hash-multiset-key-type-stl-clr.md)   
 [hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)