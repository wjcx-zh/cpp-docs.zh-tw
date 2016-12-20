---
title: "is_default_constructible 類別 | Microsoft Docs"
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
  - "is_default_constructible"
  - "std.is_default_constructible"
  - "std::is_default_constructible"
  - "type_traits/std::is_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_default_constructible"
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
caps.latest.revision: 14
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_default_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有預設建構函式。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_default_constructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果 `T` 類型是具有預設建構函式的類別類型，則類型述詞的執行個體為 true，否則為 false。 這相當於述詞 `is_constructible<T>`。 類型 `T` 必須是完整的類型、`void` 或界限未知的陣列。  
  
## 範例  
  
```cpp  
  
#include <type_traits>   
#include <iostream>   
  
struct Simple  
{  
    Simple() : val(0) {}  
    int val;  
};  
  
struct Simple2  
{  
    Simple2(int v) : val(v) {}  
    int val;  
};  
  
int main()  
{  
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha  
        << std::is_default_constructible<Simple>::value << std::endl;  
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha  
        << std::is_default_constructible<Simple2>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_default_constructible<Simple> == true is_default_constructible<Simple2> == false  
```  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)