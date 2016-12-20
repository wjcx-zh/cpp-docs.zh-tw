---
title: "is_copy_constructible 類別 | Microsoft Docs"
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
  - "is_copy_constructible"
  - "std.is_copy_constructible"
  - "std::is_copy_constructible"
  - "type_traits/std::is_copy_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_copy_constructible"
ms.assetid: d8db9d4c-21ed-4884-bead-0b0b562de007
caps.latest.revision: 13
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_copy_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有複製建構函式。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_copy_constructible;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 類型是具有複製建構函式的類別，則類型述詞的執行個體為 true，否則為 false。  
  
## 範例  
  
```  
#include <type_traits>   
#include <iostream>   
  
struct Copyable  
{  
    int val;  
};  
  
struct NotCopyable  
{  
   NotCopyable(const NotCopyable&) = delete;  
   int val;  
  
};  
  
int main()  
{  
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha  
        << std::is_copy_constructible<Copyable>::value << std::endl;  
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha  
        << std::is_copy_constructible<NotCopyable>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
  **is\_copy\_constructible\<Copyable\> \=\= true**  
**is\_copy\_constructible\<NotCopyable \> \=\= false**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)