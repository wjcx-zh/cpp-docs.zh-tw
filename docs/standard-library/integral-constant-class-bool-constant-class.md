---
title: "integral_constant 類別，bool_constant 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.integral_constant"
  - "integral_constant"
  - "std::tr1::integral_constant"
  - "std.integral_constant"
  - "std::integral_constant"
  - "type_traits/std::integral_constant"
  - "std.bool_constant"
  - "std::bool_constant"
  - "type_traits/std::bool_constant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "integral_constant 類別 [TR1]"
  - "integral_constant"
  - "bool_constant"
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# integral_constant 類別，bool_constant 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從型別和值建立整數常數。  
  
## 語法  
  
```  
template <class T, T v>  
    struct integral_constant {  
        static constexpr T value = v;  
        typedef T value_type;  
        typedef integral_constant<T, v> type;  
        constexpr operator value_type() const noexcept { return (value); }  
        constexpr value_type operator()() const noexcept { return (value); }  
    };  
  
template <bool v>  
    using bool_constant = integral_constant<bool, v>;  
  
```  
  
#### 參數  
 `T`  
 常數的類型。  
  
 `v`  
 常數的值。  
  
## 備註  
 `integral_constant` 樣板類別，具有整數類資料類型特製化時 `T` 和值 `v` 該型別，表示物件，包含具有指定值的整數類資料類型的常數。 成員命名 `type` 是產生的樣板特製化類型的別名和 `value` 成員保留值 `v` 用來建立特製化。  
  
 `bool_constant` 樣板類別是明確的部分特製化的 `integral_constant` 使用 `bool` 為 `T` 引數。  
  
## 範例  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant < int、 5 > = = 5 integral_constant < bool false > = = false  
```  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [false\_type Typedef](../Topic/false_type%20Typedef.md)   
 [true\_type Typedef](../Topic/true_type%20Typedef.md)