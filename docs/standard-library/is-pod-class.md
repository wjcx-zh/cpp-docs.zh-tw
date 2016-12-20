---
title: "is_pod 類別 | Microsoft Docs"
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
  - "std.tr1.is_pod"
  - "is_pod"
  - "std::tr1::is_pod"
  - "std.is_pod"
  - "std::is_pod"
  - "type_traits/std::is_pod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_pod 類別 [TR1]"
  - "is_pod"
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_pod 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為 POD。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_pod;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果類型 `Ty` 是一般舊資料 \(POD\)，則 `is_pod<Ty>::value` 為 `true`。  否則為 `false`。  
  
 算術類型、列舉類型、指標類型和成員類型的指標是 POD。  
  
 POD 類型的 cv\-qualified 版本本身是 POD 類型。  
  
 POD 的陣列本身是 POD。  
  
 結構或等位 \(其所有的非靜態資料成員皆為 POD\) 本身是 POD，前提是：  
  
-   沒有使用者宣告的建構函式。  
  
-   沒有私人或受保護的非靜態資料成員。  
  
-   沒有基底類別。  
  
-   沒有虛擬函式。  
  
-   沒有參考類型的非靜態資料成員。  
  
-   沒有使用者定義的複製指派運算子。  
  
-   沒有使用者定義的解構函式。  
  
 因此，您可以用遞迴方式建置包含 POD 結構和陣列的 POD 結構和陣列。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_pod\<trivial\> \=\= true**  
**is\_pod\<int\> \=\= true**  
**is\_pod\<throws\> \=\= false**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)