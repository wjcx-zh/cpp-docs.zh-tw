---
title: "aligned_union 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "aligned_union"
  - "std.aligned_union"
  - "std::aligned_union"
  - "type_traits/std::aligned_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_union"
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: 10
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# aligned_union 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供 POD 類型夠大，並適當對齊以儲存聯集類型，與所需的大小。  
  
## 語法  
  
```  
template <std::size_t Len, class... Types>  
    struct aligned_union;  
  
template <std::size_t Len, class... Types>  
    using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### 參數  
 `Len`  
 等位中最大類型的對齊值。  
  
 `Types`  
 基礎等位中的不同類型。  
  
## 備註  
 使用此範本類別取得的對齊和未初始化的儲存體中儲存的聯集所需的大小。 成員 typedef `type` 名稱為 POD 類型適用於所列的任何類型的儲存體 `Types`; 最小的大小是 `Len`。 靜態成員 `alignment_value` 型別的 `std::size_t` 包含中列出的所有類型的所需的嚴格對齊 `Types`。  
  
## 範例  
 下列範例示範如何使用 `aligned_union` 配置將等位對齊的堆疊緩衝區。  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
您的值-> i 是 1065353216  
```  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [alignment\_of 類別](../standard-library/alignment-of-class.md)